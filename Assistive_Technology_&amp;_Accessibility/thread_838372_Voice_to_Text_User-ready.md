---
title: "Voice to Text? User-ready?"
date: 2008-06-23
forum: Assistive Technology &amp; Accessibility
---

### Post by Tsu Dho Nimh on 2008-06-23
I don't want a kit, I don't want to compile ... I want something where I can install some software and talk to my word processor.

What is available for Linux?

---

### Post by DouglasAWh on 2008-06-25
I'd like to know this to.

I know there's Orca, but I haven't quite figured out what it does or how to use it yet.

---

### Post by Pipistrelle on 2008-07-15
I can't answer the first question, but Orca definitely is not directly involved in recognizing speech. Orca processes what's already on the screen and reads it aloud to visually-impaired folk. Just wanted to clear that up. :)

---

### Post by sybille on 2008-07-15
The only voice-to-text project I know of is in Google Summer of Code this year, which is aiming to enable dictated voice notes in Tomboy, the sticky note application:
[http://marcondes.wordpress.com/2008/07/10/istanbul-edition/](http://marcondes.wordpress.com/2008/07/10/istanbul-edition/)

If that ultimately gets finished, then I would imagine that someone could develop a similar plugin for OpenOffice.org. But I think that would probably take a lot of time to happen.

You're not the only person interested in this, though. There's even a Speech Recognition page in the Ubuntu wiki: [https://wiki.ubuntu.com/SpeechRecognition](https://wiki.ubuntu.com/SpeechRecognition)

Otherwise, I've just heard of people using Dragon Naturally Speaking with Wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5402)
[http://ubuntuforums.org/showthread.php?t=168711](http://ubuntuforums.org/showthread.php?t=168711)

---

### Post by Declan Moriarty on 2008-07-17
In my experience voice recognition systems are dreadful.  The technology isn't ready yet.  Some years ago I heard on News At Ten on ITV in Britain a demo of Dragon Naturally Speaking (I think) and it was painful.  Any secretary using it would have to have time off for stress!  It....was....very....slow....you....had....to....speak....each word with a pause in between for the system to work.  I also find the voice recognition systems for cinemas appalling as well.  I call them the "Do you mean Birmingham?" systems.  I live in Southampton when it says "Say the town you want film information for?" I say "Southampton" and it says "Do you mean Birmingham?".  Totally useless!  Also on BBC Watchdog (A consumer Program on BBC Television) they featured Nintendo "Brain Training" game for the Nintendo DS.  The voice recognition can only recognize American voices!  There were a lot of complaints about it.

If these things are not sorted out pretty quick.  No one will use voice recognition at all and it will go the same way as Head Mounted Displays for virtual reality, that is to say nowhere and the technology will disappear without trace. 

Also make sure you have a headset when using Voice Recognition, because the quality of the microphone is crucial!  This is one reason why I think the phone versions of this technology are pathetic since you have a standard input with standard microphones and you should be able to get a system working far more easily if you know what you input will be like, rather than having people speaking a varying distances from different microphones in different environments.

---

### Post by Category on 2008-09-28
> **Declan Moriarty said:**
> ...This is one reason why I think the phone versions of this technology are pathetic since you have a standard input with standard microphones and you should be able to get a system working far more easily if you know what you input will be like, rather than having people speaking a varying distances from different microphones in different environments.

The only problem with phones, is it has different people talking different distances from the microphone in different environments, suffering the same problem as an PC based stuff...

I also live in Southampton, but Odeon always thinks I say Northampton - it's like it skips a whole syllable each time!

---

### Post by Sef on 2008-09-28
It is definitely being worked on.

From Gnome 2.24 release notes:

> **3.3.&#8195;Better Screenreading**


GNOME and its partners have worked hard to improve accessibility and screenreading support for both GNOME 2.24 and many popular third party applications.
Text-to-speech and braille device support is now vastly improved for Java applications, OpenOffice.org, Mozilla Thunderbird, Pidgin, GNOME's Help Browser and the GNOME Panel. Users are now made aware of unfocused dialogues when switching to an application.
There has also been a lot of work to integrate GNOME's screen reading technology with ARIA-enabled web browsers, starting with Mozilla Firefox.
Also new is automatic selection of the synthesised voice based on the system language, support for verbalised links, echo by sentence and optional tutorial messages.


2.24 is the Gnome for Intrepid Ibex.   It is still in a testing phase, so use only on a spare computer.

---

### Post by jonathonblake on 2008-09-29
> **Sef said:**
> It is definitely being worked on.

From Gnome 2.24 release notes:> Quote:
3.3.&#8195;Better Screenreading

Screen Reading is *Text to Speach*.

What the original poster was asking about, is *Speech to Text*.
(Roughly 1% of the general population needs Speech to Text hardware and software, to use a computer.)

To answer the original posters question, try Sphinx-4.
(Synaptic has Sphinx-2, which is an older version.
Sphinx-4 can be obtained from [http://cmusphinx.sourceforge.net/sphinx4/](http://cmusphinx.sourceforge.net/sphinx4/)

Note: Read the description of the differences between Sphinx-2 and Sphinx-4, before deciding which to isntall.   (There is at least one more version, but I've forgotten its designation. )

xan

jonathon

---

### Post by notlistening on 2008-10-01
Hi All,

New to the thread but I do know of a speech to text deveoplment project based around tcl. This by no means is an ontsall and go bit of software but has the potential and I am providing it for completeness.

[http://www.icsi.berkeley.edu/~dpwe/projects/sprach/sprachcore.html](http://www.icsi.berkeley.edu/~dpwe/projects/sprach/sprachcore.html)

[http://www.inf.ed.ac.uk/resources/nlp/](http://www.inf.ed.ac.uk/resources/nlp/)


As a side note i am implementing the MS SAPI engine into Ubuntu see my SAPI post which includes speech to text engine. I am working on text to speech but this could also be exploited using a wrapper to SAPI.   

Tom

---

### Post by xyepblra on 2011-04-04
> **Tsu Dho Nimh said:**
> I want something where I can install some software and talk to my word processor.

What is available for Linux?
Great wording for my expectations, too, although in my case it is more like feeding an audiofile (recorded while I juggle) to an application, which will output a draft text, which I will then read through, correct where necessary and handle to further processing. Does anybody use something like that?

---

### Post by Russell Burrows on 2011-04-05
My initial work is going to be focused on trying to reduce the use of the laptop keyboard in favor of speaking.

However.

I have no idea what I am doing so most probably its going to take awhile for my proposed idea to get from hypothesis to actual working software.

Well I will try to post an update in a few weeks and for now I have to go and continue studying Python programming.:confused:

---

### Post by honeybear on 2011-06-12
gnome-voice-control
voximp
Julius
Simon Listens
Cmu Sphinx 

which solution is into repositories + can work with USB microphone easily?

---

### Post by honeybear on 2011-06-12
OK I found this is the easiest way.

However how to make it work with OPENBOX?


```
/usr/lib/gnome-voice-control$ ./voice_control_applet 

** (voice_control_applet:18309): WARNING **: AT_SPI_REGISTRY was not started at session startup.

** (voice_control_applet:18309): WARNING **: Could not locate registry

```

to install, find this into the repos: 
 33240 Jun 13 04:41 gnome-voice-control_0.4really0.2-0ubuntu2_i386.deb
[http://packages.ubuntu.com/maverick/i386/gnome-voice-control/download](http://packages.ubuntu.com/maverick/i386/gnome-voice-control/download)

apt-get -f install 


**how to make it work with OPENBOX?**

---

