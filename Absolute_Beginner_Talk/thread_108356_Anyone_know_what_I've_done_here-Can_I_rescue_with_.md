---
title: "Anyone know what I've done here?-Can I rescue with a live cd?"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by gedrick on 2005-12-25
I have Ubuntu 5.10 with kde installed and the gnome uninstalled-I couldn't install Kubuntu from the disc-it said it was corrupted.
 I had been following instructions on a maltese linux site on how to play about in command line-create new folders etc. When I came to shut down my computer it was taking a long time and I was in a rush, so I cut the power. Now when I try to boot I get this:
 
 /etc/rcS.d/S10checkroot.sh:line 309: /lib/init/readlink:Permission denied
 
 I get about 20 more lines which mention other files all "Permission denied"
 
 Then I get:
 
 No more processes left in this runlevelr 5 minutession deniedermission
 
 Leave it running and it tries to respawn Id 1-6 but it says:
 
 *Id "1" respawning too fast: disabled for 5 minutes
 
 and:
 
 *cannot execute "/sbin/getty"
 
 I don't have a rescue disk and I tried something with the ubuntu installation disk that I had seen where you got to a prompt and typed "rescue" and then reboot - it didn't work for me.
 I am not sure if playing on the command line has got anything to do with my problem, it seemed to be running fine up to switching the power off.

---

### Post by hogoh on 2005-12-25
Sorry!  I don't know what you've done there.  I am pretty sure that, although using the live CD will give a good chance of getting your computer running again, a live CD shouldn't affect the problems you describe. (Live CDs are intended to avoid affecting one's hard drives; from the output you quote, a hard drive is the most likely seat of the problems you're having.)  That is, take out the live CD & your computer is likley to be back in the state you describe. 

'Maybe, not at all sure, in the screeds of report on what's gone wrong suggest what you might try or comment (in part?) on what's gone wrong.  The nuisance could be that everything goes past so quickly you can't read it ...

---

### Post by gedrick on 2005-12-25
I'm online at the moment with the corrupt Kubuntu dvd and I can see the hard disk with my installation on it but I haven't got a clue where to look for report logs to find out what went wrong, or what to do to repair things so it will boot again.Anyone got any clues?

---

### Post by Herman on 2005-12-25
As far as rescuing your Ubuntu installation itself goes, I can't help your there, but I can tell you how to rescue your files to another networked computer if you have one, then you can re-install Ubuntu, that might be the easiest. Or else fix it later.
I'm presuming you are worried about the files mainly.

Refer to pages in my signature link for anything not clear enough here.

File Rescue, Breezy Live CD to Ubuntu SSH server via LAN

1) Place Ubuntu 'Breezy' live CD in CD-ROM drive of the disabled computer and re-boot with it.

2) Have the server computer running. Any kind of computer will do as long as it has some kind of networking set up and runnning. Windows network is even okay for this.
This example will demonstrate using SSH network for this job. (My other PC, 'red', already has SSH server installed and running, see my sig link page for how to set that up if you need to.)

3) When Ubuntu 'Breezy' live CD is booted, in disabled computer, go to 'Applications','Accessories','Terminal', to open a terminal (just in case anyone doesn't know). hehe.

4) code: sudo fdisk -l

5) From the output of the above command, choose the filesystem you want to mount and open.
   For example: /dev/hda2  *  3266   3647   3068415  83 Linux

6) a) code: sudo mkdir /media/hda2
   b) code: sudo mount -t ext3 /dev/hda2 /media/hda2
following this, and icon called hda2 should appear on your desktop.

7) Open your new icon and browse to your /home/herman (or whatever your username is) folder.

   Okay, so far? We are half way already!

8)Change to a clean desktop (one of the four desktop squares down in the left lower corner of your desktop). This isn't compulsory, it's just to save congestion.

9) Click 'Places', 'Connect to Server',
a) server type: set to:  'SSH'
b) Server: (the IP address of your server: 192.168.1.205 ((for example)( 'ifconfig' if you need to.)
c) Port:              22
d) Folder:          /
e) Username:      herman    (or whatever your username is for the computer you are connecting to).
f) name to use:     red      (the hostname for the computer I am connecting to)
g) hit the button called 'Connect'.

10)An icon called 'red' will appear under your 'hda2' icon on your desktop.
a) Open 'red' by clicking on the icon,
b) Read question about the identity of 'red' being unknown, click 'connect anyway'.
c) Type in the usual password for 'red' used for regular logins to 'red'.
d) Red's filesystem should now appear in a window on your desktop, open /home/herman in red.

11) Click the other desktop where we left open the filesystem for the disabled computer, and select the files to be copied.
(See also at this point [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/") back-up page, for more info).
12) Click the desktop where we left 'red' open (the rescue computer). Paste all your wanted files to be saved into a folder you make first in 'red'.

That's it! It's all over bar the shouting! (An Australian expression meaning 'buy me a beer'). :D (Only joking).

Oh, and you can unmount (umount) everything and shut all down whenever you please too. (Bye).

---

### Post by Herman on 2005-12-26
[http://www.ubuntuforums.org/showthread.php?p=604133&posted=1#post604133]("http://www.ubuntuforums.org/showthread.php?p=604133&posted=1#post604133")
gedrick, if you can get it to boot at all, check this thread out too, (above), also about turning the computer off too fast, and try clearing your swap area as explained and see if that fixes your too, (it's worth a try). :D (Herman).

---

### Post by gedrick on 2005-12-27
Herman, I tried the first part of what you wrote but I couldn't get anything to appear on my desktop.
I have got 2 other hard drives installed-1 is sata storage in fat32. The other is ntfs.I thought I might be able to copy it on there.I am using Kubuntu 5.10 live dvd and I have had it telling me it is copying to the fat32 drive but nothing happens.
This is the result of fdisk -l


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   c  W95 FAT32 (LBA)

Disk /dev/hda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3581    28764351   83  Linux
/dev/hda2            3582        3736     1245037+   f  W95 Ext'd (LBA)
/dev/hda5            3582        3736     1245006   82  Linux swap / Solaris

Disk /dev/hdc: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3736    30009388+   7  HPFS/NTFS
ubuntu@cpc3-bolt4-4-0-cust224:~$   


I haven't got a lot to lose on it, it's mainly bookmarks- I just thought there would be a quick way of repairing it so it would boot and I could continue my journey.

---

### Post by Herman on 2005-12-28
> I haven't got a lot to lose on it, it's mainly bookmarks- I just thought there would be a quick way of repairing it so it would boot and I could continue my journey. 
gedrik, well you have to wieght up which might take up more of your time, and decide how valuable your time is. It might be faster for you to just re-install. If it's really only a few bookmarks, you will probably remember most of your favourite sites anyway, and will be able to google them back again quickly enough. A re-install will take between 30 minutes and 1 1/2 hours or so.
Other than that, if you have some spare time, and you are interested, there are some things we can try, but nothing guaranteed to fix anything. I wouldn't like to be wasting your time.
The idea of formating your swap area somehow has worked for me in the past following similar circumstances, but that does not mean it will cure every computer problem in the world. Still, it could be worth a try. You should be able to do that with Gparted on the live CD, if it will let you unmount the swap. That would only take a few minutes to try.
Knoppix Cd has some very good diagnostic tools for trying to troubleshoot computer problems that I can point you to, if you have a knoppix CD.
Well, you decide how much time it is worth spending on it. I'll keep an eye and see how you are getting along, but I might have to go away and work too sometimes. Right now I am  free for a while.  :D (Herman)

---

### Post by Herman on 2005-12-28
> Herman, I tried the first part of what you wrote but I couldn't get anything to appear on my desktop.
I have got 2 other hard drives installed-1 is sata storage in fat32. The other is ntfs.I thought I might be able to copy it on there.I am using Kubuntu 5.10 live dvd and I have had it telling me it is copying to the fat32 drive but nothing happens. I just re-read the first part there of what you posted, gedrick, and I am thinking some more....
So you want to copy files from one disk to another with the live CD? That shouldn't be too hard. Only thing is, I don't own any computer with more than one drive, so I can't tell you for sure, but I can try and imagine what you might need to do.
I think maybe you need to 'mount' the drives you want to copy from and to.
Do you know how to do that? You'll want to copy from your /dev/hda1 partition to your /dev/sda1, it looks like to me. Does that seem right ot you, gedrick? If that is what you want I'll make up some commands for mounting those in a few minutes. (Back soon)...

---

### Post by Herman on 2005-12-28
Try these and see if it works after that or not:
```
sudo mkdir /media/fat32disc
sudo mount /dev/sda1 /media/fat32disc -t vfat -o umask=000
``` That should give you an icon on your desktop for your FAT32 drive that you want to paste things into.

EDIT (29/12/05) You can open this icon and then create a new folder somewhere in which to paste your rescued files into which we will gain access to in the next part of the process.
> sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu That should give you an icon on your desktop for the Ubuntu drive, that you want to copy things from.

EDIT (29/12/05) You can open this icon and then navigate through your Ubuntu file system to find the items that you would like to save, and copy them one at a time. Then go to the other place where you want to save your data, and paste it into your new folder, previously mentioned above.

I hope these work okay for you, gedrik, do they look right to you?
Try to move your files after mounting them now, and see if it works okay for you. I hope this helps, I have no real experience with multiple hard drives, or sata, or NTFS. (Fingers crossed!) :D (Herman)

EDIT: You might not get icons on your desktop because your Live CD is KDE, I think you said, so you might have to do looking for you /media directory to find your mounted partitions.

---

### Post by gedrick on 2005-12-28
Herman, Did the sudo mkdir, it didn't show them on the desktop but I found them in the media folder. Fat32 folder and ubuntu folder. Tried to copy and paste the ubuntu folder into the fat32 folder and it went through the motions. When it finished it said: 

could not make 
 /media/fat32disc/ubuntu/<mountpoint>

Made a folder on fat32 named kubuntu and tried to copy and paste into it.
Tried the /home/ged folder and I got: 

could not make
folder /media/fat32disc/kubuntu/home/ged/<mountpoint>

I have managed to copy /paste some downloaded files onto the fat32 drive but when I try to copy folders individually or en masse it fails. There are some folders on the fat32 drive where it has attempted to paste them but they are empty.
I have had an error message:

could not create symlink/media/fat32disc/bin/rbash. please check permissions.

"It never rains but it pours" 
That's a Lancashire saying for sod it I've had enough-time to pull the plug.
Thanks for the advice-I've learned a little bit more.

---

### Post by gedrick on 2005-12-28
Herman just a quick update. I managed to find the bookmarks and copy it to the fat32 drive so hopefully when I reinstall I can paste it into Konqueror.
Thanks again for the help.

---

### Post by Herman on 2005-12-28
Thank you for the update, gedrick, I am happy now, to read that you have succeeded.
I have edited my instructions to make them more clear for anyone new who might read them and try to follow them too. They need to be able to modify them of course, to suit their own computer. But it is still important for me to get them right. I am sorry I forgot to tell you you need to open the icons and navigate through your system to pick out what you want. I am happy you worked that out now. Sorry about that, and thanks for bearing with me. Do the edited instructions look correct now?
Good luck with your re-install, gedrick, and all the best! (Herman) :D

---

