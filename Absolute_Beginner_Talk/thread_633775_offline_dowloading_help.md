---
title: "offline dowloading help"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by drenalinejunki92 on 2007-12-06
So being quite new to Ubuntu ive noticed that linux relies heavly on the interent unlike windows that uses executables. So my problem the wireless connection does not work in the residence halls at school. only the physical connection works. I have a desktop running xp hardwired and my laptop that cannot connect to the internet. I was hoping there is an easy way to download a program onto a usb drive bring it to the laptop then install it. I have already attempted but i have great difficulty doing so. If this is possible can some one show me an example and maybe walk me through it. thanks in advance.

Cheat notes
one computer with internet one with out
need new programs on linux comp w/o internet
*newb - coming from xp*
 thanks again!

---

### Post by p_quarles on 2007-12-07
I'm not sure that this counts as "easy," but this is what I would do if I were in your situation:

The packages in the Ubuntu repositories are all available via the web here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Download the version of the package you want for your version (7.10) and architecture (if you aren't sure, it's most likely i386), and transfer it to the Ubuntu box via the flash drive. Once it's there, you can install it by double-clicking and entering your password. That's the easy part.

The hard part is dependencies. Many of these packages will rely on libraries or programs that you don't already have installed. The easiest (but most bandwidth-heavy) way around this is to simply download all the dependencies listed on the package's page, and then install those prior to installing the package you want. 

There are other, more complicated, ways of doing this that would allow you to spend less time downloading redundant packages. Let me know if you would rather go that route.

---

### Post by Rocket2DMn on 2007-12-07
If you want both computers connected to the internet, you could buy a second ethernet card for the desktop and setup a network bridge from within windows.  Then you can plug the laptop ethernet into the desktop's second ethernet using a crossover cable (not a standard patch cable).
This will give the laptop an IP like 192.168.1.2 (a private IP), but you will have internet access.
I did this when I was in the dorms when we ran a server from a different computer.

---

### Post by cadcrazy on 2007-12-16
Visit [Offline Ubuntu Package Center]("http://ubuntuforums.org/showthread.php?t=617049")

---

