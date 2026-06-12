---
title: "now that i have linux running"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by PatrickMoore on 2008-03-21
so to prove the awesomeness of ubuntu i have installed it on a recently procured desktop i was trying to run xp on so that i can manage my zune my girlfriend's ipod and our internet which i will be installing a wireless router. this sense of elation is interrupted now with my current issue. 

 i need to run the zune software itunes and att yahoo dsl.
 any suggestions? experiences? all help is appreciated

---

### Post by candtalan on 2008-03-21
If I understand correctly one issue is internet connection to adsl? (yahoo) And a wireless router?

A wired router connection is much easier as a starting project, later you can more easily check out wireless function.

The modem/router will hopefully connect to the PC using wired  (ethernet) connection, not usb. The router manages the internet connection. The ubuntu PC will connect automatically to the internet no prob.

Zune and itunes will  have been designed to run only on windows so do not be too surprised if it is difficult or worse, to do exactly what you want. You may find you are 'locked in' to an extetnt maybe.

Good luck

---

### Post by Paqman on 2008-03-21
Itunes is Windows and OS X only. You won't get it working on Linux. However, something like Amarok or Exaile will organise/play your music and talk to your iPod. Not sure about Zunes.

What do you mean by "att yahoo dsl"? Are you having trouble getting an internet connection?

---

### Post by PatrickMoore on 2008-03-21
thanks guys. i'm going to start working on the internet right away this having to pack up and walk to the library is getting old. ha

 i was just wondering if i had a virtual machine if i could run zune and itunes. any suggestions. it appears wine is a no go.

seeing that i am using the desktop sparingly i would be inclined to just load xp on it but i am unwilling to shell out a hundred dollars to do that

---

### Post by stchman on 2008-03-21
> **PatrickMoore said:**
> so to prove the awesomeness of ubuntu i have installed it on a recently procured desktop i was trying to run xp on so that i can manage my zune my girlfriend's ipod and our internet which i will be installing a wireless router. this sense of elation is interrupted now with my current issue. 

 i need to run the zune software itunes and att yahoo dsl.
 any suggestions? experiences? all help is appreciated

Your iPod is supported OOB in Ubuntu with Rhythmbox.  Now there is no iTunes store available for Linux but there are numerous places on the net like Amazon to buy mp3s.

As far as a Zune I don't think there is anything out there.  The Zune is pretty new and an M$ product so don't expect anything soon.

The wireless router will take care of the PPoE.  What kind of a wireless card do you have in your laptop?  If it is an Intel or Atheros then you are good to go.  Broadcom needs the ndiswrapper.

---

### Post by Paqman on 2008-03-21
> **PatrickMoore said:**
> 
 i was just wondering if i had a virtual machine if i could run zune and itunes. any suggestions. it appears wine is a no go.


You could, but a VM won't be able to move files outside of it's own virtual file system, so it'd be pretty annoying. Seriously, try Amarok, it does everything iTunes does and it's a native Linux ap. Exaile is a clone of it designed to look nicer on a Gnome desktop, since Amarok was built for KDE.

Seems like you're moderately screwed with the Zune, Microsoft have designed it so that it only works with Windows, bless 'em! You may be able to get it working with [these instructions](http://ubuntuforums.org/showthread.php?t=316246), but it doesn't look like fun.

---

### Post by agengo02 on 2008-03-21
as i dont have much information on linux, i do know this:  itunes = memory hog and not worth it.  ive had just about every mp3 player (minus the monopoliptic death grip known as ipod) and i refuse to use itunes.  you can do quite a bit with winamp and with most players (from the dell dj to the creative zen line) you can just drag and drop when it is connected.  its simple enough as storing the new mp3s in a folder titled "Need To Be Uploaded" and once the uploading has finished distributing them from there to various other folders.  thats the way ive done it from the get go and never had any problems, but you do need to keep up with the organization.  just my .02

---

### Post by bumanie on 2008-03-21
If you must use itunes and zune, your best bet would be to set up a virtual environment for windows. I use virtualbox (binary - free for home use). So far very impressed,  it is quick and smooth and has usb functionality. Follow this guide if you are interested [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by Ripfox on 2008-03-21
Install gtk-pod from the repos, it rocks.

---

### Post by PatrickMoore on 2008-03-21
i shall try these options

---

