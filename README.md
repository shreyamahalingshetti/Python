
import speech_recognition as sr
import pyttsx3
import wikipedia
import webbrowser
import os
import pyaudio
import pyjokes
engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
#print(voices[1].id)
engine.setProperty('voice',voices[1].id)

def jokes():
    joke = pyjokes.get_joke()
    print(joke)
    speak(joke)
def speak(audio):
    engine.say(audio)
    engine.runAndWait()
speak("Welcome to GDSC . How may I help you")
def takeCommand():
    r=sr.Recognizer()
    with sr.Microphone() as source:
        print("I am Listening.....")
        r.pause_threshold = 1.5
        audio=r.listen(source)
    try:
        print("I am Recognizing....")
        query= r.recognize_google (audio, language='en-in')
        print(f"User said : {query}\n")
        return query
    except:
        #print(e)
        return"sorry some error occured ."
    return query
if __name__== "__main__":
    while True:
        query=takeCommand().lower()
        if 'wikipedia' in query:
            print("searching wikipedia....")
            speak("searching wikipedia")
            query=query.replace("wekipedia","")
            results=wikipedia.summary(query,sentences=2)
            print("according to wikipedia....")
            speak("according to wikipedia")
            print(results)
            speak(results)
        elif 'joke' in query:
            jokes()
        elif 'open youtube' in query:
            webbrowser.open("youtube.com")
        elif 'open google' in query:
            webbrowser.open("google.com")
        elif 'website' in query:
            webbrowser.open("https://gdsc.community.dev/shri-dharmasthala-manjunatheshwara-college-of-engineering-technology-dharwad/")
        elif 'thank' in query:
            break
            var = ()
