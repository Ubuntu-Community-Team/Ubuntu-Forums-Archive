---
title: "Installed Ubuntu on NEC Versa E680 laptop"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by bluemarble on 2006-04-11
Hello people,

I just have moved from windows to Ubuntu and have installed on my NEC Versa E680 laptop. So far all has been successful and everything is working, except for  a few packages that seem to play up or run slowly.

I am keen to loose my windows parition and operate only Ubuntu but,

Firstly, I was wondering if there are any tricks and tweaks to help the machine run faster. ie burn CD/DVD takes toooo long

Secondly, If anyone out there is running the same systems who might be up for helping.

There was a third but cant remember for now....

Cheers
Bluemarble
Greener than blue

---

### Post by meborc on 2006-04-11
welcome,

you might try to enable DMA... see - [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA) to get drives working faster... :-k

---

### Post by bluemarble on 2006-04-12
I tried to enable DMA and the results were as follows;

bluemarble@:~$ sudo hdparm /dev/hdc
sudo: unable to lookup  via gethostbyname()
bluemarble@:~$

does this mean .../hdc is incorrect?

Cheers

---

