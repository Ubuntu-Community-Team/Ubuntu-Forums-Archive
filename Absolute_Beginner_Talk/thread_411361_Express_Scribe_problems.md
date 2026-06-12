---
title: "Express Scribe problems"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by dirtystevie on 2007-04-16
This is kind of a last try effort here.  I've been using Ubuntu for a few months now, and I can usually find solutions to all of my problems on here, but this one is kind of obscure.  I really need a program for transcribing.  On windows I was using Express Scribe, searching around, I found out that you can run Express Scribe under Wine, which I did and it's up and running but the hot keys dont' work. On windows, you can be listening to an audio file, have Word or something open, and use the hotkeys (F7) to rewind - without having to make express scribe, the active window.   In wine though, the F7 key only functions when I'm focused on the express scribe window.  Which totally defeats the purpose of hot keys.  Any help would be greatly appreciated as I would rather not have to reinstall windows.

---

### Post by caffienefree on 2007-04-16
You could try transcriber from the repositories?

> Transcribe speech data using an integrated editor
Transcriber enables easy transcription of recorded speech.
It is indispensable for every task that involves examination and
transcription of audio files, like transcription of recorded interviews, song
lyrics, radio shows and so on.  It is also useful if you are active
in the field of speech research.

The snack library (included in contrib in transcriber-1.2) is now a
separate package, libsnack2.  This package still includes html_library-0.3.

---

### Post by zippytex on 2007-09-20
I am having the same problem.  I asked the express scribe people and they said that I just needed to install the linux file, scribe.tar.gz instead of trying to use wine.  They said there is no work around.   Have you found something else?

---

### Post by zippytex on 2007-09-20
I found that using the windows with wine will work with the hotkeys if
you use the text editior built into express scribe.  then after you have finished, use copy and paste to paste it into the word processor of your choice.

---

### Post by Crazy4Coffee on 2008-01-14
I was using VMWare for a long time because I do freelance transcription work but it was totally annoying to have to open up a virtual machine.  I finally figured out that there was a Linux version of Express Scribe and it has made my life so much easier!  
Here's how to install it.

download the scribe.tar.gz wherever you download stuff
open the terminal and  type

cd to your directory, for example, 

cd /home/sarah/downloads
tar xvf scribe.tar.gz
sudo ./scribe.sh
(enter your password)

then the rest should be self explanatory.  Just a note...you have to go to the settings and the "other" tab and uncheck the thing about the word processor before you can get your hot keys to work.  Also, under the "control" tab, the default is to have the foot pedal enabled.

The only problem I am having now is that I upgraded to Gutsy from Feisty and now the sound is all choppy and skipping.  I've installed all the codecs and plugins I can think of but I don't know what is going wrong.  Might just be the system.  I am much happier with the way Feisty works.  

Good luck!

---

### Post by Crazy4Coffee on 2008-01-15
Solved the choppy audio problem with Express Scribe in Gutsy by updating linux headers and installing ALSA driver and reinstalling Express Scribe.  Seems to be working now.
Hope this helps someone who is having the same problem.   It took me hours to find the solution on my own!

---

### Post by gobbles414 on 2008-01-17
Hi all,

I am also having problems with choppy audio in Express Scribe for Linux in Gusty. I am using the Realtek HD audio drives found [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"). I cannot use Express Scribe in Wine because that hotkeys will not work as I am typing in OpenOffice. I am downloading a new version of the Realtek HD drivers and will report back on my progress.

---

### Post by gobbles414 on 2008-01-19
Hi all,

I think that Crazy4Coffee's solution may have worked on my computer! I removed all traces of Express Scribe from my computer, including */opt/NCH* and */home/username/NCH*. Then:

* I installed all of the necessary components for the Linux-386 kernel and rebooted.
* I reinstalled all ALSA-related packages in the Synaptic Package Manager and rebooted.
* After that, I installed the newest Realtek HD Audio drivers for my laptop and rebooted.

So far, Express Scribe for Linux has given me smooth audio playback. I'll report back once I have tested more.

---

### Post by gobbles414 on 2008-01-21
Hi all,

Nope! Express Scribe is doing choppy audio playback again. Although certainly not as bad as it was in the generic kernel, this choppiness simply will not do. I would appreciate advice on alternate programs. I do not mind using WINE, so long as I can use hot keys for stop, play, and rewind. Fast forward would also be nice, but is not critical.

---

### Post by jasongray on 2008-06-17
Did you find any solution to the problem?  Is there an alternative piece of software that will do much the same thing?  Or is there a way to get Express Scribe working sufficiently well?

---

