---
title: "Touchpad and torrents and other things I just don't understand"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by taskenspiller on 2007-05-02
Hi,

I installed Ubuntu (Feisty Fawn) 7.04, and it seems to be working OK. But there are lots of things I just don't know how to do:

One: Download torrents.
I download the torrent file OK, but when I try to open the file, the erroBitTorrent gives me is: "Read only file system: /media/sda5/torrentfilename.avi"

Two: Adjust touchpad settings
I want to get rid of the tapping function on my touchpad, but Ubuntu only seems to have settings for a regular mouse. I did some searching and found i needed QSynaptics or something. This webpage [http://qsynaptics.sourceforge.net/help.html](http://qsynaptics.sourceforge.net/help.html) says the file /etc/X11/xorg.conf needs to be edited, but it belongs to /root, and I don't know how to log in as root.

Looks like the problems might be related, I'm guessing I need to log in as admin/root or whatever?

Other things: 
Where do the programs "reside"? I wanted to choose Azureus to open the torrent ("open with..." in Firefox), but could not find it. I have downloaded Azureus, and I can open it with "Run Application"
How do I delete partitions, what kind of file system should the partitions be, and how do I know what partition has the OS on it? I was able to keep the partition I wanted when formatting, but ended up with a total of three or four partitions, when I only had two (one with OS and one for storage) in the Windows days.

I'm sorry for the long post, but I've been reading around some (here and other places), but it feels like my questions are so basic/stupid that they're not answered anywhere. Any help with my problems would be nice, thanks!

---

### Post by useResa on 2007-05-02
> **taskenspiller said:**
> 
Two: Adjust touchpad settings
I want to get rid of the tapping function on my touchpad, but Ubuntu only seems to have settings for a regular mouse. I did some searching and found i needed QSynaptics or something. This webpage [http://qsynaptics.sourceforge.net/help.html](http://qsynaptics.sourceforge.net/help.html) says the file /etc/X11/xorg.conf needs to be edited, but it belongs to /root, and I don't know how to log in as root.

Looks like the problems might be related, I'm guessing I need to log in as admin/root or whatever?
Don't know about your other questions, but you can edit the file "acting as root" by using the following command in a terminal (Applications --> Accessories --> Terminal)
```
gksudo gedit /etc/X11/xorg.conf
```However, I do advise you to make a backup copy of your xorg.conf file so that you can restore it should things not work as expected.
You can make a copy by giving the following command in the terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupfile
```Of course you can change the location and name of the backup file ([COLOR=Blue]/etc/X11/xorg.conf.backupfile[/COLOR] in the above command) as you like.

Hope that this at least will help you with your touchpad issue.

---

### Post by starcraft.man on 2007-05-02
Use Ktorrent for Torrents, its much better than the standard. I even prefer it over azureus. The error you gave must mean your torrent client set itself to download into a read only drive (maybe an NTFS partition). Go into the settings of whichever torrent client you use (In Ktorrent, settings is at the top > select configure ktorrent, go to General tab and folders are at the top, set them wherever you like :) )

I don't know how to do your touch pad, search forums or google. >.>

If you want to change the default open with application, right click on a torrent, choose properties, then go to the "Open With" tab and select the one you want from the list.

To delete a partition and manager others, you need gparted. Its the gnome partition editor. Its installed into the live cd or alternate CD you used to install. You can get a simple version [here.]("http://gparted.sourceforge.net/livecd.php") 

Hope that answers most of your questions. Read documentation for gparted before using it, lest you destroy a partition you want.

---

### Post by taskenspiller on 2007-05-03
> **useResa said:**
> Don't know about your other questions, but you can edit the file "acting as root" by using the following command in a terminal (Applications --> Accessories --> Terminal)
```
gksudo gedit /etc/X11/xorg.conf
```However, I do advise you to make a backup copy of your xorg.conf file so that you can restore it should things not work as expected.
You can make a copy by giving the following command in the terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupfile
```Of course you can change the location and name of the backup file ([COLOR=Blue]/etc/X11/xorg.conf.backupfile[/COLOR] in the above command) as you like.

Hope that this at least will help you with your touchpad issue.

Thanks! That solved it. :)

My other problem(s):
When opening a .torrent file in FireFox, the Open with button only shows BitTorrent. I can press "Other..." but I don't know where Azureus is located. The only way for me to open the .torrent in Azureus is if i download the .torrent file, then start Azureus and open the file from the program. How can I find Azureus through Firefox?

That's not the real problem, though. When I open the file, Azureus tells me the place I want to store the .avi file is a Read Only File-System. This partition is the place where I want to save my media files, so how do I change the setting?

The location is /media/sda5/film/torrentname.avi

In /media, there is a folder called /sda3. It seems to hold everything the / folder (the main folder?) holds, like /media, /root, /boot, etc. Can I delete this, somehow? I think it is mounted as a partition, but it's not being used. (This may be why I get several Ubuntus to choose from everytime I boot.)

Thanks for the help so far.

---

### Post by tact on 2007-05-03
Hi there taskenspiller

don't worry about asking what seems to be overly "beginner" questions.  its cool here.  you are in the right place.

it is good that you realise that you are not silly - just unfamiliar with things in this new environment.

Here follows a little more "orientation" advice....
regarding the torrent thing refusing to let you use a directory off /media...   in Linux every user you create on your system has their own "home" directories.

All the home directories are in ... yes..   /home.  Individual user home directories are named after their username for example:
/home/username1
/home/username2
etc.

linux is BIG on each user having ownership of their own files - and perhaps being barred from doing more than reading other people's files.  

If you have not already created additional users there will be 2 users defined on your linux system already - yourself and "root".

/media is owned by root, not you,  and if you can see it at all its because root permitted you to do so.  if its read only thats because root made it so.

"root" is the superuser account, or administrator account, of your system.  You can "become" root temporarily by using the "gksudo" or "sudo" command.   

Please note tho it is a VERY good practice to organise all your files and directories inside your own "home" directory (i.e. /home/your_username).     So create an appropriate named directory under your home directory and confiigure your torrent program to use it.

This is not windows land where people and programs can just create directories and leave files scattered all over the file system.  Its more organised and file ownership/permissions are enforced so that users cannot damage system files or other people's files.

its a feature not a problem once you learn to appreciate it.  :)

---

### Post by taskenspiller on 2007-05-03
Hi,

Thanks for giving me some of the basic information i obviously need :)
So, I am stuck with a folder (/media/sd5/) with all my media, that I should somehow transfer to my /home/username folder. How do I do this?

/root seems like a badass.

Btw, I would like to have a partition for all my media files, and another for the operating system, so I can format the operating system partition without loosing my media files. The computer was organized this way in the win XP days, and its the "other" partition (not the OS partition) that has become /media/sd5/.

---

### Post by Skrynesaver on 2007-05-03
/media/sda5 is a filesystem ( a usb disk formated by XP ?)
Enter the following in a terminal window
```
mkdir ~/data
cp /media/sda5/<torrent_name> ~/data/

```
the ~/ notation is read by the shell as wherever your home directory is
This makes a directory called data and under your home directory
Then copies the torrent over to your home directory
However if the filesystem is readonly you may not have downloaded it as successfully as you think.
ls -lh /media/sda5/torrentfile.avi to see what size the file is

---

### Post by Ripfox on 2007-05-03
Download Transmission for bittorrent if you want something functional and light...when you right click on a torrent file after you download transmission will be listed as an option.

[http://ubuntuforums.org/attachment.php?attachmentid=31467&d=1178055899](http://ubuntuforums.org/attachment.php?attachmentid=31467&d=1178055899)

---

### Post by Inxsible on 2007-05-03
> **taskenspiller said:**
> Hi,
 
I installed Ubuntu (Feisty Fawn) 7.04, and it seems to be working OK. But there are lots of things I just don't know how to do:
 
One: Download torrents.
I download the torrent file OK, but when I try to open the file, the erroBitTorrent gives me is: "Read only file system: /media/sda5/torrentfilename.avi"
 
Two: Adjust touchpad settings
I want to get rid of the tapping function on my touchpad, but Ubuntu only seems to have settings for a regular mouse. I did some searching and found i needed QSynaptics or something. This webpage [http://qsynaptics.sourceforge.net/help.html](http://qsynaptics.sourceforge.net/help.html) says the file /etc/X11/xorg.conf needs to be edited, but it belongs to /root, and I don't know how to log in as root.
 
Looks like the problems might be related, I'm guessing I need to log in as admin/root or whatever?
 
Other things: 
Where do the programs "reside"? I wanted to choose Azureus to open the torrent ("open with..." in Firefox), but could not find it. I have downloaded Azureus, and I can open it with "Run Application"
How do I delete partitions, what kind of file system should the partitions be, and how do I know what partition has the OS on it? I was able to keep the partition I wanted when formatting, but ended up with a total of three or four partitions, when I only had two (one with OS and one for storage) in the Windows days.
 
I'm sorry for the long post, but I've been reading around some (here and other places), but it feels like my questions are so basic/stupid that they're not answered anywhere. Any help with my problems would be nice, thanks!
 
1) For your first problem you could simply take ownership of the folder/partition where you are trying to store the downloaded .avi file. Note however, that if the download location is a system folder, don't change ownership. I have a separate partition to store data and I know that, that partition will always have only my data. This is how you change ownership
```

sudo chown -R <username> /shared

```
where /shared is the partition that I want to take ownership of and where I will be storing all my downloaded files
 
2) you have already solved that one
 
3)For the Open with in Firefox :
once you get to the dialog you will see a list of programs to use. If you DO NOT see your program (Azureus -in your case), Click on the arrow down at the bottom of the dialog. It says something like 'Use Command' (i think).
 
This will give you a nice text box to type in your command. In all probability your command will be azureus. I have done this with VLC, wherein i typed vlc and it worked. You only will have to do this once.
 
Hope that helps !!

---

### Post by starcraft.man on 2007-05-03
> **ripfox said:**
> Download Transmission for bittorrent if you want something functional and light...when you right click on a torrent file after you download transmission will be listed as an option.

[http://ubuntuforums.org/attachment.php?attachmentid=31467&d=1178055899](http://ubuntuforums.org/attachment.php?attachmentid=31467&d=1178055899)

Oooooh, I never seen that one, will have to try. Thanks, always like to try new clients.

---

### Post by mikewhatever on 2007-05-03
A short answer to all of your questions would be, you learn how to use the new OS for several months.Don't expect to learn or do everything in one day or week. I believe you've already got a lot of real answers from others, so I'll stop here.

---

### Post by tact on 2007-05-04
> **taskenspiller said:**
> Hi,

Thanks for giving me some of the basic information i obviously need :)
So, I am stuck with a folder (/media/sd5/) with all my media, that I should somehow transfer to my /home/username folder. How do I do this?


Is there actually any of your files in /media/sd5?   Pull up a command line "Applications>Accessories>Terminal" and type in 
```
ls -l /media/sd5
```

This is like "dir" in windows-land.  The result will be a list of all the files and directories inside /media/sd5

If there is anything in there that you want to copy into your home directory then you can do something like this:
Create a directory in your home for the files eg. "torrents"
```
mkdir /home/your_username/torrents
```

saving some typing - this does the same thing:
```
mkdir ~/torrents
```

Then copy (all?) the contents of /media/sd5 to /home/your_username/torrents
```
cp /media/sd5/* ~/torrents
```

We can worry about deleting any of your files from /media/sd5 later....  (if you don't own /media/sd5 then you need to slip into a telephone box and come out with your cape and mask as "root" temporarily to do this).

> **taskenspiller said:**
> 
/root seems like a badass.


hehehe ya a real a$$-kicker  :)   But in reality he is you... when you assume your secret identity, mask, cape and all...

> **taskenspiller said:**
> 
Btw, I would like to have a partition for all my media files, and another for the operating system, so I can format the operating system partition without loosing my media files. The computer was organized this way in the win XP days, and its the "other" partition (not the OS partition) that has become /media/sd5/.

This is one for later also...  At some time when you think of doing a re-installation.  At installation time you can do a manual or "advanced" kind of installation and assign totally separate partition for the "/" (root) directory where all the operating system files are.  and more

---

