---
title: "Remote Desktop between a mac and ubuntu"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by marzzle on 2007-01-11
So I'm using the newest version of unbuntu and OS 10.4 and I would like to set up a remote session similar to the windows thing between the mac and the unbuntu box so I won't have to sit in a rather uncomfortable position to learn how to work the unbuntu box. Now I'm not terribly familiar with my mac and I am terribly unfamiliar with linux so please explain as if to a child.

What software should I be using? Is there a "best"? Is there different software that uses the same protocol (like a web browser?)? Can one piece of software to remote desktoping on windows linux and mac?

---

### Post by linuchsan on 2007-01-11
look voor vnc, if you want client for mac and server for ubuntu.

---

### Post by jonathan.lees on 2007-01-11
Do you want to remote desktop from the Mac to Ubuntu or vice versa? On your Mac you can install a VNC client called Chicken of the VNC. This will allow you to remote desktop to your Ubuntu box, but from experience it's really slow. I run a Windows XP Virtual machine on my Mac and ran tightvnc from there and it was faster than Chicken OTV.

---

### Post by marzzle on 2007-01-11
I'd like to go from the mac to the linux box. Is it really so slow that running a virtual machine is a better option? I was thinking since macs are unix based it should be quicker maybe.

---

### Post by blackened on 2007-01-12
The lack of speed has nothing to do with the operating system, but is inherent to the fact that you're pushing alot of data through a limited bandwidth home network.  The pain of this can often be eased by adjusting the configuration settings of the vnc client you choose.

---

### Post by squirrel_f13 on 2007-02-09
I have a MBP and the popular program "Chicken of the VNC" was terribly slow when connecting to my Ubuntu machine under OS X. If you're looking for easy performance gains download the Java client for tightVNC and use it under OS X. It allows you to disable a couple things (mouse side pointer - brutal under Chicken) that makes it WAY faster. VNC is useable now.

You do need a bash script to launch the java viewer on OS X easily (otherwise you have to do it manually via terminal).

```
#!/bin/bash
cd /Users/PATH/tightvnc/classes
java VncViewer HOST "HOST-IP" PORT 5900
```

---

### Post by Gossar on 2007-02-25
Yes, _[CotVNC]("http://sourceforge.net/projects/cotvnc/")_ can be slow, but there are things you can do to get more out of it.

Go to the Profile manager (Connection->Connection Profiles...)
1) under Encodings, if you're using a wireless connection with WPA then you're already encrypted and don't need additional zlib--turn off all compression and use the Raw encoding; disable CopyRect encoding
2) under Color choose Thousands or 256 (it also helps to have a single color for the ubuntu desktop rather than a wallpaper).

You may also consider _[VNCViewer]("http://homepage.mac.com/kedoin/VNC/VNCViewer/")_.  It's more responsive, but doesn't save settings, only the most recently used.  (I've also had trouble pasting into VNCViewer from OS X).

I have not tried _[Vine Viewer]("http://www.redstonesoftware.com/products/Vine/Viewer/")_.

---

### Post by marzzle on 2007-02-25
How do I get cotvnc to do anything? I set the IP of the host to the ubuntu box but nothing happnened. I am guessing that I need to do at least something on the linux side of things to get this working but cotvnc documentation assumes a basic level of VNC stuff which I do not have.

---

### Post by Gossar on 2007-02-27
> **marzzle said:**
>  I am guessing that I need to do at least something on the linux side of things to get this working Yes, the easiest thing is to use vino, part of the default Ubuntu install. 
For 6.10 (Edgy), go to System-->Preferences-->Remote Desktop.

Make sure that the two boxes under Sharing are checked.  (Ignore the last sentence in the Sharing section. You won't use that command with a GUI app like CotVNC to connect from OS X.)

Consider the two boxes under Security based on your own situation.  The first one about confirmation means that you (or someone) will have to physically be in front of the computer that's running Ubuntu to approve and allow the connection each and every time.  The second box is important to you if you've got the Ubuntu box connected to the internet or a network with any wifi/wireless component.

It's a common model--vnc (like ftp, ssh, and the web) requires two programs, a client and a server, each running on different computers to make both halves of the connection.  By turning on Remote Desktop, you're starting a server on your computer and therefore *potentially* opening it to attack from outsiders.

---

### Post by Doppenhe on 2007-03-21
So I want to do the exact opposite, I have the latest version of OS X on my desktop and would like to remote desktop from my Ubuntu laptop (Dapper Drake).  Can anybody walk me throug this? (Ive tried using kRDC with VNC protocol with no success).

Cheers,

Diego

---

