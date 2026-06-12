---
title: "How do I copy a file from the desktop to a floppy disk?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-07-03
Ubuntu v. 5.10

There is a file on my desktop that I had downloaded named:  panther1.jpg that I want to copy to a floppy.  I tried it using 'Terminal' but no luck.  I had used the sudo cp command.  I had used the name in various ways.  I always get the message cannot stat 'panther1.jpg'

I tried to do it using the GUI:  I got the floppy to show up under Applications>Accessories>File Browser>File System>dev>fd0.  fd0 being the name of the floppy, I assume.  I can't open the fd0:  I get the message "Couldn't display "/dev/fd0".  I tried dragging the file icon to the floppy; no luck.  

Now what?

---

### Post by st00ner on 2006-07-03
hmm what kind of floppy drive is this? is this a laptop? Desktop? please be more specific and i will try to help

---

### Post by headsh0t13 on 2006-07-03
I`m not sure, but does it need to be mounted first?
```

mkdir /media/floppy0

mount dev/fd0 /media/floppy0
```

or > 

start a root terminal
```

sudo gedit /etc/fstab

```
Change the floppy line to read:
```

/dev/fd0        /media/floppy0  ext2    rw,user,noauto  0       0

```

Or if you would like to use that floppy in Windows too instead of 
/dev/fd0        /media/floppy0  ext2    rw,user,noauto  0       0 
type:
/dev/fd0 /media/floppy0 vfat,ext2 rw,user,noauto 0 0

---

### Post by JEBB on 2006-07-03
The computer in question is a Compaq 1688 laptop.  It has a 400MHz K6 cpu with 192MB RAM, CD and floppy drive.  I was able to format the floppy with Ubuntu so it knows it is present.

---

### Post by keith whitehouse on 2006-07-03
hi jebb,

all I do is to go to Places, and drag down to Computer and then double click the floppy icon. When it is finished shut down the file browser window and you should have a floppy icon on the desktop. Just drag the .jpg file onto the floppy icon and let go, it works for me.

best regards keith

---

### Post by JEBB on 2006-07-03
Keith:  I tried what you said and got an error message:

Error "Invalid URI" while copying

When I double click on the Floppy Drive icon I get the error message:

Unable to mount the selected volume.

Under that message is a drop down message:

Error:  given UDI is not a mountable volume

What is that telling me?

---

### Post by JEBB on 2006-07-03
I have right clicked on the floppy drive icon and chosen properties.  I see that the owner is root, not me.  So do I somehow need to change ownership of the floppy drive?  If so, how?

---

### Post by catlett on 2006-07-03
Post the output of this command ```
sudo gedit /etc/fstab
``` It's the command already posted above. That will launch the text editor with the file that tells the computer what and how to mount on startup.
What type of file did you download? Is it a jpg. Because the error "invalid uri" makes me think you downloaded a link to a jpg but not the actual jpg. What kind of icon does it have on your desktop? What happens when you double-click on it? Might be nothing but I thought I would throw it out there.

---

### Post by JEBB on 2006-07-03
At the terminal I entered:

sudo gedit /etc/fstab

That gave me the text file and the line that has floppy in it reads:

/dev/fd0    /media/floppy0   auto    rw,user,noauto  0  0

I wish I knew what that all means.

I right clicked on the file and chose properties.  I says that it's file type is a JPEG image and its size is 130.1 KB.

---

### Post by catlett on 2006-07-03
I don't understand it your  /etc/fstab is correct. 
 Just for your info

[COLOR="Red"]/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR]
[COLOR="Red"]/dev/fd0 [/COLOR] is the device name. dev = device. fd = floppy drive. 0 = 1st drive.
[COLOR="Red"]/media/floppy0[/COLOR] this is the mount point for that device. It is mounted in the folder media as folder floppy0. when things are mounted in media they show an icon on the desktop.
[COLOR="Red"]auto[/COLOR] auto is the place for the filesystem type. your other entries probably say ext3, swap, and ntfs (if you have windows). it is auto here because auto means the system will automatically detect the type of filesystem because the floppy could be formatted for linux or windows
[COLOR="Red"] rw,[/COLOR] rw means you can read and write to it. volumes can also be mounted "ro", read only
[COLOR="Red"]user[/COLOR] means a user can mount the device as opposed to "nouser" which means only root can mount it ,
[COLOR="Red"]noauto [/COLOR] means the device is not mounted automatically at startup. auto means it will be automatically mounted. floppy's and cd roms are noauto so you can put them in and out but you have to explicitly mount and unmount them.
[COLOR="Red"] 0[/COLOR] is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. If it's zero, dump will ignore that filesystem.
[COLOR="Red"]0[/COLOR] is a fsck option. fsck looks at the number  to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.

Not that it helps to know at the moment.

Let's try a step by step simple approach. First get a floppy and put it in the drive. Use the floppy formatter. It is under Applications<System Tools<Floppy Formatter. If it doesn't appear there, go to the Alacarte Menu Editor. It is under System<Accessories<Alacarte Menu Editor. Check off the box for floppy formatter so it can be seen in the menu.
Next launch the floppy formatter and select "linux native" and format it.
Next go to Places<Computer. Double click on the floppy icon. This will mount the floppy (if it doesn't then you have another issue.  post the error, if not continue)
Double click the floppy icon again and it will open a folder.
Minimize the floppy folder window if it is taking up the who;e desktop. Drag the jpeg image over to the folder and drop it. That's it.
Close the window. Right-click on the floppy icon to get a menu. Select "unmount volume". The data is written to the floppy and you can take it out. 
If this process doesn't work post any error you get.

---

### Post by JEBB on 2006-07-03
Thanks Catlett.

I formatted the floppy as you said.  When I tried to open the floppy by double clicking it I got the error message:

"Unable to mount the selected volume."

under "Show more details" it said:

"Error:  given UDI is not a mountable volume"

Do you have any idea what is wrong here?

---

### Post by catlett on 2006-07-03
Sorry for the long wait. Wife made dinner.
Are you running Breezy Badger or Dapper Drake? There appears to have been a bug in Breezy. SDo before I go into the bug. Are you running Breezy?

P.S. Just to go into the bug. It was about a version of pmount. Pmount is involved in mounting removable devices, mostly with usb devices etc. Anyways the bug reports people had this same problem as you but it disappeared when they upgraded to pmount version 0.9.6.
Go to Synaptic Package Manager. Search for pmount. See what version you are running.

---

### Post by JEBB on 2006-07-03
I have Ubuntu 5.10.  The pmount version is 0.9.5.  It says that 0.9.5-Ubuntu5 is the latest version.  It says nothing about version 0.9.6.  

The point of my excercise was to save some files to reinstall after upgrading to version 6.  It appears that it would be easier to just upgrade the system.  Too bad.

---

### Post by catlett on 2006-07-03
I didn't even notice the first post where you say you have Breezy. That's the issue. The bug report said people were fixing the issue by changing the backports repository to Dapper (this was back when Dapper was in testing) and u[pgrading pmount to version 0.9.6.

So upgrading to Dapper will solve your floppy issue but it is moot because you wanted to save some files before upgrade. Well that stinks. Problem solved but issue not resolved.

---

### Post by RRS on 2006-07-04
Just a guess, but;
```
sudo mkdir /media/floppy0
```

Try mounting from the command line and see if you get a different or more explicit error.

---

### Post by JEBB on 2006-07-04
Following RRS's suggestion I entered the command:  

sudo mkdir /media/floppy0

After entering my password I got the following message:  

mkdir: cannot create directory '/media/floppy0' : File exists

---

### Post by RRS on 2006-07-04
[QUOTE=JEBB]Following RRS's suggestion I entered the command:  

sudo mkdir /media/floppy0

After entering my password I got the following message:  

mkdir: cannot create directory '/media/floppy0' : File exists[/QUOTE]

Good morning. 
Sometimes I forget to create a path when I try to do something between directories but apparently you've allready covered that.

Did you try;
```
sudo mount dev/fd0 /media/floppy0
```

---

### Post by enyaw on 2006-07-04
[QUOTE=keith whitehouse]hi jebb,

all I do is to go to Places, and drag down to Computer and then double click the floppy icon. When it is finished shut down the file browser window and you should have a floppy icon on the desktop. Just drag the .jpg file onto the floppy icon and let go, it works for me.

best regards keith[/QUOTE]

WOW! thanks keith, really a slick way to do it.  I followed your directions, and after went back into places - home to drag and drop two files.  Everything running hot straight and normal.  Great :D

---

### Post by gary4gar on 2006-07-04
i am facing same prob in ununtu 5.10.when i use floppy it says
> Unable to mount the selected volume.
Error: given UDI is not a mountable volume 

i tried @RRS solution then it asked for file system i tried & entered -t vfat but no help.pls tell me a diffrent solution than upgarde as i have ordered drapper and i'll soon updarde till then i need to fix this as a temp measure

regards
gary

---

### Post by JEBB on 2006-07-04
The h*ll with it.  I just install version 6 and see how that goes.  Not being able to use floppy disks is a show stopper for me with version 5.

---

### Post by JEBB on 2006-07-04
The h*ll with it.  I'll just install version 6 and see how that goes.  Not being able to use floppy disks is a show stopper for me with version 5.

---

### Post by matt1060 on 2006-08-01
Hi Catlett, I am running BB on a compaq armada e500 and I have the same prob as Jebb relating to invalid uri on my fd0.  Is there a patch for this bug?  I don't want to upgrade unless I absolutely have to because it took forever to get the moden issue resolved for BB and It looks as though DD did not address this issue.
TIA, Matt

---

### Post by catlett on 2006-08-01
> **matt1060 said:**
> Hi Catlett, I am running BB on a compaq armada e500 and I have the same prob as Jebb relating to invalid uri on my fd0.  Is there a patch for this bug?  I don't want to upgrade unless I absolutely have to because it took forever to get the moden issue resolved for BB and It looks as though DD did not address this issue.
TIA, Matt

Sorry not to link the bug report. I try top always link to what I find. Now I can't get the bug report.
But I found another thread that says it has a solution. It involves updating The pmount package. It needs to be version pmount 0.9.6-1  (or higher I would suppose, the bug was a while ago)
It appears to be an easy fix now. Before you had to enable a dapper repository to access it but now it is in the breezy backports repository. So if you don't have the backports repo enables, use this command to open the file and then paste the url I give you into it.
```
sudo gedit /etc/apt/sources.list
```
When it opens, add this line to it
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```Make sure to save the file. Then update the repo cache
```
sudo apt-get update
```I would use Synaptic to install pmount just so you can see it first and make sure it is the version you are loooking for.
System<Administration<Synaptic Package Manager when synaptic opens select the search box and enter pmount. Just double check that the version is 9.6-1 to be safe and mark it for installation. Make sure to hit apply.

Here is the link I found [http://www.ubuntuforums.org/showthread.php?t=85777](http://www.ubuntuforums.org/showthread.php?t=85777)
This one gave some commands to use to work around it but it appears upgrading through the backports will work and it is simple but just in case, here is the thread [http://www.ubuntuforums.org/archive/index.php/t-76517.html](http://www.ubuntuforums.org/archive/index.php/t-76517.html)

---

