---
title: "Writing on Windows partition...HELP!"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by asimmittal on 2007-12-26
Hey all,

I know this topic might be redundant and believe me, I've read all the previous posts before writing this one.

I am a newbie... a day old. I have Ubuntu Linux. My fstab looks like this :  

____________________________________________________________________
[COLOR="Navy"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ba98311e-b51c-4ecf-bab7-e01d7449ec32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7456-EC6C  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=26202EBE202E94B9 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=5C803B3E803B1DC8 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=fb67d22e-a183-4e1d-912e-aacc74491564 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]

_______________________________________________________________________

I read up on fstab, and can make some sense out of what is displayed in the file. I went to the ntfs-3g website... but they have the driver listed for lots of operating systems except ubuntu (the name is there in the list but there is no hyperlink).

What is it I need to do to be able to write into the windows partitions??

Is FAT32 compatible with linux?? if i convert my ntfs to FAT32, will i be able to write and read on linux?

Thanks.

---

### Post by lisati on 2007-12-26
The good news is that it is possible to use NTFS with Ubuntu......(brief pause while I look it up) ..... 

You might want to install the NTFS configuration tool. From the "Add/Remove Programs" menu you can search for "NTFS" in "All available applications", and if it appears, check the box and click "OK" 

Let us know how you get on.

Edit: the "add/remove programs" menu can be found on the "Applications" menu

---

### Post by rahimveron on 2007-12-26
Install ntfs-3g and ntfs-config from Synaptic Package Manager (Systems>Administration>Synaptic) It will ask for root password (enter your password when prompted).
After install start NTFS from Start>Systems Tool>NTFS Configuration Tool ad enable write access to Internal and External drives. Now you can write to NTFS partitions.
Yes FAT is compatible with Ubuntu.

BTW ,Asim, Welcome To Ubuntuforums :) Where are you from?

---

### Post by asimmittal on 2007-12-26
Hey im from Bangalore, India. Oh i tried to open the Synaptic package manager... it said "another package manager is running. wait for it to finish first" ??!?!? what was that. Is there a way i can see what processes and threads are running (like task manager in Windows)

Oh and I looked up the ntfs-3g packages that you suggested... which one should i use... first of all, what are "fiesty, hardy, edgy...?" and each has an ntfs-3g. Which one do i use? and the download is available for "amd64, i386 and powerPC". I use a Core2 Duo.... now what do I choose?

---

### Post by rahimveron on 2007-12-26
Ya from Start>System>Adminstration>System Monitor. CLose ADD/Remove window and start Synaptic.
Close any update manager window or are you installing something from Terminal? Only one package manager would be open at one time. SO close all of them and start Synaptic.
There is another method to install appz from Terminal. Try the first one then will tell you about Terminal stuff Are you comfortable with command-line?

---

### Post by chewearn on 2007-12-26
> **asimmittal said:**
> Hey im from Bangalore, India. Oh i tried to open the Synaptic package manager... it said "another package manager is running. wait for it to finish first" ??!?!? what was that. Is there a way i can see what processes and threads are running (like task manager in Windows)
Using Gnome GUI:
Rightclick on an empty area of the gnome panel, select "Add to Panel"; a window will pop-up, look for System Monitor and click Add.  You will get an applet in the panel.  If you click on the panel, the Process Monitor will pop-up.

Or using CLI:
Open a terminal, type:
```
top
```

There is also a better program in CLI, call "htop".
```
sudo aptitude install htop
```
Then in terminal:
```
htop
```

---

### Post by rahimveron on 2007-12-26
Which version of Ubuntu are you using? Edgy, Feisty & Gutsy, Hardy are different versions of Ubuntu. The latest is Ubuntu 7.10 "Gutsy Gibbon". 
You have to install through Synaptic (not from any site) since you are a beginner, its very easy. Open Synaptic and search for ntfs and select ntfs-3g and ntfs-config from the results and then click apply. It will download those and install automatically. hen fire it up as i mentioned above.

To know the version for you open terminal and type ```
lsb_release -a 
``` and see the release number
Alternate: Navigate to System>About Ubuntu

In the second Paragraph down, after the Contents it tells you the version number.

---

### Post by asimmittal on 2007-12-26
yes my man, i did exactly what you said.... opened the manager... clicked search. It popped up a window reading "search name & look in" .  Now i typed "ntfs-3g" and i dont really know what to look in so to speak... but it doesnt find anything

---

### Post by rahimveron on 2007-12-26
Search for ntfs and it will show both ntfs-3g & ntfs-config. 
Make sure all repositories are selected in Software Sources. Open Synaptic and select Settings>Repositories and click on main, universe, restricted and multiverse. And then reload Synaptic. Now search for ntfs (not ntfs-3g) to get both packages.

---

### Post by asimmittal on 2007-12-26
yea i did just that over again... it shows only "ntfsprogs" in the search.... no sign of 3g and config. I even installed ntfsprogs but to no avail. What now?

---

### Post by rahimveron on 2007-12-26
Hold On. Its very important.
Which version of ubuntu are you using?
Type ```
 lsb_release -a 
``` in Terminal to get your version.

---

