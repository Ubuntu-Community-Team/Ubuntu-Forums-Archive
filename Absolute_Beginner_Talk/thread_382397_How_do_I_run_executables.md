---
title: "How do I run executables?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by talon006 on 2007-03-12
I cant believe im asking this, im a big Windows user, and i got ahold of an old school comp. It had windows 98 and it really didnt work. So i figured nows as good a time as any to try linux. I downloaded a NES emulator, and then a couple of other programs which all say they work on linux, but when i double click the executable, nothing happens.  Im sure its something really simple and its punching me in the face as i speak, but i honestly cant figure it out.

plese help:confused: :confused: :confused:

---

### Post by jfinkels on 2007-03-12
.exe files are executable _in Windows_ only! Be careful and make sure you're downloading the right files. If you're looking for an emulator designed for Linux, search the forums for some ideas.

If you really need to run software designed for Windows you need a program called "wine".

What exactly did you download/what exactly do you want to do, people in the forums can solve any problem you need.

---

### Post by siciliancasanova on 2007-03-12
Try **cabextract**

or  **WINE**

Wine works good for me but I'm never trying to run programs, I usually am openening a .exe to get 1 or 2 files out of it.  Also you will want to check **winecfg** in the terminal when you get it installed.  I had to allow my actual linux drive not the virtual windows drive to get the extracted files to show up in my user account.

---

### Post by Lonelynoob on 2007-03-12
If Talon006 is anything like me, he'll still be wondering what file to, in the true english sense of the word:  "execute" in order to run a program.  I finally managed to get gnome PPP onto my "desktop" (windows lingo prevails, sorry).. I unpacked it like a good little noob, now I have no idea what to do with it.

Newness sucks.  bleah.

---

### Post by talon006 on 2007-03-12
alright i downloded, fwNES, zSNES and FCEultra, all linux versions. fwNES and FCEultra both have the smae problem, they both had an executable and a readme, zsnes dosnt have anything at all to start it with.

what im going to do with it is im going to put this Ubuntu loaded computer inside my CUSTOM BUILT GIANT NES CONTROLLER, its as big as a table and fully functional, the idea is that i load it full with NES roms, and ill never have to spend minutes of my life blowing on a NES cartrage again,.

---

### Post by TheRingmaster on 2007-03-12
The best thing to do is to try and find some software in the repos that does the job. Your days of downloading software from the internet are over.

---

### Post by siciliancasanova on 2007-03-12
> **Lonelynoob said:**
> If Talon006 is anything like me, he'll still be wondering what file to, in the true english sense of the word:  "execute" in order to run a program.  I finally managed to get gnome PPP onto my "desktop" (windows lingo prevails, sorry).. I unpacked it like a good little noob, now I have no idea what to do with it.

Newness sucks.  bleah.

If you're having trouble installing from files you download on the net, I would start by installing programs from the synaptic terminal until you are more comfortable with the terminal.

System > Administration > Synaptic Package Manager

Then search for "gnome PPP" and it will be available to download.

---

### Post by jfinkels on 2007-03-12
TheRingMaster is right...use the package manager, Synaptic, which comes with Ubuntu. It makes installing applications very simple. Go to **System > Administration > Synaptic Package Manager**, search for the program you want (or search for "NES emulator" or whatever) and choose to install it!

I've never heard of the other two, but if you download zSNES files, you're probably going to have to compile the emulator before you can run the application, and you may not be ready for that yet. Stick to the package manager for now.

---

### Post by talon006 on 2007-03-12
ok ill try that

---

### Post by talon006 on 2007-03-12
also note, i checked again, they are ment for linux [http://fceultra.sourceforge.net/download.php](http://fceultra.sourceforge.net/download.php)

---

### Post by Lonelynoob on 2007-03-12
> **siciliancasanova said:**
> If you're having trouble installing from files you download on the net, I would start by installing programs from the synaptic terminal until you are more comfortable with the terminal.

System > Administration > Synaptic Package Manager

Then search for "gnome PPP" and it will be available to download.

Sorry I should've explained better..  I downloaded GNOME ppp from a windows machine -- I can't access the net on my Ubuntu machine  (that's why I needed GNOME ppp)  ..  so I've put the GNOME ppp program on my UBUNTU machine and have no idea what to do with it. to get it to run/install/do anything but sit there...

---

### Post by siciliancasanova on 2007-03-12
You need to extract the tarball, is it in a tar.gz format?

[B]Edit:
Example:[/B]
Say your file is **example-1.1.tar.gz**


```

tar -xvzf example-1.1.tar.gz
cd example-1.1
./configure
make
sudo make install

```

---

### Post by Najand on 2007-03-12
I think he needs to extract tar.bz2 balls.
It is easy. Use 
```

bunzip2 <FILENAME>

```
Then use

```

tar xf <FILENAME>

```
Then cd in the dir and go trough configuration and make... I think you can find enough information about it in the README file.

---

### Post by Lonelynoob on 2007-03-12
Sorry guys, I'm lost..  this Synpatic thing "finds" gnome PPP as if to say "yes, the program name exists in our list of programs, but so what?"    it doesn't "find" it anywhere and certainly doesn't give me an option of unpacking anything

---

### Post by siciliancasanova on 2007-03-12
Right click **gnome-ppp** and click "mark for installation" then in the top menu click "apply"

---

### Post by Lonelynoob on 2007-03-12
I think someone's assuming I'm doing Step "X" when I have no idea I need to do step "X"

Synaptic Package Manager.
Search.
Gnome ppp

"Gnome ppp" appears on the LEFT side of the Manager as if to say it has found the NAME ONLY in the Index of program names.  No where else does it appear.

Right clicking on it does nothing.

gnome ppp is sitting on the desktop.

---

### Post by Najand on 2007-03-12
LOL. I am wondering  whhy soome people is making him to install GNOME PPP. He just needs the FCE Ultra, which is a Nintendo Emulator.
To install it the easiest way is to Click on:
System => Administration => Software Sources
Then Check All Options including the ones like universe and multiverse.
Then Open Synaptic
Find the package "fceu"; Right Click on it, and mark it for installation; Then Click Apply to install it. It would be installed in a few minutes.

---

### Post by siciliancasanova on 2007-03-12
Talon is the one who started this thread.  Lonelynoob posted later that he is like Talon in that he doesn't know what to do.  He said he was trying to install gnome-ppp.  No one else told him to install gnome-ppp.  I was only telling him **HOW** to install it.

---

### Post by siciliancasanova on 2007-03-12
> **Lonelynoob said:**
> 
gnome ppp is sitting on the desktop.

What is the full name of the file including the extension?

---

### Post by Najand on 2007-03-12
Hey guys! Please avoid writing yoour questions in other people's thread. It just make it more complicated.

---

### Post by Lonelynoob on 2007-03-12
I have:

A folder named "gnome-ppp" with its unpacked files in it sitting on the desktop.

I also have  gnome-ppp-0.3.23.tar.bz2
sitting on the desktop.

Keep in mind that any "go here and type this"s need to be spelled out as if i was the biggest f*ckin moron this side of the pacos.

---

### Post by siciliancasanova on 2007-03-12
Use code below...

---

### Post by Lonelynoob on 2007-03-12
Sorry.. am I typing that into a terminal?

I typed in the first line and got a "no such file or directory"

---

### Post by siciliancasanova on 2007-03-12
Use code below...

---

### Post by siciliancasanova on 2007-03-12
Ok open up the terminal and type this in one line at a time:

```
cd Desktop
tar -xvzf gnome-ppp-0.3.23.tar.bz2
cd gnome-ppp-0.3.23
./configure
make
sudo make install
```

---

### Post by Lonelynoob on 2007-03-12
During the ./configure routine  I saw this:

checking for C complier default output file name... configure: error: C complier cannot create executables.....

so typing "make" resulted in:
***No targets specified and no makefile found.  Stop.


I think that last word is the computer asking me to do it a favour.

---

### Post by siciliancasanova on 2007-03-12
Try [here]("http://ubuntuforums.org/showthread.php?t=362930&highlight=tar.bz") there seems to be others with a problem with tar.bz.  The people have different files but it's the same situation you're in.

---

### Post by Lonelynoob on 2007-03-12
Thanks for your help dude, seriously.. but, sadly, this is getting ridiculous.. I followed the link, ran some code they were yapping about, it installed somethin that was supposed to do "something",  I'm running your string of code again and now it says "not in gzip format..."

This is all so I can have something, ANYTHING that dials a f*ckin bloody phone number - something I was doing 19 years ago on a commodore 64..  I can't BELIEVE it is this complicated...   I'm quitting for today..

Your patience is exetremely appreciated and much stronger than mine....  feel free to private any thoughts or mockery...  I can't take this.

---

### Post by siciliancasanova on 2007-03-12
Just have some patience and be willing to work with it.  Also you're not getting any other replies because this thread isn't even about what we're talking about now.  Tommorow, post a new thread specific to your question and I'm sure it will be answered in no time.

---

### Post by Lonelynoob on 2007-03-12
Thanks.. you're very patient.  

I deleted the file on the desktop and ran your ./configure on the unpacked gnome folder I created a while back and it seems to be "working" whatever that means..  it's taking forever to go through all the "./configure" stuff, but we'll see...

I thought I said I was quitting...  damn....

EDIT: Never mind..   "make" doesn't work like last time regardless.

---

### Post by talon006 on 2007-03-12
Thanks everyone, after a fresh night of sleep, i got synaptic package manager to download everything i needed

---

