---
title: "[SOLVED] Install desktop, programs from command line"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Niniel on 2007-12-01
Hello,

I wanted to try out Ubuntu with disk encryption, so I burned myself an alternate installation cd and went to work. Worked ok until I came to the point where programs need to be installed. Apparently, my CD has an error there and I can't install any software.
But the base system is running, so now I'm sitting here (well, not here, I'm writing from a different machine) at the prompt scratching my head over how to get a desktop.
What is/are the command/s to install gnome and all the other usual Ubuntu programs?
I also have a normal 7.10 installation CD, could that be of any help?

Thank you.

---

### Post by bernied on 2007-12-01
If you have a network connection and your /etc/apt/sources.list file makes sense, then the following will install a desktop:
```
sudo apt-get install ubuntu-desktop
```
If you'd prefer a kde desktop, then replace ubuntu with kubuntu, and for xfce, use xubuntu.

Good luck.

---

### Post by Niniel on 2007-12-01
Ah, thanks.
So I wasn't that far off when I tried "sudo apt get install gnome" :)

Anyway, I guess my network is not working even though upon boot it claimed to have configured it successfully because I'm being asked to put in the installation CD. Unfortunately, either that CD is broken as well, or it's not labeled correctly, because it wants one that's labeled "Ubuntu 7.10 _Gutsy_Gibbon_ - Release i386 (20071016.1).

---

### Post by bernied on 2007-12-01
This doesn't necessarily mean that you don't have internet. Try a simple ping:
```
ping google.co.uk
```(You'll need to hit Ctrl-C to make it stop)

You can disable the CD repositories by editing your /etc/apt/sources.list:
```
sudo nano /etc/apt/sources.list
```
Just comment out (with #) any repositories that look like cds.
use Ctrl-O to save, and Ctrl-X to exit, then try the apt-get install again.

---

### Post by XVII on 2007-12-01
> **bernied said:**
> This doesn't necessarily mean that you don't have internet. Try a simple ping:
```
ping google.co.uk
```(You'll need to hit Ctrl-C to make it stop)

You can disable the CD repositories by editing your /etc/apt/sources.list:
```
sudo nano /etc/apt/sources.list
```
Just comment out (with #) any repositories that look like cds.
use Ctrl-O to save, and Ctrl-X to exit, then try the apt-get install again.

```
ping 127.0.0.1
```
Would be more accurate

---

### Post by Niniel on 2007-12-01
nano: command not found :)

---

### Post by XVII on 2007-12-01
> **Niniel said:**
> nano: command not found :)

Command not found for what?

---

### Post by Niniel on 2007-12-01
The nano editor that bernied suggested I use.

I'm in the directory... are there other ways to edit text files? 

Tried just "edit", but that's not it.

---

### Post by bernied on 2007-12-01
nano is a text editor. Try using pico in it's place, so same command, just replace the word nano with pico. And if you don't have pico either, try vim or vi. But for these last two, you'll have to figure out the commands, which I can't help you with.
Maybe [this](http://linux.die.net/man/1/vi) might help.

Could you ping google? Because if not, you're not going to be able to download the packages anyway.

---

### Post by bernied on 2007-12-01
> **XVII said:**
> ```
ping 127.0.0.1
```
Would be more accurate

The OP wants to install packages, and I'm suggesting that he gets them from repositories on the internet. I suggested a ping to google as a way of testing internet connectivity. Pinging localhost won't do that.

---

### Post by Niniel on 2007-12-01
Yes, ping worked, thanks. 

I'll try the other editors. Hopefully something got installed with the base system.

I may still have a vi guide lying around from my university days... (vi for HP unix... fun fun fun :) )

---

### Post by Niniel on 2007-12-01
And therein lies the problem - sources.list only has one entry in it, and that is for that CD. 

How can I read the label of the that CD I do have?

---

### Post by bernied on 2007-12-01
I'm sorry I don't know how to identify the cd or refer to it in the sources.list
I've always used internet repositories.

These are where most of my stuff comes from:
```
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
```
You would need to replace the 'gb' with a country near you, and replace 'feisty' with 'gutsy'.
Or, even better, [check this out](http://www.ubuntu-nl.org/source-o-matic/).

---

### Post by Niniel on 2007-12-01
This is a cool service, thank you.
Now all I have to do is get that over to the other computer...

---

### Post by mellowd on 2007-12-01
vi will always be on any nix system, which its why its useful to learn. vi seems to be buggy on my server though so I've installed vim

---

### Post by XVII on 2007-12-01
> **mellowd said:**
> vi will always be on any nix system, which its why its useful to learn. vi seems to be buggy on my server though so I've installed vim

One of the best text editors ever.

---

### Post by mellowd on 2007-12-01
> **XVII said:**
> One of the best text editors ever.

most definately. the first few times are a bit funny but afterwards its so easy. I use it often at work so it's all I ever use

---

### Post by XVII on 2007-12-01
> **mellowd said:**
> most definately. the first few times are a bit funny but afterwards its so easy. I use it often at work so it's all I ever use

Once you train yourself you can type 50X faster with vi even faster with dvorak.  You can type 100X faster than someone with a qwerty keyboard and MS Office.

---

### Post by Niniel on 2007-12-01
Lol, yes, sure.

Anyway, I did use vi (fortunately I had a Suse 6 handbook lying around with vi commands), and it worked. Personally, I like the text editor that looks like Pine, whatever it's called.

---

### Post by natehall on 2007-12-01
If you want a GUI editor gedit works fine.

---

### Post by Niniel on 2007-12-01
I know, but the whole point of the thread was that I didn't have a GUI. 

But it's downloading and installing now, so thanks for your help, bernied.

---

### Post by bernied on 2007-12-01
Superb, you're welcome.

---

### Post by Niniel on 2007-12-03
It's working, but some things are not quite right.
E.g. the applications menu does not have the Systems folder.

Then there are programs that are supposed to be installed but that are not available, like 7zip (added that myself) or Compiz (came preinstalled, or at least parts of it). 

Weird.

Maybe I'll try to burn a new CD and install again.

---

