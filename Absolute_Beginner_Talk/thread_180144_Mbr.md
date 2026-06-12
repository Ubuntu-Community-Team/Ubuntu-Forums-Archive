---
title: "Mbr"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-05-21
If I format my windows drive, which is set as master, will I, or won't I mess up the MBR of that hard drive, thus making grub no longer avalible?  Or will it by some miracle not mess with the MBR.

---

### Post by catlett on 2006-05-21
It will erase grub and put the windows loader back and not recognise ubuntru
Wait a minute. If you are just formatting you will loose grub IF it was placed there during your windows install. If you are not reinstalling windows, no loader will be put on.
What is your hard drive/partition set up and what is the reason for the formatting?

---

### Post by ajgreeny on 2006-05-21
If you have a floppy drive put grub onto that before you reformat windows, then when you reboot with the floppy in, and set as first boot device you will get the grub menu as before.

sudo grub-install /dev/fd0 

This assumes the floppy is listed in your /boot/grub/device.map file like this:-
(fd0)	/dev/fd0

If not add that line at the bottom of device.map and all should work.

Once you have reformatted, if you install windows, you will get back the mbr, which you can then overwrite with grub by doing:-

sudo grub-install /dev/hdx  (where ever your mbr is).

This general grub installation has got me out of several problems in the past and I always keep a copy of grub on a floppy for emergencies.  Give it a try!

---

### Post by JNowka on 2006-05-21
Ok I am going to erase my windows drive on the box I have linux installed on.  I want to format that drive and use it as extra storage and a public drive on my home network so that multiple computers will have the same games and programs without the need of reinstallation or losing game saves.  My windows drive is set as master and my Ubuntu drive is set as slave.  I was told that if I format my windows drive the boot loader would still be there in the MBR on the windows drive.  I have Ubuntu already set up the way I want it so I don't wanna have to reinstall, expecially since it is my network server.

---

### Post by catlett on 2006-05-21
[QUOTE=ajgreeny]If you have a floppy drive put grub onto that before you reformat windows, then when you reboot with the floppy in, and set as first boot device you will get the grub menu as before.

sudo grub-install /dev/fd0 

This assumes the floppy is listed in your /boot/grub/device.map file like this:-
(fd0)	/dev/fd0

If not add that line at the bottom of device.map and all should work.

Once you have reformatted, if you install windows, you will get back the mbr, which you can then overwrite with grub by doing:-

sudo grub-install /dev/hdx  (where ever your mbr is).

This general grub installation has got me out of several problems in the past and I always keep a copy of grub on a floppy for emergencies.  Give it a try![/QUOTE]

I can't get grub to install to a floppy. Were you talking about installing from the terminal? Or were you talking about a system install? I mounted a floppy. I put (fd0) /dev/fd0 in the device map (because I kept getting an error about no bios drive). When I ran grub-install it said it installed (after a dialogue about an xfs bug). When I open the floppy it is empty? What am I doing wrong? I have always wanted a floppy version of grub. I have had my share of error 17's and 21's.

---

### Post by confused57 on 2006-05-21
I created a grub boot floppy using these instructions:

[http://ubuntuforums.org/showthread.php?t=6195](http://ubuntuforums.org/showthread.php?t=6195)

First I formatted the floppy with ext2.
Opened a terminal, entered "sudo su" for root permissions,
then copied and pasted the commands as given.

I didn't start a root terminal as suggested at the beginning, skip down to formatting the floppy...I did this in Dapper after using "Ala Carte" to add "Floppy formatter" to the system tools. 

I haven't tried the boot floppy yet, but there is a file on it called "boot".

It's my 1st attempt at making a grub boot floppy, may give it a go to see if it works...

---

### Post by catlett on 2006-05-21
It didn't work for me. I got an error on start up. "1962: No operating system found. Press F1 to repeat boot sequence"
When I take the floppy out, grub boots normally. So it is booting to the disk it just isn't recognising. I wonder if it is because the floppy is formatted ext2? That is the only thing I can think of because when I forget and keep a floppy in when I shutdown. The next startup I get "error not a systen disk. press any key to reboot".
I wonder why the ext2? Grub lives on windows partiutions all the time. IU'm going to try and format it with fat and see what happens.

---

### Post by catlett on 2006-05-21
[COLOR="Red"]Victory!!!!!! [/COLOR]I just took a little more time to understand what he was instructing me to do. Then I realised I had more things in my /boot/grub than him.
Basically what he instructed is to format a floppy to ext2. Then he gave a command to make a filesystem on it. Mount the floppy to /media/floppy0. Then a command to make a directory /media/floppy0/boot/grub. Finally, copy over everything in /boot/grub to /media/floppy/boot/grub.
My error was I was only cp-ing the 2 files he listed when I actually had 11 things. So I just cp-ed the 11 things and PRESTO I just booted in with my grub floppy. 
Thank you confused57. (although if you ask me your not confused at all, unless it's a ketchup thing that has you confused:D )

---

### Post by confused57 on 2006-05-22
[QUOTE=catlett][COLOR="Red"]Victory!!!!!! [/COLOR]I just took a little more time to understand what he was instructing me to do. Then I realised I had more things in my /boot/grub than him.
Basically what he instructed is to format a floppy to ext2. Then he gave a command to make a filesystem on it. Mount the floppy to /media/floppy0. Then a command to make a directory /media/floppy0/boot/grub. Finally, copy over everything in /boot/grub to /media/floppy/boot/grub.
My error was I was only cp-ing the 2 files he listed when I actually had 11 things. So I just cp-ed the 11 things and PRESTO I just booted in with my grub floppy. 
Thank you confused57. (although if you ask me your not confused at all, unless it's a ketchup thing that has you confused:D )[/QUOTE]

Great you got it to work, with minimal help from me... out of curiosity, what were the other things you had to cp and how did you determine what they were?

I meant to make my user name confucius57, but mistyped it...seriously, I was pretty lost(and confused) when I first started...my understanding of Linux is starting to come together, piece by piece...still a lot to learn, believe I manage to learn something new almost every day.   I'm think you, like me,  enjoy helping new forum members just starting, because it wasn't that long ago that I installed Ubuntu and it was "now what"?  I remember asking questions in the forum and being told to edit a certain file, but not how to edit the file...or enter a list of 3 or 4 commands, do I enter them one-by-one or all at the same time?,etc....sorry, I'm digressing .  I just want to give back, with my limited knowledge, for all the help I've received here.

---

### Post by ajgreeny on 2006-05-22
[QUOTE=catlett]I can't get grub to install to a floppy. Were you talking about installing from the terminal? Or were you talking about a system install? I mounted a floppy. I put (fd0) /dev/fd0 in the device map (because I kept getting an error about no bios drive). When I ran grub-install it said it installed (after a dialogue about an xfs bug). When I open the floppy it is empty? What am I doing wrong? I have always wanted a floppy version of grub. I have had my share of error 17's and 21's.[/QUOTE]
Hi catlett.
Yes I was talking about using grub-install /dev/fd0 from the terminal, or kde's konsole, it doesn't matter.  You can ignore the message about the xfs bug as the terminal says, and don't worry about there seeming to be nothing on the floppy, because that is exactly what I also get, though the system will still boot from the floppy.  No, I don't understand why either, but it works.  Just try the floppy you made and see.
Does anybody know why there is nothing showing on the floppy when you look in nautilus or konqueror, as it frightened me first time I looked.  Thankfully it doesn't stop the disk being bootable and starting up grub, but I'd just like to know.

---

### Post by catlett on 2006-05-22
Hello again,
I think we are alot alike confucious:D  That is exactly how I feel. I was like, now what?? I try to help not because I think I'm smart but because everyone was talking over my head before so I started replying because I thought I could explain the things  the more experienced members assumed the new guy knew. Funny you mention about entering commands one at a time or not. If you want a laugh check out one of my first posts [http://www.ubuntuforums.org/showthread.php?t=146889](http://www.ubuntuforums.org/showthread.php?t=146889)
Anyways the grub-install (fd0,0) can up with a "no file system found". When I followed your link the directions made a file system on the floppy.
> wallijonn  	How to create a bootable GRUB floppy:

If needed:
Start a Root Terminal
Code:

sudo gedit /etc/fstab /dev/fd0 /media/floppy0 ext2,vfat rw,user,noauto 0 0


{exit gedit / save}
{reboot}

-----------------------------------------------------------------------------------------------------

Insert a blank floppy
Applications -> System Tools -> Floppy Formatter
Choose "Linux Native (ext2)"

Start a Root Terminal
Code:

mkfs /dev/fd0
 mount /media/floppy0 
mkdir -p /media/floppy0/boot/grub
 cp /boot/grub/stage1 /boot/grub/stage2 /boot/grub/menu.lst /media/floppy0/boot/grub 
umount /media/floppy0


{reboot & set BIOS to boot from floppy first. It should read / boot from floppy}

I figured I'd post his directions here just in case people were wondering.The issue I had was I had more things in my grub folder than he copied over in his example. So when I ran it like that it failed. So I went back followed the same steps EXCEPT when it came to cp things to the floppy. I just opened up my grub folder in nautilus so I could see all the files I had and I individually ran a cp comand to copy each file into the floppy. It worked. What I realised after was the floppy looked exactlky like /boot/grub, because I had both opened in nautilus.
That's when I figured out it was about making a filesystem on the floppy, making a directory /boot/grub in the floppy because it is going to mirror the /boot/grub on your system (but it is actually /media/floppy0/boot/grub when you give the command because it is in the floppy. Then copy over all the files you have in your grub folder. If your bios are set to boot to floppy first it will boot to the floppy and grub is there like it would be if it was booting to your hard drive and running off of /boot/grub.
My next experiment is to use ajgreeny's command grub-install (fd0,0) but make the filesystem on the floppy first. Just got late last night.
If by any chance someone comes along and is trying to folow this thread to install grub to a floppy. The instructions above are from the thread linked to by confucious [http://www.ubuntuforums.org/showthread.php?t=6195](http://www.ubuntuforums.org/showthread.php?t=6195)
If you are confused by the root terminal there are 2 things you can do. 1st to get a root terminal in ubuntu ```
sudo su
``` Or just put ```
sudo
``` Before all the commands he outlines in the root terminal.

Thanks for all the help guys. I know I'll be seeing you in another thread confucious.[COLOR="Red"] "Virtue is not left to stand alone. He who practices it will have neighbors."[/COLOR] Confucious 551-479 BC

---

