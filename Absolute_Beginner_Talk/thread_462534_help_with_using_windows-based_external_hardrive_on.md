---
title: "help with using windows-based external hardrive on ubuntu"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by matious on 2007-06-02
i recently installed ubuntu, loving it so far. I have a minor problem though, i have a bunch of music on my external hardrive which easily can be put on amaroK or any of the other media players etc. But when i try to put files i downloaded using Ubuntu and put them on my hardrive it tells me i dont have permission.

i was told i need to create a mount point, but im not exactly sure as to how i go about doing this. It is a NTFS "simpledrive" 60 gig harddisk. 

if someone could help me with this that'd be great, its the only thing really holding me back from enjoying ubuntu as much as i'd like to so far. :)

---

### Post by Inxsible on 2007-06-02
> **matious said:**
> i recently installed ubuntu, loving it so far. I have a minor problem though, i have a bunch of music on my external hardrive which easily can be put on amaroK or any of the other media players etc. But when i try to put files i downloaded using Ubuntu and put them on my hardrive it tells me i dont have permission.

i was told i need to create a mount point, but im not exactly sure as to how i go about doing this. It is a NTFS "simpledrive" 60 gig harddisk. 

if someone could help me with this that'd be great, its the only thing really holding me back from enjoying ubuntu as much as i'd like to so far. :)

you can use pmount to install your external HDDs. connect the drive to the computer and then enter these commands and post the output here and we can help you out.

```
sudo fdisk -l
``` and ```
gedit /etc/fstab
```

---

### Post by Inxsible on 2007-06-02
We might also have to change permissions after we create the mount point. But one thing at a time :)

---

### Post by matious on 2007-06-02
okay, heres what came up:

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5853    47014191   82  Linux swap / Solaris
/dev/hda2   *        5854        9564    29808607+  83  Linux
/dev/hda3            9565        9729     1325362+   5  Extended
/dev/hda5            9565        9729     1325331   82  Linux swap / Solaris

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7301    58645251    7  HPFS/NTFS

and:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7aaf0b7d-1e01-4242-a864-32ab6b4d0ce1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e80b02de-9e14-4588-ae9e-9fe96b16a5d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0


---

### Post by Inxsible on 2007-06-02
Since you said it was the 60gb simpledrive, it should be the /dev/sda1

Now to mount it :
```
sudo pmount /dev/sda1 simpledrive
```
thats sda1 (as in - the number one ....not L )

You can change the name to anything you want. for eg. data or anything else you like.
This will create the mount point under /media. Make sure you do NOT already have a folder by the name that you are using, since pmount *creates* the folder too

After you do this, see if you can access it, if not then we will have to change the permissions on it

---

### Post by matious on 2007-06-02
i typed that in and it says "command not found"

---

### Post by Inxsible on 2007-06-02
did you copy paste. If not, are you sure you typed it in correctly ?

you might try this, but i think pmount is pre-installed 
```
sudo aptitude install pmount
```

and then try the above command again

---

### Post by matious on 2007-06-02
okay, i did that and now i get "Error: device /dev/sda1 is already mounted to /media/SimpleDrivePS"

i also tried putting files on there after doing that anyway, and it still says i do not have permission

---

### Post by Inxsible on 2007-06-02
that means that you already have a folder called SimpleDrivePS. Like i said, pmount creates the folder too, so you cannot have an existing folder.

Do this :
```
sudo pumount SimpleDrivePS
``` then ```
sudo rmdir -r /media/SimpleDrivePS
```

and then once again
```
sudo pmount /dev/sda1 SimpleDrivePS
```

---

### Post by Inxsible on 2007-06-02
After you do that, for the permissions problem, do this:
```
sudo chown -R <your-username>:<your-group> <device-name>
```

So assuming your username to be matious and your group to be matious too
```
sudo chown -R matious:matious /media/SimpleDrivePS
```

---

### Post by matious on 2007-06-02
hmm..well i did all of that, and its in my media folder now.

but now i cant even view the contents, so i dont have permission to do anything now. D:

---

### Post by Inxsible on 2007-06-02
did you do the permissions thing that i posted earlier ?

---

### Post by matious on 2007-06-02
yeah

i remember now though

this step

sudo rmdir -r /media/SimpleDrivePS

wasnt working, it was saying it was invalid.

all the other steps were working fine however.


edit:o crap, i think i just pressed something and now simpledriveps is back on my desktop!

---

### Post by Inxsible on 2007-06-02
now I am not sure if you are following the directions properly.

is it working for you now ?

---

### Post by matious on 2007-06-02
no, its back to its default setting it seems.

do you reccomend i do all the steps again?

---

### Post by Inxsible on 2007-06-02
yes, see if that helps !

---

### Post by matious on 2007-06-02
> **Inxsible said:**
> that means that you already have a folder called SimpleDrivePS. Like i said, pmount creates the folder too, so you cannot have an existing folder.

Do this :
```
sudo pumount SimpleDrivePS
``` then ```
sudo rmdir -r /media/SimpleDrivePS
```


okay, once i get to this step it says

> "mathias@mathias-desktop:~$ sudo rmdir -r /media/SimpleDrivePS
rmdir: invalid option -- r
Try `rmdir --help' for more information."

any idea's?

---

### Post by Inxsible on 2007-06-02
Could you try without the -r option
```
sudo rmdir /media/SimpleDrivePS
```

---

### Post by matious on 2007-06-02
i did that
and i get 
rmdir: /media/SimpleDrivePS: Device or resource busy

im not using any of the files of it currently though, so i dont understand why its saying that.

---

### Post by Inxsible on 2007-06-02
did you unmount the drive before doing that ?

if you did, try opening another terminal and enter the command there

---

### Post by matious on 2007-06-02
how do i un mount it when its in the media folder now?

---

### Post by Inxsible on 2007-06-02
i told you this already```
sudo pumount SimpleDrivePS
```

---

### Post by Inxsible on 2007-06-02
after that unplug the drive and then
```
sudo rmdir /media/SimpleDrivePS
```

then plug in the drive again
```
 sudo pmount /dev/sda1 SimpleDrivePS
```

then
```
sudo chown -R matious:matious /media/SimpleDrivePS
```

Hope that helps you out !

---

### Post by matious on 2007-06-02
mathias@mathias-desktop:~$ sudo rmdir /media/SimpleDrivePS
rmdir: /media/SimpleDrivePS: No such file or directory

wtf?


o, and thanks a lot for sticking with me this long as well mate :)

---

### Post by Inxsible on 2007-06-02
No such file or directory is a good thing. =D>

Simply plug in your drive again and do the 
```
sudo pmount /dev/sda1 SimpleDrivePS
```

then
```
 sudo chown -R matious:matious /media/SimpleDrivePS
```

---

### Post by Inxsible on 2007-06-02
[-o<

---

### Post by pappapump on 2007-06-02
Why work it from a command line when the Graphical program does it faster?
I just unmounted mine, then added the ntfs tool from add/remove.
Ran the ntfs tool which found the drive and named the mount point and Viollah!
So much easier than chownin around.

---

### Post by matious on 2007-06-02
um..now its telling me "Error: device /dev/sda1 is already mounted to /media/SimpleDrivePS"

pappapump?

mind breaking that down for me? sounds a lot easier

---

### Post by Inxsible on 2007-06-03
I am not sure that the ntfs-config tool has anything to do with the permissions. So if he cannot see the contents of the drive like he said, he will have to do a chown OR always log in as root (which is not a very good idea)

---

### Post by matious on 2007-06-03
any idea what i do now Inxsible then?

im starting to feel like rebooting xp isnt such a bad idea, music is the main thing i use my computer for, and if i cant easily access it on ubuntu it may not be for me :-/

---

### Post by pappapump on 2007-06-03
No, you don't need root permissions.
When you unmount the drive is there but not ready.
Install the ntfs tool using add/remove and type ntfs in the search bar.
Click to install and then run it.
It will find your drive pretty fast, if not then unplug it and replug the usb.
When the window comes up for mounting the EXTERNAL drive then name it using the space between these marks on the mount point area <  >.
Once you do that, enable read AND write, then you're done.
As a side not let me mention that the drive should have NO attributes preselected.
To confirm this is not the case IF the above method dont work click the drive name after insert and right click the mouse and choose properties, look at the last 2 tabs on the manager screen.
You will find a little arrow head which can be clicked to set attributes, make sure those areas on both tabs are blank.
Then try again with ntfs tools.

---

### Post by matious on 2007-06-03
thanks pappa gonna try it now

---

### Post by matious on 2007-06-03
i open "NTFS configuration tool" but it only gives me one box to check "write support for external devices"

none of the other options you mentioned are there

---

### Post by pappapump on 2007-06-03
Click that first and give it a try, then if that fails mount from the computer icon located in places.
Run ntfs tool again and see if it shows up.
There is a possibility that your ext drive is fat, or fat 32 and if thats the case, save the music files in a folder using XP and use the convert to ntfs tool located in windows OR do a format from windows to ntfs.
When you are done, drag and drop the files back to the drive and it should mount easily.
Linux seems to have a problem with Fat file systems on external devices.

---

### Post by matious on 2007-06-03
nope, still the only option it gives me.

[IMG]http://i134.photobucket.com/albums/q111/matious1/Screenshot.png[/IMG]

---

### Post by pappapump on 2007-06-03
Ok now go to windows and do what I mentioned above.
I just had this same problem with a maxtor external drive till I formatted it to NTFS.

---

### Post by matious on 2007-06-03
but this is already ntfs, and i dont think i even have windows installed anymore :(

ive only been using linux for 1 day and a half, and im not sure how to re-load xp, or dual boot yet.

---

### Post by david_kt on 2007-06-03
I believe you have install ntsf-3g. What you should do is plug in your usb drive, open terminal and run below command:

```
sudo mkdir /media/isoimage
```
```
sudo mount -t ntfs-3g /dev/sda1 /media/isoimage -o force
```

Please let me know the outcome.

DK

---

### Post by matious on 2007-06-03
okay david, this is what it told me

> mathias@mathias-desktop:~$ sudo mkdir /media/isoimage
Password:
mathias@mathias-desktop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/isoimage -o force
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
mathias@mathias-desktop:~$ 


---

### Post by pappapump on 2007-06-03
And theres your problem.
You did a forced shutdown in windows, and or yanked the usb plug before Windows released ownership.
Now your drive is hung till you use a windows based program to correctly eject it.
If not, permissions wont expire from windows.
You can do this from any ntfs based system such as XP, Win2k, Win2k3, or Hopefully, vista.
Insert the usb, let it mount then use the usb manager in windows and choose to stop the drive.
When windows tells you it's safe to unplug then your'e done.

---

### Post by matious on 2007-06-03
so i can go to any computer using windows xp, plug it in? then eject it? then plug it into my linux, and bam were set to go?

---

### Post by elithrar on 2007-06-03
Yes.

---

### Post by Inxsible on 2007-06-03
So the chown didnt work for you still ?

Edit : Never mind !

---

### Post by matious on 2007-06-03
<3 pappa!

wow, that was really all i had to do, i just plugged it back into linux, and its working fine :D

man, i cant beleive it was that simple...

/6 hours of life wasted

---

### Post by pappapump on 2007-06-03
Education is never wasted, good luck bro!

---

### Post by david_kt on 2007-06-03
> **matious said:**
> <3 pappa!

wow, that was really all i had to do, i just plugged it back into linux, and its working fine :D

man, i cant beleive it was that simple...

/6 hours of life wasted

Yes, that was what I have in mind: you have not cleanly remove your usb drive. But for my case 
```
sudo mount -t ntfs-3g /dev/sdb1 /media/isoimage -o force
``` 
always work, I do not need to go to any MS Windows box. If that happen again, you could try below command:

```
sudo apt-get install ntfsprogs
``` 

And after it install ntsfprog, run this command:

```
sudo ntfsfix /dev/sda1
``` 


DK

---

### Post by pappapump on 2007-06-03
It's nice to see that you can remember all that text, I bet you can even remember what it all means too.
What the people migrating from windows want is a simple straight forward way to do what they always did before.
Some of the Linux only people seem to believe that all of this terminal stuff and massive amounts of typing this and typing that is what a common user should learn.
If you continue to follow that road you will have loads of people who just won't be bothered.
For those of you who are completely Linux literate, I'm sure these methods are quite common and easy to do.
But for those of us who are used to a simple GUI, and know that there are Linux based programs which will save all that typing and do these things for us, the above mentioned method is absolutely useless except for the instance where we needed it.
We won't remember it, and even if we write it down, it will be absolute gibberish to us in the future.
Imagine a man who has always run in adidas tennis shoes suddenly being told that those tennis shoes will never fit him again and that he must now wear dress shoes when he jogs.
That is the dillema for those who are new to linux switching from windows.
I get a lot of backlash when I say things like, NO I don't want to learn a load of terminal commands, I want a rich graphical user interface to do those things for me.
What do you expect?
Ok, if your main intent is to keep Linux as a linux user only environment with nobody else making the switch from windows, the above method is a sure way to go.
When a system is advertised in so many circles as a replacement to windows, and BETTER, then what you'll end up with is a lot of people expecting it to pretty much act similar to windows in all the ways that matter.
Typing out sudo commands with no explanation about what that command actually means is paramount to handing out a password with no idea of what its for or why it's needed.
But your heart is in the right place.
I for one, intend to pursue the easy GUI based methods until I find all the ones that perform the functions that relate directly to similar windows functions.

---

### Post by Mr.Beast on 2007-06-03
> **pappapump said:**
> It's nice to see that you can remember all that text, I bet you can even remember what it all means too.
What the people migrating from windows want is a simple straight forward way to do what they always did before.
Some of the Linux only people seem to believe that all of this terminal stuff and massive amounts of typing this and typing that is what a common user should learn.
If you continue to follow that road you will have loads of people who just won't be bothered.
For those of you who are completely Linux literate, I'm sure these methods are quite common and easy to do.
But for those of us who are used to a simple GUI, and know that there are Linux based programs which will save all that typing and do these things for us, the above mentioned method is absolutely useless except for the instance where we needed it.
We won't remember it, and even if we write it down, it will be absolute gibberish to us in the future.
Imagine a man who has always run in adidas tennis shoes suddenly being told that those tennis shoes will never fit him again and that he must now wear dress shoes when he jogs.
That is the dillema for those who are new to linux switching from windows.
I get a lot of backlash when I say things like, NO I don't want to learn a load of terminal commands, I want a rich graphical user interface to do those things for me.
What do you expect?
Ok, if your main intent is to keep Linux as a linux user only environment with nobody else making the switch from windows, the above method is a sure way to go.
When a system is advertised in so many circles as a replacement to windows, and BETTER, then what you'll end up with is a lot of people expecting it to pretty much act similar to windows in all the ways that matter.
Typing out sudo commands with no explanation about what that command actually means is paramount to handing out a password with no idea of what its for or why it's needed.
But your heart is in the right place.
I for one, intend to pursue the easy GUI based methods until I find all the ones that perform the functions that relate directly to similar windows functions.

Bravo.  I agree to a certain extent, certainly with your sentiment in opening up the O/S to the LeyUser.
There are those that are happy to attempt these commands, but when posting I have noticed a lack of annotation, so you don't know what part of the command does what. So whilst you get the knowledge to help fix your immediat problem, you don't gain the knowledge to apply this to different situations.
Bear in mind that even in XP there are times when it's easier to drop to command line. (IPCONFIG, NBTSTAT, etc) This will come in time, and I'm not sure that the main bulk of the linux community is appreciative of how much handholding a large portion of Windows users need, and get!
There are huge swathes, generations of windows users who don't know how to zip, or unzip files, even with an interface as simple as XP, or Winzip.  Based on this, do we really think they are going to readily install applications from a command line.

---

### Post by otterstrom on 2007-06-14
Hi

I am having a similar problem. I am very new to Linux and recently installed a dual boot with Ubuntu and Windows XP. I also recently put together an external hardrive and it is formated using NTFS. I tried using the suggestions listed above in order to get permissions set correctly so that I can read and write to my external HD. I began with the command terminal and was unsuccessful so I tried installing the NTFS Config program with the Add/Remove feature. 

Somehow I managed to mount my Windows XP partition and there is now an icon on my Linux Desktop that allows me to read files on my XP partition (I accidentally named this "External Hardrive" because I did not realize what I was doing). Now I am unable to undo what I have done and I still have not been able to change the permissions on the External HD to allow me to write to it. (I tried plugging the External HD into a windows machine and ejecting it properly and then I plugged back into Ubuntu and ran the NTFS Config program and that did not work)

Help Please!

I would at least like to undo what I did that created the icon on my desktop which allows me to access my Windows XP partition.

---

