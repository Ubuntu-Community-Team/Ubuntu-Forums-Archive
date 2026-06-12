---
title: "Text-to-speech in Ubuntu"
date: 2009-06-16
forum: Assistive Technology &amp; Accessibility
---

### Post by cdahmedeh on 2009-06-16
Hello,

I'm looking for a program where I highlight text and it will read the text. The problem with Ocra is that it's not on demand, it reads everything automatically. I'm looking for something that is on demand, only when I need it.

Thanks

---

### Post by Robotman on 2009-06-27
I've had this issue on and off since I started using Linux 2 years ago.  One solution I found (and got used to) was the KDE text-to-speech system.  It was a combination of software called "kttsmgr" and "ksayit", along with whatever dependencies and custom voices were available.  Then one day, "ksayit" vanished.  "ksayit" was the frontend application that allowed the kind of text-to-speech use you and I want- selectively - where the screen reader speaks only what we tell it to say.  It was buggy in Gnome (I don't use KDE) and the voices, frankly, suck.  The least horrible of all of them sounded to me like a drunken Scottish C3PO.

With my recent update on all my systems to Ubuntu 9.04, "ksayit" just wasn't there any more.  I've asked around, but never gotten an answer as to why it's no longer in the Ubuntu repositories.
I have no idea if the KDE text-to-speech system (or Gnome's) can even be used selectively.  Rather than find out, I've gone about things in a bit of a complicated workaround.

I have VirtualBox 2 installed in Ubuntu, and with it I can run a virtualized Windows XP installation.  With an extra copy of Windows XP I have, I'm able to use a windows application I bought a long time ago called "TextAloud mp3".  That program is the best for selective text-to-speech that I have ever found.  It didn't work at all under the previous version of VirtualBox, but the new version handles it quite well. 

TextAloud mp3 has the convenient feature of "watching" the clipboard, so if text above a threshold limit is copied (like a news article) the program will automatically start reading the text.  The program is MUCH easier to listen to and understand than anything I've heard in Linux, and the custom pronunciation feature actually works for me.

Search around these forums for info on how to get VirtualBox running.

Much as I hate to admit it, in text-to-speech, Windows has Linux solidly beat.  I'd love to use a more direct and less memory and CPU intensive way of getting my computer to talk to me, but as far as I know, in Linux it just doesn't exist yet.

---

### Post by notlistening on 2009-06-28
How bad do you want it? 

I can tell you how to get TextAloud running in Linux and with a bit of work can provide a modified Linux application / plugin / tool that will do the bits of what TextAloud does that you want.

I used to use a very simple app in windows that monitored the clipboard for new text and just used to speak what ever i copied.I found that quite nice.

Plus you can use your nice SAPI voices in Linux now but it takes a little setting up. 

NL

---

### Post by nruner on 2009-07-15
Software for Ubuntu, run "sudo apt-get install festival"

Software for Windows and for free, take a look at [panopreter.com]("http://www.panopreter.com/")

---

### Post by reneorense on 2009-07-15
> **notlistening said:**
> How bad do you want it? 

I can tell you how to get TextAloud running in Linux and with a bit of work can provide a modified Linux application / plugin / tool that will do the bits of what TextAloud does that you want.

I used to use a very simple app in windows that monitored the clipboard for new text and just used to speak what ever i copied.I found that quite nice.

Plus you can use your nice SAPI voices in Linux now but it takes a little setting up. 

NL

Are the procedures one could do using WinE to make sapi-driven voices talk in linux would also work in making Orca screen reader be understood better..?

---

### Post by notlistening on 2009-07-15
One step ahead of the game here but i need some more developers on the project.

[http://code.google.com/p/open-sapi/](http://code.google.com/p/open-sapi/)

Tom

---

### Post by lakersforce on 2009-07-15
If you need it in danish you can get it at [www.adgangforalle.dk](www.adgangforalle.dk)

---

### Post by go_beep_yourself on 2010-03-18
For anybody interested in seeing an open source application similar to TextAloud and 2nd Speech Center (Windows apps) further developed, I could use some help with this project. So far, it has just been me working on it. I am trying to understand how espeak and mbrola work together, though if easier or better, I would develop this program to use festival or flite. I do not see many command line options for those apps and sence my program runs espeak with arguments gathered from the gui, I don't see the others as an option. My application is working. So far it is able to take any text highlighted and copied, and if what is highlighted is text and is different, the text is read by espeak with the default voice for horrible default espeak voice, so I am trying to understand better how espeak and mbrola work together to get some better sounding voices for this application to use. If anyones interested in seeing this project grow, please contribute whether you know how to program in Java or not, you can still contribute by trying the application and helping me to figure out how different features are used through the command line, so they can be put into the application or by packaging it as debs. Contact me if you are interested.

Edit: This app allows anything that can be copied as text to the clipboard to automatically be read to you whether the text is in Firefox, pdfs, email, etc.

---

### Post by phillw on 2010-03-18
Hi, there is an app that can take copied / pasted text and read it out. It's in the repositories. I did a brief introduction onto this forum, in case you missed it I have it over here --> [http://forum.phillw.net/viewtopic.php?f=14&t=33](http://forum.phillw.net/viewtopic.php?f=14&t=33)

If you are working on anything that is similar, please get in touch with the author, his details on are that thread. He's interested in doing more and, like many, would be grateful of others who are like minded.

It goes without saying, but I'll say it anyway, if any developers of assistive want a 'developers chat area' I'd be more than happy to set one up for you on my baby forum.

If you know of an area for them, please let me know & I'll put a link onto my baby forum.

Regards,

Phill.

---

### Post by go_beep_yourself on 2010-03-22
> **notlistening said:**
> One step ahead of the game here but i need some more developers on the project.

[http://code.google.com/p/open-sapi/](http://code.google.com/p/open-sapi/)

Tom

Would that project allow a Linux user to use voices made for Windoze in Linux like ATT Natural Voices, Cepstral, and others?

---

### Post by notlistening on 2010-03-23
That is exactly what it means. So far I have tested it with the basic Microsoft voices that come free with Windows XP and Vista. I have also tried a purchased voice from Voice Ware, Kate 16 and she is singing on Linux using Orca :D.

The project is getting some well deserved love over the next week as I am on holiday. So there should be some good work happening.

Watch this space...

NL

---

### Post by go_beep_yourself on 2010-03-23
> **notlistening said:**
> That is exactly what it means. So far I have tested it with the basic Microsoft voices that come free with Windows XP and Vista. I have also tried a purchased voice from Voice Ware, Kate 16 and she is singing on Linux using Orca :D.

The project is getting some well deserved love over the next week as I am on holiday. So there should be some good work happening.

Watch this space...

NL

Great, I hope to be able to use your program with mine to extend the voices available.

My project is here.

[http://code.google.com/p/ttsreader/](http://code.google.com/p/ttsreader/)

---

### Post by go_beep_yourself on 2010-03-23
> **cdahmedeh said:**
> Hello,

I'm looking for a program where I highlight text and it will read the text. The problem with Ocra is that it's not on demand, it reads everything automatically. I'm looking for something that is on demand, only when I need it.

Thanks

Have you tried my application? It's still in early development, but there's more to come. Linux has two clipboards. One is the one most people are familiar with when you copy highlighted text. The other is called the selection buffer or X selection. It's buffer gets filled with text as soon as you highlight something. This is usually used in Linux to highlight some text and then push down the middle mouse button where you want to paste it. I've just figured out how to read that text with programming, so I can implement it in my program to read text as soon as it's highlighted. Currently my app reads what you highlight and copy to the primary clipboard.

You can download it here.
[http://nanomachine.byethost22.com/files](http://nanomachine.byethost22.com/files)

---

### Post by notlistening on 2010-03-25
I like the idea of using your multimedia keys with such an application or global key/mouse (I like the idea of using my scroll wheel to skip) bindings that allows you to pause/resume skip back, skip forward, repeat etc. This could be done with a small notification area at the top right for example with the text in and highlighting a bit like text aloud when it is reading.

I have just developed the ability to provide RAW audio streams from SAPI with event tracking. So you can get information into your application such as the position of the word/sentence boundaries. This allows your app to process the audio stream as it wants and to skip around as the user requests with quite basic data stream work. This can be seen in Text Aloud, it is the way they highlight the current word when it is reading the text.

Not usable by other applications yet but will be soon.

---

### Post by Ter Rymon on 2012-11-09
I use gespeaker 0.8.1 and xsel  to read text I've highlighted

add a short cut under system settings>keyboard>Shortcuts

Key: 
Super+R
name:
Read Text
command:
bash -c "gespeaker --play-text=\"$(xsel | sed -e :a -e '$!N;s/\n/ /;ta')\""


gespeaker 0.8.1 can be installed from
code.google.com/p/gespeaker/downloads/list

xsel is in the ubuntu repository

sudo apt-get install xsel

---

