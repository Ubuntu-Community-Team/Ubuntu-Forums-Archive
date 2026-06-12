---
title: "Xubuntu to Win 7 OS"
date: 2012-10-03
forum: Any Other OS
---

### Post by griffinschulz on 2012-10-03
I am a beginner; so I posted this here instead of the other thread.

Not to outsource, but I listed the question on Yahoo Answers, so here's the link:
[http://answers.yahoo.com/question/index?qid=20121002172546AAaRmVs]("http://answers.yahoo.com/question/index?qid=20121002172546AAaRmVs")

The question reads:
> [SIZE="3"]**How do I get my Xubuntu Linux netbook to boot Windows 7 from my USB flash drive?**[/SIZE]
I have an Asus 'Eee PC' 900A netbook.

When it turns on, the Asus goes through an Xubuntu loading screen, clearly Linux OS..
But I don't know ANYTHING about Linux.

I have Windows 7 on an 8gb USB flash drive. 
I tried pressing F2 to go into the 'Setup', I made sure the Boot Load priority 1 is set on "Rem Dev" for USB. 

I'm stumped on a screen that reads "GNU GRUB version 1.99-12ubuntu5"
It then lists 4 boot up options; Ubuntu/Linux normal and recovery, and then Memory test w/ 2 different variations.

I tried doing some research on the web through my other computer... But its all Greek to me. Some sites say to use Terminal (which I understand is similar to Command Prompt) but I can't even begin to understand the tutorials or what these Linux prompts mean.

Please feel free to respond here; I'm not asking anyone to register with Yahoo.


I just don't know anything about Linux OS's..

---

### Post by rai4shu2 on 2012-10-03
It would help people if you let them know what you're asking:

> How do I get my Xubuntu Linux netbook to boot Windows 7 from my USB flash drive?
I have an Asus 'Eee PC' 900A netbook.

When it turns on, the Asus goes through an Xubuntu loading screen, clearly Linux OS..
But I don't know ANYTHING about Linux.

I have Windows 7 on an 8gb USB flash drive.
I tried pressing F2 to go into the 'Setup', I made sure the Boot Load priority 1 is set on "Rem Dev" for USB.

I'm stumped on a screen that reads "GNU GRUB version 1.99-12ubuntu5"
It then lists 4 boot up options; Ubuntu/Linux normal and recovery, and then Memory test w/ 2 different variations.

I tried doing some research on the web through my other computer... But its all Greek to me. Some sites say to use Terminal (which I understand is similar to Command Prompt) but I can't even begin to understand the tutorials or what these Linux prompts mean.

This is not a Windows support forum. I have no idea how Windows 7 "works" nor am I inclined to find out.

---

### Post by griffinschulz on 2012-10-03
> **rai4shu2 said:**
> It would help people if you let them know what you're asking:



This is not a Windows support forum. I have no idea how Windows 7 "works" nor am I inclined to find out.

...

Right... But if I take this to Windows, they'll give me the same run-around..

I have an Asus that is LINUX.
And I'm just trying to change Operating Systems, there's no need to add to the fact that you're clearly not a Windows fan.

**I get that. **

But when I put my USB into my LINUX OS netbook, the netbook won't boot the new OS. So at this point, the issues begins on a Linux Support thread because I HAVE A LINUX. Until I have an actual problem with Windows, I have no need or justification to ask them why my LINUX won't boot a new OS from a flash drive.

Alternatively, I'm sure I could put Linux OS into my Windows computer and it would run that just fine, but that is not the issue at hand.



**Please if there is anyone that is truly trying to assist, please do. I understand the community here is a Linux OS fanbase. I'm only trying to get my netbook to where I can use it, unfortunately I do not know how. And it would serve me no purpose to learn it at this point. Please assist.**

---

### Post by windscape on 2012-10-03
Hi,

To get a PC to boot from the USB device, you need to tell the BIOS to do that. Usually there is a key that you can press during the very initial startup that will either take you into the BIOS Setup or to a Boot Device Menu. The documentation for your netbook should tell you which key to press.

---

### Post by egeezer on 2012-10-03
Put you USB in the netbook and leave it there when you shut the netbook down. The very first screen that appears when you start your netbook from a shutdown (not simply a restart) will have between two and four little notes usually at the bottom of the screen, with text like Setup or Startup or something similar, followed by F1 or Esc or Del - keys to press to access the BIOS boot order.  When you use the proper key, you will be shown a screen that will allow you to change the order in which the BIOS searches to find a medium to start from: hard drive, USB, CD (if it has one), etc.  Choose USB or External HDD or whatever it calls your USB as first.

---

### Post by jmore9 on 2012-10-03
Its not a linux fanbase its a linux support forum.  I use windows 7 on one dell machine because the tv app is better than anything i can find on linux.  But how to get it into the grub bootloader i have no idea.

You could try googling "installing window to grub" or try " installing windows to ubuntu bootloader".  Something like that.

Or google dual boot ubuntu with windows 7

---

### Post by yragnos on 2012-10-03
You will need to tell you OS to select the drive at boot time.

This depends on your OS - newer OS may be easier, older OS, the USB drive shows up under hard drives, not neccesarily under removeable drives.

So you need to change the order of boot from your hard drives and move the USB drive if listed to the first boot partition.



> **griffinschulz said:**
> I am a beginner; so I posted this here instead of the other thread.

Not to outsource, but I listed the question on Yahoo Answers, so here's the link:
[http://answers.yahoo.com/question/index?qid=20121002172546AAaRmVs]("http://answers.yahoo.com/question/index?qid=20121002172546AAaRmVs")

The question reads:


Please feel free to respond here; I'm not asking anyone to register with Yahoo.


I just don't know anything about Linux OS's..

---

### Post by oldfred on 2012-10-03
Moved to otherOS since Windows issues.

Windows will only boot from internal drives. And the normal recommendation I have seen is 30GB for Windows 7. It may install into a lot smaller but I do not know how small. But only the installer will boot from a CD or USB flash device. The actual install has to be internal as the license is only for one computer.

---

### Post by critin on 2012-10-03
8gb won't give much room you know.  Did you use WinToFlash to install it?

I'm wondering if windows will even boot from the ext4 hdd.  I don't know for sure, but I think it's doubtful.  Linux will boot from windows formatted disk, but windows is more picky.

Oh, I see oldfred has answered while I was researching.

Play with the xubuntu until you learn how to use it--it's not that hard.  And it doesn't restrict you with all those licenses requirements.  xubuntu is a great os.

---

