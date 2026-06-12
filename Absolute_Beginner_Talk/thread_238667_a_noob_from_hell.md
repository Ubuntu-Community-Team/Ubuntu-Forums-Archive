---
title: "a noob from hell"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Jimmyd on 2006-08-18
ok, got ubuntu loaded (text mode), boot my old computer up, type in my user name and password, now the fun begins.....where does a dummy like me find a simple place to find the simple commands or whatever I have to type in to get going? remember the title of this thread, the noob from hell. :-k

---

### Post by Titus A Duxass on 2006-08-18
Use the search facility!

---

### Post by magnoliablossom on 2006-08-18
this doesn't actually explain commands and such to you but i have found that it helps me a lot.  it's pretty much all cut and paste.

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

---

### Post by bodhi.zazen on 2006-08-18
Google.

Search Linux guide, Linux command guide, unofficial Ubuntu guide.

With Linux Google is your friend.

---

### Post by fdoving on 2006-08-18
I can recommend:
The getting started guide: /www.tldp.org/LDP/gs/gs.html
Linux command directory: [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
Linuxcommand.org: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)
Linuxshortcuts: [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

Good luck!

- Frode

---

### Post by Jimmyd on 2006-08-18
lol, no point and click. damn, i got a lot to learn.:confused:

---

### Post by givré on 2006-08-18
> **Jimmyd said:**
> lol, no point and click. damn, i got a lot to learn.:confused:
You could do a majority of things by point & click. Are you sure you started the graphical interface?

---

### Post by Jimmyd on 2006-08-18
the HUH? as far as Ive got is booting up and got to my username and password, then it wants some commands. now IM LOST.](*,)

---

### Post by Jimmyd on 2006-08-18
oh, and the computer ive got the ubuntu on is not connected to the net yet, got to get a cable this weekend, if I get the chance.

---

### Post by Soarer on 2006-08-18
It sounds like you have installed th server version, which doesn't install the point-n-click desktop. If you didn't do that deliberately, type:

sudo apt-get install ubuntu-desktop

give your password when asked, and wait for a while. It will install Gnome from the CDROM.

---

### Post by givré on 2006-08-18
What kind of CD did you install, i guess you install the server CD. If it's the case don't worry, you are not the first to one to do this error.
Just download a normal desktop CD (or the alternate CD)

EDIT: soar has a better tip 8)

---

### Post by Jimmyd on 2006-08-18
had the cd in, gives message:: reading package list....done
                               building dependancy tree...done
                               E:: counldnt find package ubuntu 
                               desktop

and Im postive when I installed i did in text mode, unless it did something on its own. would it be better since ubuntu is the only thing on this computer to do it in oem mode?

---

### Post by bodhi.zazen on 2006-08-18
Could be you need to configure X

---

### Post by Jimmyd on 2006-08-18
I ordered the cds from shipit, none of them would work, they would freeze or crash at one of the stages, forget which. downloaded the alternate cd (pretty sure) for desktops and thats what I have. guess I could try another.

---

### Post by givré on 2006-08-18
You have three choice of install CD :
- The Desktop CD for graphical installer
- The alternate CD for text mode, if your hardware can't support the graphical installer
- The server CD which install the base system, with no GUI.
I guess it's the third one you do. If you want a text mode installer, try the alternate CD.

Also on which mirror did you get the CD, a month ago, the description of the server CD was quite confusing, but it should be fix now.

---

### Post by Jimmyd on 2006-08-18
[QUOTE=bodhi.zazen;1392814]Could be you need to configure X[/QUOTEe

lol, command lines are what got this thread started, that confused me, X? lmao, the only x I know about is there is one on the keyboard. this gets better by the minute. now my crappy, no, make that sh!tty broadband service compliments of Charter who sold out to Suddenlink and my download speed is near nothing. I need a beer. Did try one of the shipit cds again, no dice. it crashed.

---

### Post by givré on 2006-08-18
Get that one, [http://se.releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso](http://se.releases.ubuntu.com/6.06/ubuntu-6.06.1-alternate-i386.iso)
it will work.

---

### Post by Engnome on 2006-08-18
> **Jimmyd said:**
> had the cd in, gives message:: reading package list....done
                               building dependancy tree...done
                               E:: counldnt find package ubuntu 
                               desktop

and Im postive when I installed i did in text mode, unless it did something on its own. would it be better since ubuntu is the only thing on this computer to do it in oem mode?

ubuntu desktop? shouldn't that be ubuntu-desktop?

---

### Post by bodhi.zazen on 2006-08-18
Jimmyd: I am taking a wild guess, it would be nice to know exactly what you installed. I assume the "alternate CD". This boots into a graphical installer.

If at the Boot prompt you typed "enter" and installed, and none of the other CD's booted, I believe your problem is with configuration of X.

If at the boot prompt you typed "server" then you did a server install and will need first to install X.

Ditto if you used the "server" CD, although I am not familiar with that one.

X is the base of a graphical environment. When you launch a GUI ("point ans click" with a mouse and not a command line), first X starts and then your GUI.

Try this:

At the command line type X (that is a single capital X). You should get a gray screen with a large black "X" cursor that responds to mouse movements. Ctrl-Alt-Backspace to exit X (that one took me a while to figure out).

Please:
1. Can you confirm what CD you installed from, "alternate" or otherwise.
2. Did you do a server install (I assume not).
3. What happens when you type X? Error message?
4. What graphics card and monitor do you have. To configure X you will need to know the vertical and horizontal refresh rate. Google search you monitor to find the technical specifications (this is often the hardest part about configuring X in most cases).

Last question: How much RAM do you have?

---

