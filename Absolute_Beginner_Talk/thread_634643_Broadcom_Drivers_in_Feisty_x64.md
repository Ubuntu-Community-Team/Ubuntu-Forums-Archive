---
title: "Broadcom Drivers in Feisty x64"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Mr.Wellington on 2007-12-07
Hello everyone. 

I am using a HP dv6409wm (laugh all you want at the walmart exclusive) and fiesty fawn 7.04 that is completely updated and has easyubuntu installed. Thats all ive done so far. 

My broadcom wireless drivers will not install or work. I have tried ndiswapper (sp?) and everything from the feisty wiki to no avail. 

I went to the irc channel and someone there (not naming anyone) kindly dumped me into the page for gentoo and redhat.  I pushed further and they said that when it didn't work for them, they just went out and bought a new card that supported what they were trying to do. i don't think that was very professional, nor does it help my problem because I am on a laptop.  

I used some google fu to find this (on these forums no less) [http://ubuntuforums.org/showthread.php?t=50386](http://ubuntuforums.org/showthread.php?t=50386) but I don't know how to install it or even if it is what i am looking for (i am a completely new user).  

please help

---

### Post by betes on 2007-12-07
> **Mr.Wellington said:**
>  i don't think that was very professional, nor does it help my problem because I am on a laptop.please help

First- not many people here are professionals. They're just people. But that doesn't mean you won't find very helpful and nice people.

Do you know what broadcom card you have?  If not type this command into the terminal :

lspci

Somewhere in the output you should see something about wireless and broadcom and it should say exactly what card you have.  That will help people here answer your question and will also give you more ammunition for your googling.

---

### Post by Mr.Wellington on 2007-12-07
[quote=lspci] Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)[/quote]

this is what it reads.

And i don't feel like arguing the point about professionalism.

---

### Post by betes on 2007-12-07
Sorry-

I didn't mean to sound like I was arguing. I agree that the person who sent you to the redhat page wasn't being helpful and you are right to be annoyed.

Here is a HowTo for your wireless card from elsewhere on the forums:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It seems to be up to date, and if you run into specific questions posting in that thread will be most likely to get answers from people who have specific experience with making your card work. 

Good luck!

---

### Post by GSF1200S on 2007-12-07
> **Mr.Wellington said:**
> this is what it reads.

And i don't feel like arguing the point about professionalism.

Please post the results of ```
iwlist scanning
``` 

and well see if your card is receiving signal..

---

### Post by Mr.Wellington on 2007-12-08
betes - I have gotten to the point where it says YOUR-NDISWAPPER-DIRECTORY the first time.  I'm not new enough to software to just type that in blindly: what is the default ndiswapper directory.

Like it suggested, i did a complete fresh install of Feisty before doing that guide. So what do i type if i just left everything default? 

[quote=iwlist scanning]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

[/quote]

Where do i go from there on that part? can ANYONE help?

---

### Post by betes on 2007-12-09
When you uncompressed the ndiswrapper it should have made a directory somewhere with those files.  I think "tar" automatically uncompresses files into the directory you are in when you run the command.  In the case of this how-to, it looks like that would be your desktop.  

If there is not a folder on your desktop that looks like it might be it, try to do a file search (under the places menu) for ndiswrapper.  (Also, it might be hidden, so if you don't see it on your desktop go to Places>Desktop and press "ctrl+H" to show hidden folders.)

When you find it you switch to the directory in which it from the terminal.  For example if its on your desktop you do "cd /home/YOUR USER NAME/Desktop/THE NAME OF THE DIRECTORY".

If you have trouble finding it using search you may repeat the steps in the how-to when you downloaded and uncompressed it.  After you do the tar command do the command "ls -a" and you should see the ndiswrapper directory in there somewhere.  Then just do "cd THE NAME OF THE DIRECTORY".

---

