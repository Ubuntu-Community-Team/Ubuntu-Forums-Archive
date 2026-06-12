---
title: "Help install Ubuntu on iBook G3 dual USB"
date: 2012-01-01
forum: Apple Hardware Users
---

### Post by DDukes94 on 2012-01-01
Alright, so I bought an Apple iBook G3 dual USB with a PowerPC G3 processor @ 500Mhz.  Its got the 64mb. on-board RAM w/ a 128mb. stick.

I've got it running Mac 10.4.11 Tiger.  I know I can run older Ubuntu on this machine.  I'd prefer to dual-boot both OSs.  

I've got an i386 install disk of 8.04 LTS that I've used on many a PC.  

I'm sure this sounds very noob like, but it won't boot from it, and I've got the Ubuntu Mini installer that uses the internet to download, but I don't really know networking very well and I would have to use WiFi but despite trying I can't seem to get connected.

What I would like to do is dual-boot them, hopefully using a Ubuntu install disk that isn't all text based. 

I've researched and researched, I've found 1 video of a guy doing it, but his instructions are really really horrible.  

Any help available is appreciated!  Thanks!

-Dylan Dukes

---

### Post by theos911 on 2012-01-01
Hello,

Your machine is PowerPC. An i386 CD will not work. PPC and x86 are two very different architectures.

Plain Ubuntu is likely to be very slow on that machine. Try PPC Lubuntu, rsavage has an excellent guide posted on installing it found [here]("http://ubuntuforums.org/showpost.php?p=11020435&postcount=1"). You may also be interested in [MintPPC]("http://www.mintppc.org/content/installation-instructions").

However, 192MB of RAM is not a lot. 128MB is the minimum RAM needed for both MintPPC and PPC Lubuntu.

---

### Post by DDukes94 on 2012-01-02
Alright, umm..

Thats for 11.04, I have the 12.04 installer of Lubuntu now, what I do is I pop the disk in, at the first boot I type "Live"

it runs some stuff then gives me a CLI?

I haven't a clue what to do from here... and I've read through most of his instructions and they don't make any sense of my situation.

:S

This iBook is driving me nuts.

---

### Post by rsavage on 2012-01-02
12.04 is still in development. If you are newish to linux then I wouldn't recommend you try it. 11.10 is the current release. There is no working powerpc disk for that, however, so you have to go via 11.04 and upgrade. It is in the instructions.
 
See the release notes for your CLI problem [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot) .

---

### Post by DDukes94 on 2012-01-02
I am new to Linux in the way of installing this method.

I am used to installing with a GUI or using a text method to put in information then it just starts.

Here is what I've done now and I'm getting problems still.  

I downloaded the PPC Ubuntu 8.04 mini installer.  And it runs and I select my language, choose USA Macintosh Keyboard, get the network running (I think), and I use the default United Kingdom install source, I choose next then it flashes a download thing for a second then brings me to a plain blue screen with a grey bar at the bottom that I can write at, but it isn't a command line.  I leave it there and nothing happens.

---

### Post by rsavage on 2012-01-02
Why have you gone for 8.04?  Sorry, have no clue what you are on about.

---

### Post by DDukes94 on 2012-01-02
I figured shoot for 8.04 because it would be lighter than a newer distro.

I mean, its a G3 @ 500mhz so It can't handle much, I'm hoping to get this where I can surf the internet at decent speed.  I've been using it to write a resume and occasionally check Facebook, but Youtube is completely out of the question, I can't listen to music on it, even my Gmail is super slow.  So I'm hoping by dual-booting Linux, but primarily using Linux and maxing out the RAM I can get this to be a nice little netbook.  I bought it for $40 online and bought a $10 charger, so I won't be horribly disappointed if this doesn't go anywhere but trying to put Linux on this has turned into like a Earth-shattering task.


I think what I'll do is film me doing what I've done so far, post it to Youtube, and you guys can help me with what I'm doing wrong?  

You don't know how thankful I am for your support, I'm very computer savvy but this has blown what I know out of the water into the pond like 3 miles away.  No joke.  Like, I know the ins and outs of Windows like the back of my hand, I know Mac fairly well, and I've been using Ubuntu on and off since 2008 but its only been on PCs, so it was a graphical install the whole time, and once it was installed then I could use the package manager to install everything else.

Whew, and I thought tri-booting Windows 7, Mac Tiger, and Ubuntu 8.10 on a Dell Inspirion B130 was hard...

---

### Post by rsavage on 2012-01-02
The desktop packages for 8.04 are not updated anymore so don't install that.
 
EDIT: Just to add, don't know if you've made space on your hard disk for ubuntu?  It's probably easier to do it before installing, although you can do it from the text installer. 
 
Download the 11.04 mini cd. Run the cd and type "cli" at the yaboot prompt. Choose the manual option for setting mirror repositories. Make sure it is set to "ports.ubuntu.com" with directory "/ubuntu-ports/". I can't remember if you need the quotes or not. Haven't done it for a while. I may have got that wrong in the instructions. You'll have to let me know what works.
 
If you have a classic Airport wifi card then during the install you may be told you are missing the non-free firmware file "agere_sta_fw.bin". This can be ignored at this stage. 
 
I know the installer does appear to hang at one point with a black screen. If you give it a couple of minutes, the download should kick in. Also, the screensaver (black screen) does come on during the installation just to confuse you more!
 
Then immediatly upgrade to 11.10. It's just easier to install lubuntu that way.
 
Lubuntu is designed to be run on old computers so it will be fast even at version 11.10. 
 
You don't have enough memory for the live cd so you would have to use a text installer even if it was a i386 computer. The text installer asks the same questions as the GUI installer. It is just less pretty.
 
You can do it!

---

