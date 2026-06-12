---
title: "How to uninstall ubuntu"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by veryconfused on 2007-06-14
Hello, i was wondering how to take off ubuntu, im sorry to say thats its just made my life more complicated, not only dose it not let me change my screen size from 800x600 to 1024x768, and my screen refresh rate higher, or wont let me on the internet (dial-up), but now it messed up my internet cash (every time i go to a web page ive been to, i have to wait longer for it to download, because somehow my internet cache got cleared) and it resets my security update downloads for windows, and i have a very slow connection, someone please help.

---

### Post by veryconfused on 2007-06-14
someone help.

---

### Post by nukkariffic on 2007-06-14
A couple things...

You said that it won't let you on the internet, but then go to say it messed up your cache when you're browsing websites.  Which is it?

Do you have Ubuntu on the same HDD as Windows, but in a separate partition, or do you have it on its own HDD?

As for the video problems, you need to give us more info.  You should check the compatibility list and see if your hardware is compatible with Ubuntu.  

I honestly have no idea who it would mess w/ Windows... it's on a separate partition/HDD.

---

### Post by veryconfused on 2007-06-14
Yes its on the same HDD as windows, and when i said it messed up my cache, i ment on widnows, not on ubuntu. Reply Please

---

### Post by Jimmyfj on 2007-06-14
This is very confusing info you provide - You say that you've installed Ubuntu on the same HDD as your Windows, meaning you have a dual-boot system. Then you go on telling that the internet cache is messed up in your Windows I-net cache? How can this bee? You do not alter your I-net-cache on your Windows partition while running Ubuntu, not even if you have enabled NTFS read/write in Ubuntu. I therefore must assume that the messing up the cache thing is a Windows specific matter.

Having said that, you HAVE to provide us with more information about your Ubuntu setup - I need information about what graphics card you have installed in your computer. Do you connect to the internet via cable or wireless? Also make a copy of any error messages either by taking screen shots or command line tekst output. Thank you.

---

### Post by feistyfirsttimer on 2007-06-14
Hi,[[

You wrote that Ubuntu > wont let me on the internet (dial-up)  I've found that a good way to establish a dial-up link is by using **wvdial**.  You need to run **wvdial** in a terminal.  It's a little involved to go into right here but type ```
man wvdial
``` in a terminal for good instructions.

---

### Post by Bohlio on 2007-06-14
Well, If you really wanna get rid of ubuntu, thats your choice... (a bad one though :-P)
You dont really "uninstall" ubuntu, What you can do is, boot into the LiveCD, Run Gparted, Delete your Swap and ext3 partitions, add the empty space back to your windows partition, reboot from a Windows CD, Then type in "fixmbr". Thats either exactly how you do it or pretty close, Search the forums before you post as I'm 99.9% positive there is a guide to this alread on here.

---

### Post by bone43 on 2007-06-14
> **veryconfused said:**
> Hello, i was wondering how to take off ubuntu, im sorry to say thats its just made my life more complicated, not only dose it not let me change my screen size from 800x600 to 1024x768, and my screen refresh rate higher, or wont let me on the internet (dial-up), but now it messed up my internet cash (every time i go to a web page ive been to, i have to wait longer for it to download, because somehow my internet cache got cleared) and it resets my security update downloads for windows, and i have a very slow connection, someone please help.

Have a look here ...

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Read thru it first and you should be fine, remember to do the fix MBR part!

---

