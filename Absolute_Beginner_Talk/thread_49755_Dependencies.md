---
title: "Dependencies"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-17
One thing about Linux, there is always a dependency for a dependency. 

So far having to download packages from internet and installing from cd, I have very little luck getting bluetooth up and running. I am trying to install Gnome-bluetooth, but after I downloaded every file that I can think of was missing, the missing ones had missing depencies! Darn, where can I get a simple thing like: 
Download Program "X" and the necesarry dependencies is included. At least on the Debian site the depencies is listed, but you pick one you get four new ones and so on and do forth. 

Unless there is some real clever person that can tell me how I can add my phone as a Bluetooth modem. So far I was able to see and connect and pair my phone, but it seems I need the Bluetooth utilities and its growing list of depencies...

I DEPEND on you help.....


Please

---

### Post by damonw5 on 2005-07-17
Have you tried using a program called Synaptic? It's in the menu under "System." It will let you search for "gnome-bluetooth" and when you choose to install it, it will automatically install the required dependencies.

Make sure you enable the "universe" and "multiverse" repositories as it says at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

Let me know if this helps.

---

### Post by aysiu on 2005-07-17
One thing about Linux--people always try to do things the Windows way on it.

It can't get any easier than opening a terminal and typing *sudo apt-get update* and *sudo apt-get install gnome-bluetooth*.

Or you can use Synaptic Package Manager if you want a GUI for the same thing.

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=damonw5]Have you tried using a program called Synaptic? [/QUOTE]

This particular poster does not have fast internet. His complaint is valid, I often call Ubuntu "a broadband OS."

What this is called is "RPM Hell" (or "Deb Hell" in our case).

As I have said before, if I did not have broadband I would use Debian -not Ubuntu- because all of the debian packages are on CDs. Much nicer.


The only shot you have parent poster is this how to:

[http://www.ubuntuforums.org/showthread.php?t=49630](http://www.ubuntuforums.org/showthread.php?t=49630)

Then you can make your own Deb CDs.

---

### Post by GrootBrak on 2005-07-18
[QUOTE=poofyhairguy]This particular poster does not have fast internet. His complaint is valid, I often call Ubuntu "a broadband OS."


[/QUOTE]


Thanx Poofy for sticking with me. I should have told them again, I do not have ANY internet with Ubuntu. I have to download with a cell-phone. (Don't even have a fixed line at home, can't afford to. My company provides me free of charge all time and data I can get via my cellphone, but its a bit slow. With luck I get to 28.8kb/s....) 

I have 9 Debian CD's and that is a FANTASTIC help. But I still have lots of dependency problems. The joke is most of the dependencies is so small files, I can download it in seconds, but it takes much longer to locate them!!!

BTW. After my post last night, I successfully installed Bluetooth and phone manager, and wow. I can send SMS via my phone. I had to use DPKG -i to install it. Why won't Synaptic see the files and list them when it is in my repository?
To add files for synaptic I use the following:

dpkg-scanpackages dists/warty/main/binary-i386 /dev/null >Packages

Synaptic listed most of the packages I have in the repo, but half of them were missing. Is there something I should do? How can I verify the new packages is all there?

---

