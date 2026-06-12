---
title: "How do I format a USB flash drive?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Antarctica on 2006-11-09
Hola!  Yesterday I bought a USB flash drive.  It's the Cruzer Micro 512 MB, and I love it!  It has a retractable USB connector so that it doesn't get damaged!  Anyway, it came with some crap on it that's used for Windows.  So, I took it off there, but it didn't have 512 MB free space like it should've.  Instead, it has 483.6 MB free and I'd like to know how to format it.  I've looked online but I cannot seem to find a decent tutorial.  Most of the tutorials I read are for formatting floppy disks.  Can somebody show me how to format my flash drive?  Thanks.

---

### Post by bodhi.zazen on 2006-11-09
> **Antarctica said:**
> Hola!  Yesterday I bought a USB flash drive.  It's the Cruzer Micro 512 MB, and I love it!  It has a retractable USB connector so that it doesn't get damaged!  Anyway, it came with some crap on it that's used for Windows.  So, I took it off there, but it didn't have 512 MB free space like it should've.  Instead, it has 483.6 MB free and I'd like to know how to format it.  I've looked online but I cannot seem to find a decent tutorial.  Most of the tutorials I read are for formatting floppy disks.  Can somebody show me how to format my flash drive?  Thanks.

See this [link](http://ubuntuforums.org/showthread.php?t=282018)

Note: some of your space on the drive will be taken up by the journaling system. I believe ext2 may take the smallest space, but I am not sure.

---

### Post by matthew on 2006-11-09
One of the easiest ways to do it is to install gparted. Once it is installed you can run it from System->Administration->Gnome Partition Editor.

Be very careful so you don't format your hard drive instead.

Plug in the thumb drive. Once it has mounted start gparted as described and enter your password when requested.

At the upper right of the gparted window is a drop-down menu that will show all the storage devices attached to your computer. Select the one corresponding to your thumbdrive (carefully check the size, etc.). It will likely be called /dev/sda or something similar.

Right click on the graphic display of the drive (top, just under the icons/actions like new, delete, etc) and unmount the drive.

Right click again and choose "format to" and the filesystem type you want to use. 

If its a smaller drive I tend to use Fat16 and for larger ones Fat32 just because I often use them with Windows or Mac machines and the drives can be read by them using these filesystem types whereas they can't generally read ext2/3.

---

### Post by Antarctica on 2006-11-09
> **matthew said:**
> One of the easiest ways to do it is to install gparted. Once it is installed you can run it from System->Administration->Gnome Partition Editor.

Be very careful so you don't format your hard drive instead.

Plug in the thumb drive. Once it has mounted start gparted as described and enter your password when requested.

At the upper right of the gparted window is a drop-down menu that will show all the storage devices attached to your computer. Select the one corresponding to your thumbdrive (carefully check the size, etc.). It will likely be called /dev/sda or something similar.

Right click on the graphic display of the drive (top, just under the icons/actions like new, delete, etc) and unmount the drive.

Right click again and choose "format to" and the filesystem type you want to use. 

If its a smaller drive I tend to use Fat16 and for larger ones Fat32 just because I often use them with Windows or Mac machines and the drives can be read by them using these filesystem types whereas they can't generally read ext2/3.

Hey it turns out that I don't have GNOME Partition Editor in System, Administration.  How can I get it installed on Dapper Drake?  Much thanks. :)

---

### Post by Antarctica on 2006-11-09
Never mind my last post.  I found out how to install GNOME Partition Editor.  Duh, do apt-get install gparted.  I feel stupid now. :)

---

### Post by taurus on 2006-11-09
Open a terminal, Applications -> Accessories -> Terminal, and run

```

sudo aptitude update
sudo aptitude install gparted

```

---

### Post by ildfroe on 2006-11-09
In a terminal:
> sudo apt-get install gparted

---

### Post by ildfroe on 2006-11-09
Ok, you should know how by now :-)

---

### Post by matthew on 2006-11-09
> **Antarctica said:**
> Never mind my last post.  I found out how to install GNOME Partition Editor.  Duh, do apt-get install gparted.  I feel stupid now. :)Ahh, don't feel bad. I could/should have mentioned that as well. I'm glad you figured it out. Hope the formatting process goes easily for you.

---

### Post by Antarctica on 2006-11-09
Hey it worked!  Thanks. :)  I looked at it, and I had a question.  What would the advantages be of having an ext3 partition on the flash drive opposed to fat16/fat32?  And, one more question... if I were to format my flash drive to linux-swap, is it possible that I could use the drive as extra RAM (or basically a swap file) when using the Ubuntu Live CD?  I think it would be nice to know that I have 512 MB extra RAM at my disposal when using the live CD.  Thanks again for your answers.

---

### Post by kc8hr on 2006-11-09
The only advantage to formatting your flash drive in MS/DOS or FAT32 is that you will be able to access your data on any Windows machine. Format it as EXT2/3 and you will only be able to access on a Linux box.

---

### Post by bodhi.zazen on 2006-11-09
I agree FAT is easier for shared drives. Some people report they are able to access ext2 and ext3 from windows:

[fs-driver](http://www.fs-driver.org/faq.html)

---

### Post by Antarctica on 2006-11-09
What about swap space?  Could I use my flash drive as swap on a live CD if I formatted the drive as linux-swap?

---

### Post by matthew on 2006-11-09
> **Antarctica said:**
> What about swap space?  Could I use my flash drive as swap on a live CD if I formatted the drive as linux-swap?Hmm. I suppose it could work. You would have to edit your fstab file so the OS would know where the swap was located. I think it would be slower though and in my experience flash memory doesn't last as long as hard drive space or ram. Flash ram does wear out.

Bottom line: I think it could work, but I wouldn't personally recommend it. It might be fun for an experiment though...just to see if you can do it.

---

### Post by Antarctica on 2006-11-10
Cool, thanks.  I didn't know that flash drives didn't last as long as RAM or hard drives.

---

### Post by Endow on 2006-11-14
Regardless of the type of format I try to do I always get an error message.The error message simply says an error ocurred...

---

### Post by ReaderRat on 2006-11-14
You are confusing physical (512 megabyte) storage memory with RAM (Random Access Memory), the memory you load and run programs in. Fat 16 and Fat32 can be read and written to from both Windoze and Ubuntu. ext3 cannot.

---

### Post by Endow on 2006-11-16
Can anyone help me : I have a Creative 256MB MuVo TX FM mp3 player and I tried formatting it with gparted but I can't.Regardless of the type of format I choose I get an error message (which doesn't actually specify what was the problem).And now whenever I turn my mp3 player I get a "Filesystem Error" message which means I can't use as of now.

Any suggestions?

---

### Post by tedrogers on 2006-11-17
I have a problem where once I've formatted the USB drive using gparted to ext3....I cannot write to the drive. It's like I only have read permissions?

Any ideas?

---

### Post by taurus on 2006-11-17
You are talking about permissions then.  You need to change it to 777 like

```
sudo chmod -R 777 /where_you_mount_it
```

---

### Post by tedrogers on 2006-11-17
Lovely...thank you so much...still getting my head round all of this.

It does make 'spin-dows' seem more simple (but less secure - hence the problems) when it come to these sort of things. :)

---

### Post by CujoQuarrel on 2006-11-17
I've been trying to get a script together that can be dropped in the scripts folder so that the right click on the USB device would get you a format option. Cut the stuff below the line into a text file , set the execution bit and plop it in your Nautilus_Scripts foler (easiest way is to right click on a drive. Go to scripts and select open folder to get the right folder)

Here's where I'm at so far for one that formats to 
FAT32.

It unmounts and formats right now. At this point you have to unplug and replug the USB device since I haven't figured out a way to remount it from the script.


------------------- START SCRIPT ------------------
#!/bin/bash
device=$(grep $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS /etc/mtab | awk '{print $1}')
gksudo umount $device
sudo mkdosfs -F 32 $device
------------------- END SCRIPT ------------------

---

### Post by tedrogers on 2006-11-17
This is a great idea...but a bit 'heavy' for me right now. :-k 

I have trouble negotiating folders in bash, so you have an idea at the level I'm at right now. Once I get into permissions that stuff like that I'm pretty much screwed without ubuntuforums!

But I'm sure someone will find this useful and you should definitely keep up the good work.

---

### Post by CujoQuarrel on 2006-11-17
Once you put the file in the right place it should just "work" (I hope) if you have the mkdosfs command. 

I'm hoping that someone will give me a hint on how to do the remount. Once I unmount I don't know where to get the information to mount since on my system at  least the act of putting the USB card into my card reader puts the entries into  /etc/mtab for me.

---

### Post by tedrogers on 2006-11-18
To be honest, I don't know why this sort of auto-unmount, format and remount functionality isn't already in edgy....isn't it supposed to be 'bleeding edge' and this sort of action is something a lot of people would want to do...more so than formatting a floppy I would say.

I hope someone can help you out here CujoQuarrel.

Thanks.

---

### Post by bodhi.zazen on 2006-11-18
> ------------------- START SCRIPT ------------------
#!/bin/bash
device=$(grep $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS /etc/mtab | awk '{print $1}')
gksudo umount $device
sudo mkdosfs -F 32 $device
------------------- END SCRIPT ------------------

Try:

sudo mount $device

I will look at this script later (as time allows) an add formatting and label options.

---

### Post by tedrogers on 2006-11-18
Looks like you got the assistance you were looking for CujoQuarrel! :cool:

---

### Post by bodhi.zazen on 2006-11-19
I wrote a short script that will do this for you.

I posted it in the "how-to" section although I do not know how long it will take for the moderators to review....

I will post a link here with an update.....

8)

---

### Post by moshuptrail on 2006-11-19
Wait a sec...
I think there's a much simpler way.
I'm using Dapper and when I click on System / Administration / Disks
I get a screen called "Disks Manager", click on the "Partitions" tab.

Here I see my USB drive listed as a "hard drive" with one partition.
There is a button that says, Format, but it's greyed out.
If I click the "Disable" button the Format button lights up. (I assume this unmounts it)

I haven't gone farther than that yet..  I didn't see in the thread if you guys had run across this...

---

### Post by moshuptrail on 2006-11-19
One very important thing you should know about USB drives and Linux:

Don't just pop 'em out!  It's more like a Mac.  

You should always right-click on the icon on your desktop and select "Eject".  This will write any buffered data to the USB drive.  I have learned the hard way that Linux does indeed buffer data and it may not get physically written to the USB drive for some time.

---

### Post by tedrogers on 2006-11-19
Yes of course you are exactly right.

Mac > UNIX based
Ubuntu > LINUX (a UNIX type OS)

'Win-blows' also complains if you rip out USB drives, depending on whether they're optimised for access speed or connectivity.

I always optimise for speed, so I have to unmount/disconnect/eject on 'win-blows' too.

---

### Post by bodhi.zazen on 2006-11-19
I enjoyed writing this script and posted it in the "how to" section to share with others.

Let me know what you think....
[indent]Be careful not to lose data ![/indent]

[How to format removable devices](http://ubuntuforums.org/showthread.php?p=1778405#post1778405)

---

### Post by Endow on 2006-11-19
Can no one help me?I'm pretty desperate here...I have even formatted the flash drive in WindowsXP but to no avail...I get the same filesystem error message :'(](*,)

---

### Post by bodhi.zazen on 2006-11-19
> **Endow said:**
> Can no one help me?I'm pretty desperate here...I have even formatted the flash drive in WindowsXP but to no avail...I get the same filesystem error message :'(](*,)

Perhaps the problem is with the device (hardware) then ?

Perhaps someone at Creative may have an answer.

---

### Post by tedrogers on 2006-11-20
Sounds like hardware failure to me as well...if it won't format in XP then I strongly suspect this.

Have you got access to a Mac with OSX...try it there and if it still doesn't work then I think it's probably knackered!

---

### Post by UberIcarus on 2006-11-26
I could use some help, I have the SD Cruzer Micro 2gb as well, and when I plugged it in I just moved all the files on it into trash, and then perma deleted the trash.

But the "CD" keeps popping back up every time I plug it in, so there's still something on it. I open up gparted and it's got a filesystem lock on it.

I tried sudo chmod -R 777 /dev/sda1 and also sudo chmod -R 777 /media/usbdisk with no change in the filesystem lock.

And reformatting in windows isn't an option now...because windows only sees it as a CD, no USB drive pops up.

Any suggestions?

---

### Post by UberIcarus on 2006-11-26
bump.

---

### Post by tedrogers on 2006-11-26
Try doing:

```
sudo chown -R user_name:user_name <path>
```

So, for example:

```
sudo chown -R mrbungle:mrbungle /dev/sda1
```

Or:

```
sudo chown -R root:root /media/usbdisk
```

You should then be able to delete the files manually, forever!

---

### Post by UberIcarus on 2006-11-26
=( didn't work, the CD still comes up, although I should point out that the only output I get from mkdosfs is the version number.

---

### Post by tedrogers on 2006-11-26
Sorry then....I'm stumped.

Hope someone else can help you out.

Maybe try on a Mac? If you can get hold of one.

---

### Post by bodhi.zazen on 2006-11-26
> **UberIcarus said:**
> I could use some help, I have the SD Cruzer Micro 2gb as well, and when I plugged it in I just moved all the files on it into trash, and then perma deleted the trash.

But the "CD" keeps popping back up every time I plug it in, so there's still something on it. I open up gparted and it's got a filesystem lock on it.

I tried sudo chmod -R 777 /dev/sda1 and also sudo chmod -R 777 /media/usbdisk with no change in the filesystem lock.

And reformatting in windows isn't an option now...because windows only sees it as a CD, no USB drive pops up.

Any suggestions?

First, what version of Ubuntu and kernel are you running? i386, i686, 64 bit ??

I think the problem you are having is with the U3 software on the disk itself. [See this thread](http://www.ubuntuforums.org/showthread.php?t=207683)

Also, I have seen these drives "forged". The forged drive works for a very short time, if at all. It comes with packaging that looks very legitimate and I have seen them sold on line and on EBay.

Contact ScanDisk to confirm the serial number of your drive....

---

### Post by raul_ on 2006-12-11
I don't understand. I do "unmount" and then "format", choose the fs type and then the pen "magically" mounts itself and it won't let me format it because it's mounted =\

---

### Post by bodhi.zazen on 2006-12-11
> **raul_ said:**
> I don't understand. I do "unmount" and then "format", choose the fs type and then the pen "magically" mounts itself and it won't let me format it because it's mounted =\

could you giv more details? Are you suing my script? Or are you formating from the CLI?

If the disk "magically" mounts is it then formatted? Is the disk ro ? Type of disk ?

---

### Post by raul_ on 2006-12-11
Lol. I'm sorry. It's not your script. I should've quoted. That happend with gparted. I click "unmount" and then "format to", choose the format and then the drive auto-mounts itself again, a window pops up with the contents (it's what my ubuntu does when a new device is mounted) and gparted cannot continue because the device is mounted.

---

### Post by bodhi.zazen on 2006-12-11
> **raul_ said:**
> Lol. I'm sorry. It's not your script. I should've quoted. That happend with gparted. I click "unmount" and then "format to", choose the format and then the drive auto-mounts itself again, a window pops up with the contents (it's what my ubuntu does when a new device is mounted) and gparted cannot continue because the device is mounted.

What I have done in the past is to unmount the device, then start gparted (both in Ubuntu and the gparted live CD).

If you like, try my script it is full featured and fully funtional :)

---

### Post by raul_ on 2006-12-11
```

bodhi's format script
Erro: não foi possivel determinar o real caminho do dispositivo: Arquivo ou diretório inexistente
umount: /media/FLIP: não encontrado
Linux: No such file or directory
Erro: o dispositivo /dev/sdb1 já está montado em /media/FLIP 256

```

Basically, first it couldn't umount because it didn't find the device (it was lister as FLIP, but its FLIP 256). Then it tried to format the correct device, but because the first step wasn't done, this one fails

My device name is "FLIP 256" so it's normal it wouldn't find :rolleyes:
How can i change the name of my pen in Ubuntu? I tried to right click inside the folder and change it (as root) but it didn't work

---

### Post by dmartinsca on 2006-12-11
nevermind..

---

### Post by bodhi.zazen on 2006-12-11
> **raul_ said:**
> ```

bodhi's format script
Erro: não foi possivel determinar o real caminho do dispositivo: Arquivo ou diretório inexistente
umount: /media/FLIP: não encontrado
Linux: No such file or directory
Erro: o dispositivo /dev/sdb1 já está montado em /media/FLIP 256

```

Basically, first it couldn't umount because it didn't find the device (it was lister as FLIP, but its FLIP 256). Then it tried to format the correct device, but because the first step wasn't done, this one fails

My device name is "FLIP 256" so it's normal it wouldn't find :rolleyes:
How can i change the name of my pen in Ubuntu? I tried to right click inside the folder and change it (as root) but it didn't work

Hey, sorry about that :redface:

What file system (FAT, ext3, ??) is currently on the device ?

---

### Post by raul_ on 2006-12-11
FAT

Ironically (or not) i really don't want to format to change the filesystem type, but i already have DSL in my pen and i want to change to Feather Linux, and i just wanted to wipe all of it,instead of manually deleting the files, but because it didn't work, now i got curious :)

---

### Post by bodhi.zazen on 2006-12-11
_FAT (Windows partitions)_:

Use mtools to label a FAT partition:

[list=number][*]Install mtools:```
sudo aptitude install mtools
```

[*]Copy the mtools configuration file to ~:```
cp /etc/mtools.conf ~/.mtoolsrc
```
_Note_: ~ is shorthand for /home/user_name.


[*]Mount your flash drive.


[*]Edit ~/.mtoolsrc:```
gedit ~/.mtoolsrc
```

[*]Add these lines to the end of ~/.mtoolsrc:
> drive i: file="<device>"
mtools_skip_check=1
Where <device> is the device assigned to your mounted USB device/flash drive (ie sda1, sdb1, ...).
_**Note_: You can do this from the command line:**```
echo 'drive i: file="<device>"' >> ~/.mtoolsrc
echo mtools_skip_check=1 >> ~/.mtoolsrc
```[indent]Although you will need to edit ~/.mtoolsrc for each new device if the device assignment changes.[/indent]


_**Example_: = drive i: file="/dev/sda1"**


[*]Change to drive i:```
mcd i:
```

[*]Check the current label:```
mlabel -s i:
```

[*]Change the current label:```
sudo mlabel -s i:DATA
```
[indent]_Note_: mlabel USES ALL CAPS.[/indent]


[*]Add an entry to fstab:> LABEL=DATA <mount_point> vfat defaults 0 0
_Note_: You can also mount the usb device with:```
mount LABEL=<label>
```[/list]

---

### Post by raul_ on 2006-12-11
```

raul@raul:~$ mcd i:
init I: non DOS media
Cannot initialize 'I:'

```

oops

---

### Post by bodhi.zazen on 2006-12-11
post the contents of ~/.mtoolsrc and

sudo fdisk -l

---

### Post by raul_ on 2006-12-11
```

raul@raul:~$ mount LABEL=DATA
mount: não foi possível localizar LABEL=DATA em /etc/fstab ou /etc/mtab
raul@raul:~$ 

```

"not possible to locate blablabl"

and here is my fstab:
```

blablablabla
blablabla
LABEL=DATA /media/DATA vfat defaults 0 0 

```

and my mlabel:
```

raul@raul:~$ sudo mlabel -s i:
 Volume label is DATA  

```

i got past that previous error

EDIT: i'm so stupid..ur script already worked with the label DATA :) thnx

---

### Post by bodhi.zazen on 2006-12-11
> **raul_ said:**
> ```

raul@raul:~$ mount LABEL=DATA
mount: não foi possível localizar LABEL=DATA em /etc/fstab ou /etc/mtab
raul@raul:~$ 

```

"not possible to locate blablabl"

and here is my fstab:
```

blablablabla
blablabla
LABEL=DATA /media/DATA vfat defaults 0 0 

```

and my mlabel:
```

raul@raul:~$ sudo mlabel -s i:
 Volume label is DATA  

```

i got past that previous error

EDIT: i'm so stupid..ur script already worked with the label DATA :) thnx

LOL raul_ :lol:

What version of Ubuntu are you running ?

Yes/ label no longer works in edgy :(

Solution:

use

```
/dev/disk/by-label/DATA /media/DATA vfat users,umask=000 0 0
```

in fstab and then:

```
mount /media/DATA
``` to mount.....

To list your devices by label:```
ls /dev/disk/by-label -l
```

---

### Post by antw on 2007-01-25
> **raul_ said:**
> I don't understand. I do "unmount" and then "format", choose the fs type and then the pen "magically" mounts itself and it won't let me format it because it's mounted =\

I have the same problem in edgy. I unmount in Gparted, select format and it immediately mounts and brings up nautilus. The format fails and I am back to square one.

I have since used the terminal and used mkdosfs -F32 -v /dev/sdb1 while the usbdisk is unmounted and all works fine. I have used this same command for mp3 players as well.

hope this helps someone

---

### Post by davebgimp on 2007-03-01
> **moshuptrail said:**
> One very important thing you should know about USB drives and Linux:

Don't just pop 'em out!  It's more like a Mac.  

You should always right-click on the icon on your desktop and select "Eject".  This will write any buffered data to the USB drive.  I have learned the hard way that Linux does indeed buffer data and it may not get physically written to the USB drive for some time.

Oh yeah...you want to wait anywhere from 30 seconds to a minute sometimes. Found that one out the hard way, more than once till I figured out what was going on. Some kind of notification that all writing is finished and the device to is safe to remove would be nice.

---

