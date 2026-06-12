---
title: "A few quetions from a newly transferred Ubuntee"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by AliL on 2007-07-20
Sorry, I was trying to come up with a snappy 1 word name for a Ubuntu user and all I could come up with was Ubuntee (it's awful so my apologies) :D .

Anyway, I've been using Ubuntu for about 2 weeks now and am quite happy with it, considering it recognized more of my hardware out-of-the-box than XP did, however I have a few noobish questions for y'all.

1. In keyboard shortcuts, what do some of the keys refer to, i.e. 0xf5 0xe5 0xec 0bb2 etc...

2. Is there any way to access the multimedia keys on my keyboard/notebook (I have a Toshiba Satellite A30 I'll post a picture of what I mean as well)

3. I'm running the laptop wirelessly through a Broadcom chipset (which initially was a pig to install but I eventually found a very simple way of doing it) into my home network which has a 500GB Freecom NAS drive attached to the hub, but whenever I try and access the NAS through Places->Network->Freecom (this is what it's called) I keep getting the error message "Sorry, couldn't display all the contents of "Windows Network: Freecom". Is there any way of fixing this?

4. Is there any way of making the touchpad less touchy-feely for example when I scroll down a webpage in firefox and I've only been touching the touchpad for a few milliseconds and I lift my finger off when it's pointing to a link it loads the link up. This is very frustrating as it means I'm constantly using the back button.

5. Is there a way of making the text less wide. Not smaller, but just less wide because in some menus e.g. tools or bookmarks in firefox (the dropdown ones) the values of the dropdown menus seem to stretch across a very large portion of the screen and I'd like to reduce it.

6. I seem to have 3 different search facilities available to me: desktop search, deskbar search, and search for files. Why are there 3 and which is the best?

7. When I got Ubuntu I got it to dual-boot with XP, and the way I did this was to completely wipe the hard drive, get the XP CD and create a 10GB partition for windows and install that how i wanted it, then I live booted to Ubuntu and did the install method from the desktop the windows partition was then labelled /dev/sda1. I then created a primary partition of 10GB in ext3 format for Ubuntu which was labelled /dev/sda2 and then created a third partition for the swap file of 512MB which got labelled /dev/sda3 with an arrow to /dev/sda5 (i'm guessing a primary partition with the swap file being a logical partition in it?) and then finally created another primary partition in FAT32 format for my multimedia and various files which could be read and written to by both Ubuntu and windows. However when I booted back into windows I made this folder the "My Documents" folder so windows would put all my files there automatically that were not part of the programs or operating system. However back in Ubuntu, the MY Music, My Pictures and My Videos Folders have padlock icons by them and I am now unable to write inside these folders, why? Also How can I edit the names of these partitions/mounted drives as having the names sda1 and sda3 on the desktop is quite annoying having to remember which is which.

8. When I boot up my wireless card automatically detects my wireless network and trys to connect but as I'm using WEP it asks me for the keyring manager key(?) and I have to input this each time I boot up. Is there a way of it automatically doing it without having to ask me or is this a(n) (annoying) safety feature.

9. How do I completely erase a blank CD-RW?

10. [SOLVED] How do I edit files in my /boot/ folder e.g. I want to upgrade the memtest86+ to the newest version (1.70) but I keep getting a write permissions denial when I try and overwrite the file.

</rant>

Thanks for your time,

AliL

---

### Post by Mornedhel on 2007-07-20
> **AliL said:**
> 1. In keyboard shortcuts, what do some of the keys refer to, i.e. 0xf5 0xe5 0xec 0bb2 etc... Probably multimedia keys (Play/Pause, volume control...)

> **AliL said:**
> 2. Is there any way to access the multimedia keys on my keyboard/notebook (I have a Toshiba Satellite A30 I'll post a picture of what I mean as well) See above. Redefine the shortcuts if the binds are not correct (pressing your multimedia keys as you would any other)

> **AliL said:**
> 4. Is there any way of making the touchpad less touchy-feely for example when I scroll down a webpage in firefox and I've only been touching the touchpad for a few milliseconds and I lift my finger off when it's pointing to a link it loads the link up. This is very frustrating as it means I'm constantly using the back button. Are you using a Synaptics touchpad ? If so you can get the drivers for that and a utility to change touchpad sensitivity (not sure about that).

> **AliL said:**
> 7. However when I booted back into windows I made this folder the "My Documents" folder so windows would put all my files there automatically that were not part of the programs or operating system. However back in Ubuntu, the MY Music, My Pictures and My Videos Folders have padlock icons by them and I am now unable to write inside these folders, why? I'm guessing you don't have the rights to access these folders. Try to chmod them so a non-root user can access them.

---

### Post by kagashe on 2007-07-20
> **AliL said:**
> 
7. When I got Ubuntu I got it to dual-boot with XP, and the way I did this was to completely wipe the hard drive, get the XP CD and create a 10GB partition for windows and install that how i wanted it, then I live booted to Ubuntu and did the install method from the desktop the windows partition was then labelled /dev/sda1. I then created a primary partition of 10GB in ext3 format for Ubuntu which was labelled /dev/sda2 and then created a third partition for the swap file of 512MB which got labelled /dev/sda3 with an arrow to /dev/sda5 (i'm guessing a primary partition with the swap file being a logical partition in it?) and then finally created another primary partition in FAT32 format for my multimedia and various files which could be read and written to by both Ubuntu and windows. However when I booted back into windows I made this folder the "My Documents" folder so windows would put all my files there automatically that were not part of the programs or operating system. However back in Ubuntu, the MY Music, My Pictures and My Videos Folders have padlock icons by them and I am now unable to write inside these folders, why? Also How can I edit the names of these partitions/mounted drives as having the names sda1 and sda3 on the desktop is quite annoying having to remember which is which.


From [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite"):
>  How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

    * Save the edited file
    * Read #How to remount /etc/fstab without rebooting 

kagashe

---

### Post by boumcke on 2007-07-20
Waouw, that's quite a long post ! I won't be able to answer every question, but here's what I can tell you :

1 and 2. You may want to take a look at xev. That's a small program that allows you to monitor the inputs in X, it's installed by default so you won't have to do anything to make it work. Open a terminal, launch the program by typing simply xev, and you should see a small window appear. Now whenever you type a key, you should see in the terminal some info about the pressed key. The most important thing for you is the hex code of the key, values such as 0xf5 0xe5 etc. Try it with your multimedia keys, normally you should see something if they're supported. If that's the case, you can use another program named xmodmap and practically map them to any key you want.

6. I didn't know there were 3 different kind of searches, but I know at least two. The basic search, accessible via the "Places" menu is just the built-in gnome search engine. It allows you to search in any file of your system. Take a look at the different options, it's quite easy to understand. The deskbar is a whole other thing. It's based on a small daemon named beagle. At the first launch, you specify some folders that you want to be indexed by the daemon, that's the places you'll be able to search. It's a more powerful search, if you want to get more informations just google beagle and you'll find better explanations than those I could give you. The only thing I know is that it's quite resource-consuming.

7. I got the same problem years ago. You have to take a look at the /etc/fstab file. It's the place where you define the options of the different filesystems. The system mount your FAT partition with root as the owner, and that's what you need to change. Try searching fstab and FAT32, there are plenty of posts about that I think.

8. I suppose you're using network-manager. Personnaly I don't like this program, so I don't use it. I prefer another one called wicd. If you want to give it a try, there's no need to type your WEP password each time. Check [http://wicd.sourceforge.net](http://wicd.sourceforge.net) if you want more details.

Hope that'll help...

---

### Post by AliL on 2007-07-20
@ Mornedhel: I think it's an ALPS touchpad rather than a Synaptics touchpad.

I don't think they're bound to the multimedia keys as I've tried pressing them yet nothing happens and when I go into keyboard shortcuts and I try to bind these keys to anything when I press the button nothing happens, its as if Ubuntu is ignoring them or is not aware they're there.

Any help on chmod? Sorry I'm not very adept at this terminal stuff yet. Or is kagashe's idea better?

@ boumcke

I don't need to type in the WEP password each time, but the password for my keyring manager. God if I had to do the WEP key each time I'd go mental considering its a huge HEX key.

---

### Post by Mornedhel on 2007-07-20
> **boumcke said:**
> 8. I suppose you're using network-manager. Personnaly I don't like this program, so I don't use it. I prefer another one called wicd. If you want to give it a try, there's no need to type your WEP password each time. Check [http://wicd.sourceforge.net](http://wicd.sourceforge.net) if you want more details.

Actually, in Feisty (maybe in Edgy too, but I never got the opportunity to test Edgy), the network-manager asks you once for your password to the default keychain. It's not as troublesome as having to manually re-enter a loooong passphrase everytime. And the default keychain can hold the wireless key for each network you routinely use.

It's not as bad as in Dapper Drake.

Edit : Kagashe's right. I thought they were separate folders but obviously I need to read more carefully. Sorry about that. However, you WILL have to learn how to use a console at one point or another.
I dunno about ALPS touchpads, does anyone know if there are specific drivers out there ?
As for your multimedia keys, sometimes they are indeed not recognized at all by Ubuntu. I have an Acer Aspire 5672 WLMi and mine work perfectly. Lucky.

---

### Post by boumcke on 2007-07-20
You should try kagashe's idea. Chmod-ing your partition would allow you to write only until next reboot. With kagashe's trick, it would be permanent.

---

### Post by AliL on 2007-07-23
I tried kagashe's trick but to no avail. I din't really know what I need to modify from the code that's there except for changing hda1 to sda3 (as sda3 is the FAT32 partition.

@Mornedhel

So am I stuck with typing the keyring manager key every time i boot into Ubuntu or can I turn it off so it doesn't ask me?

---

### Post by imdano on 2007-07-23
I think the only way to get rid of the keyring prompt is to use another network manager.

---

