---
title: "Ignorance is most decidedly not bliss..."
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by dabigguy85 on 2008-03-30
I need some help guys.  I can't figure out how to get mp3s or dvd's to play.  Nor can I get executable file (.exe) to run.  And I can't connect to a wireless network.  Please help, all advice is appreciated.

---

### Post by Helgiks on 2008-03-30
Are you trying to open the windows specific ".exe" files on linux? You can't to that exept through wine or other program for running windows programs.

You need codecs for the mp3's.

EDIT: What wireless card do you have?

---

### Post by Tatty on 2008-03-30
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29]("https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29")

This page shows you how to get restricted formats (such as mp3s) working. It would probably be worth reading the official two links at the top of that link too.

Can you give us some more information on your wireless problems?  Where have you run into problems?  information on your wireless hardware would be useful too.

---

### Post by drs305 on 2008-03-30
dabigguy85,

It would be best if you presented particular problems you are having. If you don't know where to begin, there are many sites that can help. One of these is:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)


Most of what you want to do has probably been discussed at length on this forum at one time or another. Here is a link to do a google search within the ubuntu forums:
[http://www.google.com/advanced_search?q=+site:ubuntuforums.org&hl=en](http://www.google.com/advanced_search?q=+site:ubuntuforums.org&hl=en)

If you still can't find an answer, you can post more specific questions and will get better responses. 

Welcome to ubuntu!

---

### Post by blazercist on 2008-03-30
Ok for mp3's and dvds you need to install the restricted formats see [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

Exe's will not run natively on linux because exe's are for windows, in order for you to run exe's on linux you will need wine.  Its a windows compatibility layer which allows you to play some windows games and run some windows apps on linux.

To install wine assuming you are on Ubuntu Gutsy
open a terminal and type the following

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine

For the wireless problem you have to tell us what hardware you are using the wireless card is especially important if you don't have this information its ok you can find out using the terminal.

open a new terminal and type

lspci | grep Wireless

then just post the output that you get from that command here so we can help further.

---

### Post by Victormd on 2008-03-30
for the mp3's, go to System>Administration>Synaptic Package Manager and search for ubuntu restricted extras. This will install Java, mp3 and other restricted (Non Open Source) extras. You'll need internet access to install the most up-to-date drivers...

So you'll need to take care of your wireless (unless you're connected through your ethernet card cable). What is your comp.?
Try this link:
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

Also, check System>Administration>Restricted Drivers Manager (I'm assuming that you're using Ubuntu 7.10 Gutsy)

As for the EXE files, you will NOT be able to execute them like you're used to in Windows. To run executables in Ubuntu, you will need to install a package called WINE (you can find this in the Synaptic package manger as well) - visit [www.winehq.org](www.winehq.org) for more info.

---

### Post by tgalati4 on 2008-03-30
If you are still having trouble playing multimedia files, then give Linux Mint a spin.  Most multimedia files play out-of-the-box since Linux Mint comes with codecs already installed.

---

### Post by dabigguy85 on 2008-03-30
one thing I don't understand and don't know how to get through isin terminal when I've put in a command it says "[sudo] password for dabigguy85:" and I can't type anything else.

---

### Post by Tatty on 2008-03-30
type in your password and press enter... it will show absolutely no output when you are typing for security, but it is listening.

---

### Post by Victormd on 2008-03-30
> **dabigguy85 said:**
> one thing I don't understand and don't know how to get through isin terminal when I've put in a command it says "[sudo] password for dabigguy85:" and I can't type anything else.

you can type, it simply won't show for your safety...

---

