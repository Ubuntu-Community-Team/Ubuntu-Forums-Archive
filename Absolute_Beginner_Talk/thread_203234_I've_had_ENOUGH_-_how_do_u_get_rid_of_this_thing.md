---
title: "I've had ENOUGH - how do u get rid of this thing???"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-24
Hi,

Some may say that I'm giving up too easily but I would say that when NOTHING works there's not much left to do. There's no graphics, I can't edit the boot menu list, I can't fix the wireless... 

By the way, when I try to change the default boot option, I get a stupid error:

" sudo cp /boot/grub/menu.lst /boot/grub/menu.lst " - this line works

" gksudo gedit /boot/grub/menu.lst " - but this doesn't 

error: " (gksudo:4005): Gtk-WARNING **: cannot open display: "

So, how do I get rid of this freakin' thing now? I can just use Partition Magic to remove the Ubuntu partition but my master boot record is now corupted with Grub. Is it possible to remove Grub without having to reinstall Win XP???

Otherwise good luck to you all with linux but this just isn't for me.

Thanks for any responses

---

### Post by PsychoTrauma on 2006-06-24
Instead of using gksudo use sudo.

Use the windows disc to get to recovery console and do "fixmbr". That will reset the mbr without you having to reinstall.

---

### Post by Drakkor on 2006-06-24
I take it that this is dual boot? And grub is on the mbr?
Boot with XP disk hit R for Repair type fixmbr.

---

### Post by Sye d'Burns on 2006-06-24
If I understand correctly when you say that you have no graphics, you're doing this from the console... if so you'll want to use a text editor as opposed to gedit. That would explain why it can't open the display. Try 

sudo nano /boot/grub/menu.lst

---

### Post by PsychoTrauma on 2006-06-24
I should have read more closely since I did not notice the no graphics part i'm sorry.

Sye d'Burns advice is what you want to try so just ignore my earlier post if you're not  in a graphical mode.

---

### Post by catlett on 2006-06-24
[QUOTE=ovimunt]Hi,

Some may say that I'm giving up too easily but I would say that when NOTHING works there's not much left to do. There's no graphics, I can't edit the boot menu list, I can't fix the wireless... 

By the way, when I try to change the default boot option, I get a stupid error:

" sudo cp /boot/grub/menu.lst /boot/grub/menu.lst " - this line works

" gksudo gedit /boot/grub/menu.lst " - but this doesn't 

error: " (gksudo:4005): Gtk-WARNING **: cannot open display: "

So, how do I get rid of this freakin' thing now? I can just use Partition Magic to remove the Ubuntu partition but my master boot record is now corupted with Grub. Is it possible to remove Grub without having to reinstall Win XP???

Otherwise good luck to you all with linux but this just isn't for me.

Thanks for any responses[/QUOTE]
Nothing is corrupted you installed a different operating system on your computer and this system employs a boot loader that can boot multiple OSs unlike XPs boot loader.

This has already been mentioned but I thought I would add a little more detail to the process.

If you have an XP install disk put it in and boot to the disk. When you get the first prompt type "R" (without the quotes) this will start the recovery mode. You will come to another prompt where it will ask you which copy of windows you want to enter to run the recovery from. You will most likely only have one to choose from so enter "1" (again without the quotes)

This will take you to a windows comand prompt.  C:\ 
At C:\  enter  "fixmbr" (without the quotes)
You will be given a warning about loosing the ability to boot to other partitions etc. Don't worry just enter "Y" to continue.
You are done. Windows will start normally. If you have Partition Magic that will do just fine. Delete the linux partitions and resize your windows partition back to it's original size.

Stick with windows, linux takes alot of effort if you don't come from a unix background.

---

