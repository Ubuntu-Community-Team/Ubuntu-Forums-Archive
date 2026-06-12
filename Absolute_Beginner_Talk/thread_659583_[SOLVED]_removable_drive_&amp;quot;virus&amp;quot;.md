---
title: "[SOLVED] removable drive &amp;quot;virus&amp;quot; issues"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by woknblues1 on 2008-01-05
I have recently switched to 7.10.... 

Here in the Philippines, nearly everybody is running illegal copies of windows, and most people use internet cafe's... As a result, nearly everyone has all kinds of trojan horse viruses and .exe files on their removable drives. (one of the reasons I switched was because I got tired of getting other people's viruses on my computer) 

I have some virus infected thumb drives and SD cards, myself, by using a thumbdrive to download documents and files to and from school, etc. 

I notice that viruses on removable devices in my ubuntu OS environment seem to be disregarded. Meaning, they still show up in the infected drive as a particular file, but don't cause any disruption or viral behaviour in my desktop environment.

As I do have a windows machine (technically, my girlfriend's laptop) still running in my house, and other friends and project collaborators who use windows, it seems like I have an opportunity to "cleanse"  removable drives through my ubuntu desktop before we use them in the windows machine, adding a layer of removal/restoration/etc to the process. 

I have tried to trash the various .exe files through ubuntu but it says

"Cannot move "/media/disk/Recycled" to the trash because you do not have permissions to change it or its parent folder"

Anyone have any suggestions?

---

### Post by skymera on 2008-01-05
```
cd /location/of/drive
```

example:

```
cd /media/usb
sudo rm <filename>
```

---

### Post by woknblues1 on 2008-01-05
not entirely sure what to do with the code you sent. copy/paste into terminal? I am on ubuntu for about 48 hours now. :)

---

### Post by thelatinist on 2008-01-05
First of all, welcome to Ubuntu!

Second: probably the easiest way for you to do this, since you're new to Ubuntu, would be to go to a terminal and type

```
gksudo nautilus
```

to open the Nautilus file browser as a super user.  You can then browse to the proper folder on your thumb drive and delete these files.  As a superuser, you should be able to delete the files without trouble.

If you are up for learning about the terminal, then you should follow skymera's suggestion by typing or copy/pasting the commands he listed in the terminal.  You will of course need to replace the path in the cd command with the correct path to your USB drive.

---

### Post by woknblues1 on 2008-01-06
awesome!! I was able to go onto nautilus and remove the file. it did not show up in my trash can. I'll take that as normal?

OK, another question, if I am using skymera's suggestion, and I open the folder using the "ls" function, it gives me the contents using a color coding scheme, that showed all the normal files on the drive in a green color, and the problem file that I had indicated within the "<>" in blue.... at that point, what would I have done?

thanks to both for the great responses and useful info. I love this OS and the community. :popcorn:

-joaquin

---

### Post by Perfect Storm on 2008-01-06
I you deleted them via gksudo they are in /root/.Trash 
Just be very careful when using gksudo nautilus - Too many have accidently deleted files that broken their system.

---

### Post by rkd on 2008-01-06
I'm new to Ubuntu, also, so I may misunderstand things, but I was under the impression that when you deleted a file on a removable drive with nautilus, it was placed into /.trash on the the removable drive. That is a hidden directory, so be sure to set the Nautilus options to show hidden files and directories before trying to find it.

I have read that the Clam open source antivirus program is a pretty good one. That would probably do a better job (and be much easier) than examining the thumb drives manually. It is available to install from the repositories using the Add/Remove choice under the Application menu. Be sure to use the control in the top right of the Add/Remove window to select All Available Applications before you try to search for Clam. I've never used Clam, so I can't tell you anything about how to run it. I hope it has some directions available with the installation package.

Concerning the color codes in the ls listing, I found this explanation in an old thread in the forums:

grey -- regular file (usually a text file) -- In a white background terminal window these filenames will appear black. 

blue -- directory 

green -- executable 

cyan -- symbolic link -- Often referred to as a symlink. 

red -- archive -- If an archive has an executable permission set it will appear green. 

magenta -- graphic -- If a graphic has an executable permission set it will appear green. 

yellow -- block or character device 

brown -- FIFO (named pipe) 

in rare instances, magenta can also signify a socket, and a red background and white blinking text can signify an orphan file -- a symlink (a file that points to another file), to a nonexistent file.

So it seems that blue just means the name is a directory (Windows calls them folders), not that it is a virus or any other kind of problem file.

I know there is some variation in the colors in some Linux distributions, but I don't know what the changes are. If you really need to find out what colors mean, you can look at the output of the command
```
echo $LS_COLORS
```
and look up the code numbers in the description of ISO 6429, but I haven't yet found an exact description of what the letter codes in LS_COLORS mean. Some of them are file extensions, but others seem not to be that. I'm sure the description is somewhere, but as with most things Unix, it isn't very clear to the newcomer where to look for it.

---

