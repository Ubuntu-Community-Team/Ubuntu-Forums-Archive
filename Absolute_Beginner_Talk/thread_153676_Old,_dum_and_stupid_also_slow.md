---
title: "Old, dum and stupid also slow"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Topaz on 2006-04-01
I dumped widows. Loaded 5.04 and after playing around went and updated to Breezy. I have not been able to figure out how to load, acccess any of my harddrives,
floppies or usb drives. I'm well past the speed limit in many states of 65 so please bear with me.

---

### Post by nickle on 2006-04-01
do you want to access your old windows partitions or your drives in general?

If it is the latter any you are using KDE (Kubuntu), then click on the konquerer icon and you should be able to access everything just like in the windows file manager.

---

### Post by red_Marvin on 2006-04-01
**Floppies:**
Put floppy in:
(Gnome menu) Places->Computer
Double-click on "Floppy drive" or whatever it's called.
Now the floppy is "mounted" (That is, you have told the os that there actually is something there)
There should appear an icon on the desktop, either double-click that, or the one you used to mount it, to acces the floppy.
When you've finished right-click on the very same icon and choose "unmount".
Now you can remove the floppy from the floppy drive.

**USB drives**
Normally there should appear an icon on the desktop (and in the "computer" winow mentioned above)
when you connect the usb drive.
If that's not the case you could try to open a terminal window and type
*sudo mount -t vfat /dev/sda1 /media/usbdisk*
and press enter.
If this doesn't work please post the error message and usb memory brand and type (etc.)
Also here you need to unmount it in the same way before disconnecting it.

---

### Post by Topaz on 2006-04-01
Forgot to respond about old windows. Had ubuntu 5.04 repartition harddrive and get rid of windows. I'm straight linux now.

---

### Post by Topaz on 2006-04-01
One of my replies got lost.
Double click on floppy located in computer box with disk in floppy gives ( Unable to mount the selected volume).
Computerbox has
floppy drive
cd-rw/dvd+r drive
external cd-rw drive
external cd-rw dvd + r drive
149.0 gig volume firewire (also only one shown on desktop).
filesystem
Where is my 225gig c drive with breezy on it?

---

### Post by red_Marvin on 2006-04-01
Try
sudo mount -t auto /dev/fd0 /media/floppy0

---

### Post by BoneKracker on 2006-04-01
It sounds like you may need to make or modify some entries in your /etc/fstab file.  That file is what tells Linux about your disks.  For example, what you've said above makes me suspect you lack an entry for your floppy drive.  (This is where those "mount" commands the other guys are asking you to test would eventually go, to make them "built-in".)

Could you copy the contents of that file and paste it into a reply here?

Then we can compare the drives you've talked about (above) to those entries and help you figure out what (if any) modifications to make to the file.

Here's some info about the fstab file:
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

By the way, my dad will be 72 in May, and he's using Ubuntu.

---

### Post by Sef on 2006-04-01
There is a bug in breezy which causes the floppy drive to fail to automatically mounth.  This is fixed in Dapper, which will be out 1 June.

Here's a link to how I fixed it:  (Did work the first time I did it.)

[http://ubuntuforums.org/showthread.php?t=110132&page=2&highlight=floppy+drive]("http://ubuntuforums.org/showthread.php?t=110132&page=2&highlight=floppy+drive")

---

### Post by Topaz on 2006-04-01
:~$ /etc/fstab
bash: /etc/fstab: Permission denied
:~$ sudo mount -t vfat /dev/fd0 /media/floppy
:~$ sudo mkdir /media/floppy
mkdir: cannot create directory `/media/floppy': File exists
:~$ mount /mnt/hda1
mount: can't find /mnt/hda1 in /etc/fstab or /etc/mtab
:~$ mount /mnt/sda1/
mount: can't find /mnt/sda1/ in /etc/fstab or /etc/mtab
:~$ mount /mnt/dev/sda1/
mount: can't find /mnt/dev/sda1/ in /etc/fstab or /etc/mtab

Above are some of the things I tried and the floppy is on my desktop, but nothing
else.

---

### Post by Topaz on 2006-04-01
I did a reboot after my last reply and the floppy is not there, it is gone from the desktop.

---

### Post by ferebee on 2006-04-01
[QUOTE=Topaz]:~$ /etc/fstab
bash: /etc/fstab: Permission denied[/QUOTE]

you could try 
```
 gedit /etc/fstab 
```
to view your fstab file. This will give you read only access, so you can copy and paste the contents.


[QUOTE=Topaz]:~$ mount /mnt/hda1
mount: can't find /mnt/hda1 in /etc/fstab or /etc/mtab[/QUOTE]

Here you might try 
```
mount /dev/hda1
```

You could also try this for your sda1 drive or your floppy (fd0)

---

### Post by Topaz on 2006-04-01
[QUOTE=ferebee]you could try 
```
 gedit /etc/fstab 
```
to view your fstab file. This will give you read only access, so you can copy and paste the contents.

Here you might try 
```
mount /dev/hda1
```

You could also try this for your sda1 drive or your floppy (fd0)[/QUOTE]

[COLOR="Green"]Here is what happened, 
:~$ mount /dev/hda1
mount: according to mtab, /dev/hda1 is already mounted on /
mount failed
:~$ gedit /etc/fstab

What do I do now,
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/scd1       /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

    [/COLOR]

---

### Post by steve.horsley on 2006-04-02
I don't know how relevant it is, but in Dapper, to see my floppy I have to use the command **sudo modprobe floppy** first. Then either **pmount /dev/fd0** or double-click the floppy icon on nautilus/Computer.

---

### Post by belikralj on 2006-04-02
To edit /etc/fstab you must be root as it is a system file so you must use sudo. To access /etc/fstab you must specify what application can open it. Try this command to open fstab "gedit /etc/fstab" (if your using Ubuntu, for KUbuntu I don't know use an editor). To alter it's contents use "sudo gedit /etc/fstab". The command you used ":~$ sudo mount -t vfat /dev/fd0 /media/floppy" actually worked but there are two floppy mount points in /media one is /media/floppy and the other one is /media/floppy0 it is the latter that shows up on the desktop. For automounting show us the contents of the /etc/fstab. NOTE: make a BACKUP of the /etc/fstab BEFORE you change it, and don't change the options for the drives on which your system is on.

check out the (this link is from memory you may want to look for it through google.com) 
[www.tuxfiles.com/linuxhelp/fstab.html](www.tuxfiles.com/linuxhelp/fstab.html)

Hope I helped!  :cool:

---

### Post by belikralj on 2006-04-02
SORRY! Ignore previous post, I didn't see the second page till after I posted.

(it's very late here and I'm sleepy, forgive my mistake)

---

### Post by belikralj on 2006-04-02
The site I gave you in my first post should be usefull in understanding what I'm doing here.

I don't know how Ubuntu labels firewire drives but if the previous posts are correct add this line to your fstab file:
/dev/sda1 /media/usbdisk auto rw,user,sync,auto  0 0

but you may want to check with some one else on that one, I'm not sure about it.

try this to sort out your floppy:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/scd1 /media/cdrom2 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,auto 0 0                         <- change this line

remember to save a backup of the original!

---

### Post by Topaz on 2006-04-02
Hope this helps.
HDA1=my 225gig C:\ harddrive I hope
HDA2=my 60gig D:\harddrive
HDA3=my 6gig G:\harddrive
SDA1=my dvd  E:\dvd writer
SDA2=my USB H:\cd writer
SDA3= my USB I:\DVD writer
         = my floppy drive
NON OF THESE ARE ON MY DESK TOP WHEN I BOOT UP AND ALL ARE PLUGGED IN ON START UP.
140gig firewire is the only thing showing up on my desktop.
 
I tried this before I sent this off'

~$ sudo mount /dev/hda1
mount: /dev/hda1 already mounted or / busy
mount: according to mtab, /dev/hda1 is already mounted on /
~$ sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/ieee1394disk busy
mount: according to mtab, /dev/sda1 is already mounted on /media/ieee1394disk
~$ sudo mount /dev/hda2
mount: can't find /dev/hda2 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/hda3
mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
~$ sudo mount /dev/sda3
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab


Above states HDA1 already mounted (must be hidden on desktop).
SDA1 states it is my firewire (ieee139 is firewire I think).

---

### Post by R3linquish3r on 2006-04-02
Do the following:

```
sudo mount -a
```

That will mount EVERY disk in your fstab file. Also to open your fstab file so you can get the contents for us use the following line.

---

### Post by R3linquish3r on 2006-04-02
Yeah same as the sleepy guy above. I didn't see the second page :)

---

### Post by Topaz on 2006-04-03
None of these codes above have got anything to my desktop and nothing there after reboot. I don't know how I did it but I got my HP G85 printer to print today. I had it print a test page an a e-mail that was sent to me. I did not try and do any of the other things the G85 can do yet. I'm still in the woods and none of the trees are recognizible. I tried to get the virus scan going and keep scanning (no luck).

---

### Post by Topaz on 2006-04-03
Can't get .tar.gz located on desktop to install. In windows using rar double click then
clicked install or setup and that was it.

---

### Post by aysiu on 2006-04-03
[QUOTE=Topaz]Can't get .tar.gz located on desktop to install. In windows using rar double click then
clicked install or setup and that was it.[/QUOTE] .tar.gz files are generally a last resort.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ferebee on 2006-04-03
[QUOTE=Topaz]Hope this helps.
HDA1=my 225gig C:\ harddrive I hope
[/QUOTE]

If this is the drive where you installed Ubuntu then it is mounted at boot.
You don't need to mount it to view files. Just go to Places>Computer or Places>Home Folder. I believe that's why you are getting an error when you try to mount it.
[QUOTE=Topaz]
HDA2=my 60gig D:\harddrive
HDA3=my 6gig G:\harddrive
SDA1=my dvd  E:\dvd writer
SDA2=my USB H:\cd writer
SDA3= my USB I:\DVD writer
         = my floppy drive
[/QUOTE]



According to the fstab you posted earlier, the names you are giving these 
drives are not how Ubuntu is seeing them.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/scd1 /media/cdrom2 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```
NON OF THESE ARE ON MY DESK TOP WHEN I BOOT UP AND ALL ARE PLUGGED IN ON START UP.

According to this hdd, scd0 and scd1 are cd or dvd drives.These don't need to mounted unless you have a cd or dvd in them. When you insert media it should show up on the desktop automatically. If the media is an audio Cd or  Dvd you don't need to mount it in order to play it.  If on the other hand it is a data cd or dvd you would need to mount to view the files.

If you wanted to mount these drives using the command line you would
do this:

```
sudo mount /dev/hdd
``` 
for cdrom0 
```
sudo mount /dev/scd0
```
for cdrom1
```
sudo mount /dev/scd1
```
for cdrom2
```
sudo mount /dev/fd0
```
for your floppy

That said, I'm not sure what is going on with your 60gig and 6 gig hard drives, as they don't seem to be listed in your fstab. 

 
*Edited out bit that wasn't really applicable to Ubuntu*

Try going to System>Preferences>Removable Drives and Media
In the first tab- Storage the first three boxes should be checked.
The last one is more a matter of personal preference.
[ATTACH]7966[/ATTACH]


Is this more what you are aiming for, Topaz?

---

### Post by ComplexNumber on 2006-04-03
[quote=Topaz]I did a reboot after my last reply and the floppy is not there, it is gone from the desktop.[/quote] insert floppy into floppy drive, then go to 'computer' icon  on your desktop and double click the floppy icon. the icon will now appear on your desktop. gnoem automounts, so because it wasn't mounted (ie there was no floppy there), it had nothing to mount, and so no floppy icon appeared on your desktop.

---

### Post by Topaz on 2006-04-03
I have done nothing with the last 2 replies above, but went and took a snapshot.
Does this help us solve some of my problems?

    /home/smileeb/Desktop/Screenshot.png

I did not see png like it is on my desktop, so I went to attach files below in additional
options (hope it works).

---

### Post by Topaz on 2006-04-03
[QUOTE=ComplexNumber]insert floppy into floppy drive, then go to 'computer' icon  on your desktop and double click the floppy icon. the icon will now appear on your desktop. gnoem automounts, so because it wasn't mounted (ie there was no floppy there), it had nothing to mount, and so no floppy icon appeared on your desktop.[/QUOTE]
[COLOR="Green"] I did what you said and got ( Unable to mount the selected volume. 

 Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount)         [/COLOR]

---

### Post by Topaz on 2006-04-04
I am in Knoppix, running live cd. The live cd found all the hardware on my computer. It has 11 icons running down the left side of screen. In one and only task bar at the bottom it has 14 icons of applications. It did not connect my printer even though it sees it as usb. Why is this version of linux so much different than ubuntu and seems closer to windows. Have to leave for doctor's right now to get my oil changed and some new air. Will be back to play and find out more later.

---

### Post by ferebee on 2006-04-04
[QUOTE=Topaz]I am in Knoppix, running live cd. The live cd found all the hardware on my computer. It has 11 icons running down the left side of screen. In one and only task bar at the bottom it has 14 icons of applications. It did not connect my printer even though it sees it as usb. Why is this version of linux so much different than ubuntu and seems closer to windows. Have to leave for doctor's right now to get my oil changed and some new air. Will be back to play and find out more later.[/QUOTE]

Aha!
Now we're getting somewhere, Your Knoppix screenshot tells us exactly what your hard drives are called, and how linux sees them.
While you are in Knoppix try

```
kwrite /etc/fstab
```  in terminal and post it here for us.
With this info we should be able to get your drives recognized.

Knoppix generally has really good hardware detection, and uses KDE as
its desktop environment. KDE looks more like windows than Gnome
does. You can install KDE in Ubuntu, 
This guide tells you how:

[http://doc.gwos.org/index.php/KDE_Installation]("http://doc.gwos.org/index.php/KDE_Installation")

I'd wait til your hard drive issue is sorted though.

Did you try this guide to get your floppy working?
[http://doc.gwos.org/index.php/Floppy_mount_issues]("http://doc.gwos.org/index.php/Floppy_mount_issues")

---

### Post by Topaz on 2006-04-04
[QUOTE=ferebee]Aha!
Now we're getting somewhere, Your Knoppix screenshot tells us exactly what your hard drives are called, and how linux sees them.
While you are in Knoppix try

```
kwrite /etc/fstab
```  in terminal and post it here for us.
With this info we should be able to get your drives recognized.

[COLOR="Green"] I did try earlier to use kterminal and it wiuld not allow me. It said it needed a password and I thought demo was it. It was wrong. Is kwrite a command prompt?     [/COLOR]

---

### Post by ferebee on 2006-04-04
[QUOTE=Topaz][QUOTE=ferebee]Aha!
Now we're getting somewhere, Your Knoppix screenshot tells us exactly what your hard drives are called, and how linux sees them.
While you are in Knoppix try

```
kwrite /etc/fstab
```  in terminal and post it here for us.
With this info we should be able to get your drives recognized.

[COLOR="Green"] I did try earlier to use kterminal and it wiuld not allow me. It said it needed a password and I thought demo was it. It was wrong. Is kwrite a command prompt?     [/COLOR][/QUOTE]

Okay, try clicking on Home on the taskbar. This will open Konqueror, KDE's
file manager - browser. Beside the back and forward arrows is an up arrow.
Keep hitting up til you get these folders in view, or clear the url bar and type / there. That will bring you to your root folder.
[ATTACH]8012[/ATTACH]

That's your basic linux filesystem, fstab is located in the etc folder.
It's been a long time since I booted up my Knoppix livecd so I hope the structure is the same.

*edit: booted into knoppix livedvd to check that this works!*

In the meantime, could you tell us what fiesystems you are using on 
hdb1, hdb2 and hdc1?  A Windows filesystem like NTFS, Fat32 or Linux
filesystem like ext3, ext2 or reiserfs? This information will help work up
an fstab that will work, if you can't get to Knoppix's fstab file.

---

### Post by Topaz on 2006-04-04
[QUOTE=ferebee][QUOTE=Topaz]

Okay, try clicking on Home on the taskbar. This will open Konqueror, KDE's
file manager - browser. Beside the back and forward arrows is an up arrow.
Keep hitting up til you get these folders in view, or clear the url bar and type / there. That will bring you to your root folder.
[ATTACH]8012[/ATTACH]

That's your basic linux filesystem, fstab is located in the etc folder.
It's been a long time since I booted up my Knoppix livecd so I hope the structure is the same.

*edit: booted into knoppix livedvd to check that this works!*

In the meantime, could you tell us what fiesystems you are using on 
hdb1, hdb2 and hdc1?  A Windows filesystem like NTFS, Fat32 or Linux
filesystem like ext3, ext2 or reiserfs? This information will help work up
an fstab that will work, if you can't get to Knoppix's fstab file.[/QUOTE]

[COLOR="Green"]The screenshot is of my breezy desktop
                                                                I'm sure that is c:\drive, G:\ is ext2 or 3,   F:\ is fat i think, D:\use to be ntfs, Will try to get other info with knoppix Wed.  [/COLOR]

---

### Post by johnnymac on 2006-04-04
It's so.......green

---

### Post by Topaz on 2006-04-05
[QUOTE=Topaz][QUOTE=ferebee]

[COLOR="Green"]The screenshot is of my breezy desktop
                                                                I'm sure that is c:\drive, G:\ is ext2 or 3,   F:\ is fat i think, D:\use to be ntfs, Will try to get other info with knoppix Wed.  [/COLOR][/QUOTE]


[COLOR="DarkOrchid"] Here are screenshot in knoppix.         [/COLOR]

---

### Post by ferebee on 2006-04-05
[QUOTE=Topaz][QUOTE=Topaz]


[COLOR="DarkOrchid"] Here are screenshot in knoppix.         [/COLOR][/QUOTE]

That's exactly what we need!

Okay for the next bit, you should be booted back into Ubuntu.
Before you do any of this I would wait a bit and see if any other users
might see any problems with my method. I'm relativeley new to linux, less than a year
but I've had to make edits to my fstabs on the various distros that I have installed
when I've made partitioning changes. 

Could somebody check this over for any errors or extra fstab tips and tricks?


Step 1
Open terminal, and type
```
sudo nautilus
```

Nautilus will open looking different than it usually does, because you are browsing
as a root user.
You should see a sidebar called **Places**
Under this click on **File System** then on the **Media** folder
There should be folders inside here already for your cdrom drives
and the hda1 and sda1 which ubuntu already recognizes.You are going to create folders
here for the drives you are trying to access.
To do this go to **File>Create Folder** and name the first one hdb1 
 repeat and name the second hdb2, the next hdc1.

Step 2

Still in nautilus, click back and find your **etc** folder.
Find your fstab file here and right click on it and select copy
Paste it to your Desktop and rename it as backup fstab or similar, so you'll have a 
backup you can find easily.
Now, go back to the etc folder and open your fstab. It will open up
in gedit and this time you will be pasting in new lines.

Underneath the /dev/hda5  line, make a space and paste in these lines:

```
/dev/hdb1 /media/hdb1   ext2    defaults        0       2
/dev/hdb2  /media/hdb2   vfat   defaults        0       0
/dev/hdc1   /media/hdc1  ext3  defaults        0       2
```

and then save. 
It might be a good idea to post your new
fstab here in the forums so we can see it, just to be sure everything is right, and
have a few more users check it over.
When you close it reboot. Hopefully this will put your drives on your Desktop and in
Places>Computer.
This should give you read-only access to these drives 
as a regular user. This might seem inconvenient, but I think it's safer.
To get write access you can just open Nautilus file manager
with the Terminal command sudo nautilus like we did above.

I don't believe writing to an NTFS formatted drive is possible, though I could be wrong about that

---

### Post by Topaz on 2006-04-05
[COLOR="Green"] I did your changes and here is the screenshot.    [/COLOR]


[COLOR="Green"]Is it possible to get them named the same as they were in knoppix or do they use different ids. Right now hdb1=53.5gig which is my d:\drive. I don't know what hdb2 and hdc1 are the size don't match any harddrives. Filesystem=212 gig and I figure that it is my C:\drive. As you can see you got somethings to show up on my desktop, sure hope this helps some other neebie.         [/COLOR]

---

### Post by m.musashi on 2006-04-05
I kind of jumped to the end of this thread so sorry if this was mentioned but have you tried [diskmounter](https://wiki.ubuntu.com/AutomaticallyMountPartitions)? It has worked great for me.

---

### Post by ferebee on 2006-04-05
[QUOTE=Topaz][COLOR="Green"] I did your changes and here is the screenshot.    [/COLOR]


[COLOR="Green"]Is it possible to get them named the same as they were in knoppix or do they use different ids. Right now hdb1=53.5gig which is my d:\drive. I don't know what hdb2 and hdc1 are the size don't match any harddrives. Filesystem=212 gig and I figure that it is my C:\drive. As you can see you got somethings to show up on my desktop, sure hope this helps some other neebie.         [/COLOR][/QUOTE]

That's great! They're showing now, Gnome and KDE use different naming conventions, but they're basically the same thing. If you want to edit your fstab again, and rename those folders you created in /media, you could do that, and give
them labels that would make more sense to you.

For example, I call my hard drives Wallace and Gromit ;) 

in your fstab you could change the line to read
```
/dev/hdb1 /media/Wallace   ext2    defaults        0       2
```
then go to /media and using the **sudo nautilus** command and rename folder hdb1 to Wallace. Substituting whatever you want to call them, of course.

I'd go have a good look at the contents of the drives, though, just so you know 
what's stored where, get yourself oriented. As for those sizes,Nautilus reports the free space on the disc or partition, not the total size.

I know Linux seems to have a steep learning curve, but once you get used to 
the differences, well, you'll probably know a whole lot more about computers than you did before!

Keep on reading the forums, too. You learn a lot by reading about other peoples problems. I've had a lot of "Oh! I didn't know I could do that! Neat!" moments reading through the posts here.

---

### Post by Topaz on 2006-04-05
[QUOTE=m.musashi]I kind of jumped to the end of this thread so sorry if this was mentioned but have you tried [diskmounter](https://wiki.ubuntu.com/AutomaticallyMountPartitions)? It has worked great for me.[/QUOTE]

[COLOR="Green"] That worked great. That info is not present in the fstat file. The ones on the desktop are sort of wrong. Here is a screenshot of following your instructions.             [/COLOR]

---

### Post by Topaz on 2006-04-05
[QUOTE=Topaz][COLOR="Green"] That worked great. That info is not present in the fstat file. The ones on the desktop are sort of wrong. Here is a screenshot of following your instructions.             [/COLOR][/QUOTE]






[COLOR="Green"] Like my mother and wife always said, "Can't leave you alone for a minute." I somehow got all those hda to sda and their 1,2,5s in the wrong location. They have a padlock on them and I tried move, delete and can not move them. I all
so noticed on bootup filesystem failed. Here is is the screenshot of my hda, sda screw up.          [/COLOR]

---

### Post by Topaz on 2006-04-06
[COLOR="Green"]I tried to do some editing and the harddrive with all the work the last few days will not boot up. That drive is my 225 gig. I have removible harddrive drawers and can change c:\drive. I now have the 6 gig drive in the drawer, it was the first one I tried ubuntu on and decided I liked it. I then took the 6 out and formated the 225 for linux and put ubuntu on it and was doing the alterations you have sugested. I went a little over board and now have to use the 6 gig for now. As I stated in an early reply that when the computer is booting up it has (local file system failed). I was getting that on both harddrives. There maybe away to get the other harddrive to boot without looseing anything on it. My live knoppix cd will let me see that harddrive, but will not allow me to do any editing with knoppix. I don't know the password for allowence. Sitting between a rock and a hard place. When over 70 things sure seem harder to do.[/COLOR]

---

### Post by Topaz on 2006-04-07
[QUOTE=Topaz][COLOR="Green"]I tried to do some editing and the harddrive with all the work the last few days will not boot up. That drive is my 225 gig. I have removible harddrive drawers and can change c:\drive. I now have the 6 gig drive in the drawer, it was the first one I tried ubuntu on and decided I liked it. I then took the 6 out and formated the 225 for linux and put ubuntu on it and was doing the alterations you have sugested. I went a little over board and now have to use the 6 gig for now. As I stated in an early reply that when the computer is booting up it has (local file system failed). I was getting that on both harddrives. There maybe away to get the other harddrive to boot without looseing anything on it. My live knoppix cd will let me see that harddrive, but will not allow me to do any editing with knoppix. I don't know the password for allowence. Sitting between a rock and a hard place. When over 70 things sure seem harder to do.[/COLOR][/QUOTE]

[COLOR="Blue"]It is Friday the 7th and I finally got ubuntu back up and running after 10 refomats and installs. As you can see by my new screenshot I have Kubuntu running and still the only icon is my firewire on the desktop. My 3 harddrives and 1 cd, 2 dvd writers are still missing in action.
[/COLOR]

---

### Post by m.musashi on 2006-04-07
After reinstalling did you do diskmounter? I'm not sure if it works in KDE but it should. It should also find and mount all your hard drives/partitions (unless somehow hidden - I noticed that it doesn't mount the hidden dell partition related to the restore function). Optical drives seem to only mount when there is disc inserted although they usually show up in a file browser.

I don't know how the removable HDs play into this. I would think that any drive inserted and active at boot would be seen by diskmounter. However, if you run diskmounter and then change drives I wonder if it won't find it.

---

### Post by Topaz on 2006-04-07
[QUOTE=m.musashi]After reinstalling did you do diskmounter? I'm not sure if it works in KDE but it should. It should also find and mount all your hard drives/partitions (unless somehow hidden - I noticed that it doesn't mount the hidden dell partition related to the restore function). Optical drives seem to only mount when there is disc inserted although they usually show up in a file browser.

I don't know how the removable HDs play into this. I would think that any drive inserted and active at boot would be seen by diskmounter. However, if you run diskmounter and then change drives I wonder if it won't find it.

[/QUOTE] That did not do anything.
[COLOR="Green"][/COLOR]

---

### Post by m.musashi on 2006-04-07
[QUOTE=Topaz]That did not do anything.
[COLOR="Green"][/COLOR][/QUOTE]
This may be a KDE issue. I just ran diskmounter in KDE and although it said it mounted all partitions I couldn't find any (the computer I did this on is dual boot so there is a windows partion it should have mounted). Perhaps if I knew how to navigate KDE better it may be there. In any case, I logged out and then into a gnome session and there on my desktop is the windows partition (sda2).

I don't know how KDE handles other partitions but give gnome a try. If you mount and see them in gnome then it's only a KDE issue to work out. If they won't mount in gnome then there is a larger problem.

---

### Post by Topaz on 2006-04-07
[COLOR="Green"] Another dum question? I do not leave my printer  (HP g85 ) turned on all the time. When I ran windows if I wanted to print something I would turn it on. My kubuntu states the printer is there but it did not print to it using the different text programs. I turned the printer on after boot up.         [/COLOR]

---

### Post by ferebee on 2006-04-07
[QUOTE=Topaz][COLOR="Blue"]It is Friday the 7th and I finally got ubuntu back up and running after 10 refomats and installs. As you can see by my new screenshot I have Kubuntu running and still the only icon is my firewire on the desktop. My 3 harddrives and 1 cd, 2 dvd writers are still missing in action.
[/COLOR][/QUOTE]

Oh my goodness!
What happened? 

It looks like you might have to edit your fstab again and add the entries for those hard drives again, along with creating the corresponding folders in the /media folder. If you have changed the way the drives are arranged 
you might need to re-post your current fstab and perhaps a screenshot of the contents of the /media folder.

Your cd and dvd drives typically do not show up on the desktop unless you have a cd or dvd in them.  If they contain no media, they don't need to be on the desktop. When you insert a cd or dvd
then this will appear on the desktop.

The drive you installed Ubuntu on will not show up on the desktop, except as your Computer icon or your Home icon (on the taskbar in kde, it appears.) That is how you access this drive, because this is your root filesystem. If you were to rename that, then ubuntu wouldn't be able to find it. It doesn't need to be mounted because it mounts automatically on boot.

The printer doesn't need to be turned on all the time, but when you set it up for the first time, with the System>Settings>Printing Manager utility, then I'd recommend turning it on before you boot. After it's set up and you get a correct test page out of it, it shouldn't matter if it's turned on at boot or not.

Edited to add:
You'll probably need to follow this doc once again for your floppy:
[http://doc.gwos.org/index.php/Floppy_mount_issues]("http://doc.gwos.org/index.php/Floppy_mount_issues")

---

### Post by Topaz on 2006-04-14
I'm back and it is 04-14-06 and I still am lost. Here are some snapshots to show what I have tried to do. The fire wire icon in upper left corner, somehow I refomated it because I want to use it for storage and it has the error now. The big dummy will be waiting for good news. My problem here could may be turned into a insturction page for neebies by a ubuntu geek.

---

### Post by wolfee on 2006-04-14
1st off your swap file partition should only be 512 mb anything bigger is a waste.
2nd why don't you install Ubuntu 5.10? It sounds and looks like your using 5.04?
also if you check out 
[https://wiki.ubuntu.com/HardwareSupport?highlight=%28%28HardwareSupportComponentsMultimediaWebCameras%29%29](https://wiki.ubuntu.com/HardwareSupport?highlight=%28%28HardwareSupportComponentsMultimediaWebCameras%29%29)
This will tell you what hardware works and doent work. I recomend that you spend the money to buy hardware that is known to work so you wont have to install tar gz files and such. It's worth paying the extra money for the time you will save. Also a newer version of Ubuntu (dapper Drake) is comming out soon so you might want to try it out and see if it "sees" more of your hardware.

---

