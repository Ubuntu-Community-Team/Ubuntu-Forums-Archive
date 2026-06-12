---
title: "Dual boot for Windows and Ubuntu"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-03-13
I want to install Ubuntu, but I need to keep Windows.  The best solution for for me is to install a second internal hard drive.  I am a novice, but I have someone who will install the second hard drive.  Then when I start up my computer, I want to be able to select from a screen  the operating system (Windows or Ubuntu) without having to press F3 or F8 and change the boot routine.

Is an additional piece of software required or  is it something else?


Thanks for your assistant.

---

### Post by Kobalt on 2007-03-13
Hello,

You can install both Ubuntu and Windows on the same hard drive : we call that a dual boot. When you will turn on your computer, you will have a menu (Grub) that will prompt you on which OS you can boot. Grub comes automatically with Ubuntu. 
Here is some doc on dual booting : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
And some other doc on installing Ubuntu : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you have further questions, feel free.
Welcome :)

---

### Post by BobSongs on 2007-03-13
> Is an additional piece of software required or is it something else?

If you install a second hard disk drive then you should have no problem installing Ubuntu Linux on the 2nd hard drive. No extra software necessary. You just indicate during the setup process that you're going to use the second hard drive for Ubuntu.

The setup process for Ubuntu is frighteningly simple. Just download the setup CD.

You might even be surprised that you can surf the web (if you're using a router) when the Ubuntu Setup CD is finished booting. Unlike the XP setup (where you're paralyzed during the installation) Ubuntu allows you to work in a real GUI (albeit a bit slow since it's loading off a CD) with the ability to surf while you install.

Enjoy your Ubuntu experience and come back with any questions. We'll be glad to assist.

---

### Post by confused57 on 2007-03-13
You might want to consider this method:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by chopperfixer on 2007-03-13
I have a Dual Boot System using two hard drives. (One 120gb and one 160Gb)  First thing I did was to install Windows on one drive, ( I was doing a fresh install, but if you've already got Windows installed and running on one of your drives your half way there).  Once this was done, I made the Windows drive the slave drive, and fitted the second drive making it the master.  Your friend may be able to help you with this if you are unsure.

Once this was done, I restarted the computer and booted from the Ubuntu CD and installed the programme onto the new master drive (labeled hda in Ubuntu). The installer will also format the drive with the correct file system and Linux swap file.

The Ubuntu installer is so good that at the final point of installation it is aware that there is another operating system installed on the slave drive and asks if you would like the option to use it as an alternate operating system.  If you answer yes at this point Ubuntu configures the GRUB Boot Loader to give you the option of a Windows or Linux boot up sequence.   Once completed a OS Choices Menu will be displayed at every boot up allowing you to choose the operating system of your choice.  This gives me the chance to play with Linux and get to know it, whilst the wife and kids can are still happy using Windows. (Windows Messenger is a terrible thing)

Hope this helps.

Chopperfixer

---

### Post by louieb on 2007-03-13
> **chopperfixer said:**
> First thing I did was to install Windows on one drive, ... made the Windows drive the slave drive, and fitted the second drive making it the master.... booted from the Ubuntu CD and installed onto the new master drive 
First time I installed Linux I did the same thing. Beauty of doing it this way you WIn drive is untouched.

---

### Post by explorer716 on 2007-03-16
Thank you very much for your assistant.  With your advice we were to install the second hard drive and get the dual boot feature.

Thanks again,

explorer716

---

