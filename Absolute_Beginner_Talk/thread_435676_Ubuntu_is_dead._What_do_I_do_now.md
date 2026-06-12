---
title: "Ubuntu is dead. What do I do now?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by sahil1 on 2007-05-07
Hi.

My name is Sahil and I am from India. Recently I had downloaded, burned, and installed Ubuntu Fiesty Fawn and everything was fine until today. I plugged in a USB stick but I couldn't delete anything from it or add anything cuz the error was it was a read-only (which i know it wasnt cuz it worked with XP fine) i tried all my three ports, and the same problem. And there is no "switch" on the actual stick. 


NOW HERE IS WHERE IT GETS FRUSTRATING

Someone told me to open up my terminal and type fsck, and like a newbie I DID! And nothing happened, the problem was still there. Then i restarted my computer and BAM everything is messed up. It says that apt-get is not installed and eve "install" is not installed and tells me to type "apt-get install apt" but it doesn't work. Nothing works. I need to get my system back up and running. I am using the Live CD now. The recovery mode also doesn't work.
Someone PLEASE help a newbie and a Linux enthusiast to get my system working,

Desperately seeking help.
Sahil

[email]sahilbajaj1@gmail.com[/email]

PLEASE!:(

---

### Post by AAM on 2007-05-07
sahil1,

I can't tell what the problem is .... BUT some USBs you need to open up as admin. In this case where you are told it is read-only, open a terminal and type
sudo nautilus
The file manager will open up in admin mode. You then go to the USB anjd you should be able to set its permissions to allow everyone to read and write (right click on the icon and go to Properties | Permissions.
If that doesn't work, copy all the files off and reformat while in linux with permissions set to everyone. Then put the files back.
Unless someone has some good advice to fix the problem, re-install! That is one of the beauties of the liveCD - I can't tell you how many re-installs I have done to 'fix' problems I have made. It is all learning!

---

### Post by matburton on 2007-05-07
Wow!

Sounds like you have some severe issues. I'd back-up your data and do a format and reinstall.
What is your usb stick formatted with? FAT32 I guess?
It was probably nothing more than a permissions problem originally?

Hope that helps ;)

---

### Post by dptxp on 2007-05-07
REINSTALL.

Keep your data in separate partitions so that in initial stages you can reinstall n times when you create a mess.

Normally USB sticks work fine.

---

### Post by Swankyman on 2007-05-07
Hi,

Bad luck there,

Right first of all the usb been read only ive seen a couple of times but not for a long time. I just pulled of the usb stick and put it back in a few times and it would work. No idea why

Anyway

When you type all these commands and they don't work can you copy us the errors it spits out

Did you type sudo in front any of these commands because they wont do anything unless you have administratior powers

Maybe when you fsck you tried to repair all harddisks you had linux on but where using thus killed them. only two things to do that I know. try to repair the disk using the live cd or reinstall

1) using the terminal on the live cd do another fsck but make sure the the harddrive partitions are not mounted, reboot and see if it mended the problem or 

2) Reinstall using the live cd (you can copy all stuff from your home folder using the live cd onto the usb stick before doing it):( :( :| 

rich

---

### Post by sahil1 on 2007-05-07
Hi.

Thanks for that. I have the LiveCD and I don't mind re-installing as it is the easiest method. However, there a .odt and .doc file in my home folder that are vital to me. It is my Resume. Can somone please tell me detailed instructions on how to copy that file to a USB stick or how to email it to myself ?????, or just any way to get that file, i will be indebted to them forever.

Thanks to all the people who are trying to help me, it is very much appreciated as I don't know what to do.

Thanks,
Sahil

---

### Post by lapsey on 2007-05-07
You can run the LiveCD, and using 'mount' you can get the files from your drive onto something else, like the internet. However the LiveCD should mount it automatically anyway. (Sorry I have no detailed instructions for this)


In case this happens to you again, I always recommend making a separate partition for /home/, which is where all your personal files and settings are kept. When reinstalling you can tell ubuntu not to format it but to use it as it is.

---

### Post by Wiebelhaus on 2007-05-07
you can back up your data while in the live cd enviroment.

[http://www.cyberciti.biz/tips/ubuntu-linux-live-cd-save-data-desktop-information-on-usb-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-live-cd-save-data-desktop-information-on-usb-device.html)

After installation run [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") read/write ntfs/fat32 script and ntfs3 (sudo apt-get install ntfs-3g)

---

### Post by sailor2001 on 2007-05-07
If you have a web address ie yahoo or gmail... send imortant files to yourself there.Gmail has almost 3g space which is plenty of space for personal files.

---

### Post by Malta paul on 2007-05-07
Hi,
I would boot from your live CD and see if the files you need are in view. If so put in your usb pen-drive which should mount itself. then copy your files over.Right click the mouse and click eject before  removing  your pen drive. Its a good idea to install Ubuntu again with a clean format.
 Hope this is of some help, if you do still have problems after this, ask again :)

---

