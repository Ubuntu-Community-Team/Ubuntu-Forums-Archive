---
title: "Change write permission of mounted external usb hard drive"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by VicVega on 2005-11-10
Hi,
	         I am brand new to Ubuntu and Linux. I need to change permission settings on my external usb hard drive. It is a pluged usb drive that I want to use for my Home and as a backup, I do not always have it turned on. It has 3 partitions on it , about 90Gb of it is formatted ext3. the access path in disk manager shows /media/usbdisk as /dev/sdb3 . I also have an NTFS partition on this drive that I can read just fine. It mounts fine and I see the contents of the ext3 volume (lost&found) but I cannot read or write to it. The permission in properties for the drive shows both the file owner and file group as root also in Text view: drwxr-xr-x and Number view: 755 . It says: You are not the owner, so you can't change these permissions. I need to have write permission on this drive.

	        I have tried editing /etc/fstab without success, but I am not really sure I know what I'm doing. I have searched goggle and the forums and have not found the answer. I realize that I cannot write to the NTFS but I do need to write to the ext3 partition. I hope someone will take pity on me and point me in the right direction as I really need to solve this.

Thanks,
Vic

---

### Post by teaker1s on 2005-11-10
chmod -R +w /path/to/folder/

[http://catcode.com/teachmod/]("http://catcode.com/teachmod/")
will give you the idea or someone who uses terminal more than me will tell you more

---

### Post by patrick295767 on 2005-11-10
Maybe u'll need to use a  startup script ...
(as I do for my external usb drive)
   
[http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

---

### Post by VicVega on 2005-11-10
[INDENT]Thank you to teaker1s and patrick295767 for your responses. I have done a lot of reading since your posts. I grasp the part about needing to define permissions. I think we are on the right track .... but I still have not discovered a solution. [/INDENT]

I have not used chmod on anything yet because I am not sure exactly what to use it on. 

**Do I chmod:**
		[INDENT]1. /dev/sdb   -   my entire external drive[/INDENT]
                [INDENT]2. /dev/.static/dev/sdb3   -   the ext3 partition on the external drive[/INDENT]

		[INDENT]3. /media/usbdisk   -   the access path listed in Disk Manager for the ext3 partition[/INDENT]

		[INDENT]4. Some other directory or file[/INDENT]

[INDENT]I hope I am not making this more dificult than it needs to be. I am just a little gun shy after messing up my original Breezy install (not knowing how to recover) and having to do a fresh install last night. [/INDENT]

Any help in solving this issue is greatly appreciated. 

Thanks,
Vic

---

### Post by gord on 2005-11-10
i personally would do it to /media/usbdisk i don't think doing anything to the /dev's will work

---

### Post by VicVega on 2005-11-12
As a result of the responses here I believe I have resolved the issue of writing files to my external drive. Thanks for pointing me in the right direction. I did a lot of reading/googling and chose a direction to take.

I am new to Linux so if I misspeak or refer to something incorrectly please feel free to point it out. What worked for me was to change the ownership of the mount point of the ext3 partition on the drive. I changed it from root:root to root:<user> using the chown command. My target partition was located at media/usbdisk. I needed full access to /usbdisk but did not want change default setting for /media. I don't recommend doing this unless you do some background reading on the commands or get advice from someone more experienced than myself. This is what I did.

[LIST=1]
[*]Open terminal
[*]**cd /media**
[*](Login as root)  **sudo su**
[*](type)  **chown -R root:<user> /<usbdisk>**
[*](type)  **chmod g+w <usbdisk>**
[*](logout of root)  **exit**
[/LIST]

[INDENT]***note** -	remove **< >**  <user> = substitute your user name
		    <usbdisk> = substitute your actual file or folder name.
 [/INDENT]
 
If I understand this correctly, doing this gave me group privileges and added the ability to write files to this partition. It changed ownership of /usbdisk from root:root to root:<user> (substitute your user name for <user>). The chmod command added write permission to the group <user> (it already had read and execute) . I can now add files and folders to this drive.

For now this seems to do what I need. I may have overlooked something or there may be a better way to do this. If so, please post the details.

I really do appreciate the help that the Ubuntu forums provide and all of the assistance available here.

Thanks,
Vic

---

### Post by xurizaemon on 2006-01-27
This page gave me the answer I wanted:

[http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.shtml](http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.shtml)

I've already configured udev to give my external disk the imaginative name of "usbdisk". This means I automagically get a /dev/usbdisk and a /media/usbdisk when I plug it in; however it was annoyingly rwx------ to the user mounting it, meaning I couldn't connect and use my MP3s unless I used the same desktop user on my (K)Ubuntu box.

Here's the amazing udev config I achieved this with. Your device serial will differ.

```
# Mount datalink device on /media/usbdisk
BUS=="usb", SYSFS{serial}=="DEF107727402", KERNEL="sd?1", NAME="%k", SYMLINK="usbdisk"
```

Because I knew this was all flash udev stuff, I figured the answer wasn't in fstab (cos it requires a specific mount device, right, and all I knew was the USB disk appeared somewhere in /dev/sd?1 according to udev.)

But the link above gave me the clue I needed: the device name and mount point are dynamically generated, so I can use a "static" fstab entry just fine.

```
/dev/usbdisk    /media/usbdisk  auto    users,gid=users,umask=0002,defaults
```

That worked straight away, though the above gives you GROUP access to all members of "USERS" group. If you want access for everyone (it's just a big disk full'o'mp3s, right?) then make it umask=0000 above.

Well, I'm sorted. But finding this took longer than I thought it oughta! Silly me :)

*cough* KEYWORD ATTACK: external usb drive disk permission read write shared

---

### Post by rts on 2006-04-07
None of these solutions are particularly satisfying (think extreme newbie who doesn't want to open a console or edit scripts).

I've also discovered the following:

I have a USB hard drive enclosure and an old disk laying about.

If I format the disk as a Linux filesystem (0x83 partition type, ext2, ext3, etc) then HAL mounts it as root:root.

If I format the disk as any other sort of filesystem (FAT, FAT32, etc) then HAL mounts it as user:user.

So, *somewhere* HAL is distinguishing between Linux filesystems and non-Linux filesystems and choosing to mount as root or not based on that, but damned if I can find where!  I've been poking in /etc/hal/ and /usr/share/hal, but to no avail.

If anyone knows the answer to where HAL makes this determination, I'd sure be interested.

Unless there is some compelling security or other reason that I'm not thiking of, future Ubuntu versions should probably make it so that Linux filesystems get mounted as user:user.

---

### Post by fopetesl on 2006-07-01
xurizaemon: As a newbie I find your description confusing, e.g.> I've already configured udev to give my external disk the imaginative name of "usbdisk". This means I automagically get a /dev/usbdisk and a /media/usbdisk when I plug it inHow do you get udev(?) to automagically create /media/usbdisk when you plug it in?
My system (Breezy) creates /media/USB DISK/ 'automagically' with the wrong permissions so I cannot recognise its existence from a php script.
If I could get udev(?) to automagically create a known directory with, say, 777 permission ... YAY!
Of course I could edit udev.rules as you have done but where do you derive the SYSFS{serial}=="DEF107727402" code from?](*,)

---

### Post by jimbo99 on 2007-06-12
I was reading this thread because I too have problems with USB HDD in external enclosures being mounted so that everyone can write to them.

I was reading this thread and thought to myself.  These guys are clueless.  I know that's not true but I can't understand how on earth you can't seem to give this guy a simple answer.

He has an external HDD it is USB it is mounted and formatted in ext2/3.  He wants everyone to be able to write to it.  Now.  Keep it simple.  Give him the command to make that happen without any scripts, with little or no modification to files without having to load extra programs.

He simply wants to write to the ext2/3 formatted partition that is made available through a USB enclosure for a spare drive he has.  How hard can that be?

---

### Post by hamishau on 2007-08-26
Hi all

OK, so I had this problem too. Had a 120 GB SATA drive which I put in a USB enclosure and formatted it with GParted. However, I also couldn't write to it. I am using Ubuntu 7.04, and it was mounted as /media/disk, with root:root, etc, same as the above posts.

My solution:
1. Backup all data on the drive as you will be formatting it again
2. In a terminal, type in "fdisk -l" to find out where the drive is. Mine was /dev/sda1
3. Type in mkfs.ext3 -L <disklabel> /dev/sda1 (where <disklabel> is what you want to call the disk. I used SATA120, so the full command I used was mkfs.ext3 -L SATA120 /dev/sda1)

This took about 60 seconds for me, and I had a newly formatted EXT3 disk.

Now, the moment of truth. Turn it off and then back on again, and for me it mounted as /media/SATA120, with ALL THE CORRECT USER & GROUP PERMISSIONS!!!

I think that the default label for GParted to use is "disk" and I couldn't find a way to change it without resorting to the command line :-( I think that Ubuntu treats anything called "disk" differently from another label. Especially as I have previously had other devices with the label "disk", so it might just have had some confusion.

Anyway, all good now, and I hope that this benefits some others :-)

Hamish

---

### Post by skemerkelkie on 2007-08-26
I have an external 250 Gig drive in ntfs, and am having the same problem. I can read from it but not write, and also get the grayed out permissions tab. I tried the following 6 steps: but cannot log in as root in step 3 . I get the 'autentication failure, sorry' message. I do not have sufficient space to back up and format the drive.

1. Open terminal
   2. cd /media
   3. (Login as root) sudo su
   4. (type) chown -R root:<user> /<usbdisk>
   5. (type) chmod g+w <usbdisk>
   6. (logout of root) exit

---

### Post by Endolith on 2007-11-08
> **jimbo99 said:**
> I was reading this thread and thought to myself.  These guys are clueless.  I know that's not true but I can't understand how on earth you can't seem to give this guy a simple answer.

Agreed 100%.

Q: "How do I view a web page?"

A: "Well, start by opening a terminal...."

> **hamishau said:**
> 1. Backup all data on the drive as you will be formatting it again

...

I think that the default label for GParted to use is "disk" and I couldn't find a way to change it without resorting to the command line :-( I think that Ubuntu treats anything called "disk" differently from another label. Especially as I have previously had other devices with the label "disk", so it might just have had some confusion.

Reformat the drive???  Surely there's an easier way.  You can't just re-label the partition?

---

### Post by jollo on 2007-12-04
Hi everybody.

I came across this thread as I was having the same problem myself. I got it working, so I thought I'd throw in my 2p:

Relabeling the volume: no use, since automount does *not* bother with labels when assigning permissions, thankfully :) Besides, reformatting is a little overkill if you just wish to change a volume label: try ```
tune2fs -L volume-name device
``` instead.

Configuring udev and fstab to recognise the drive: works for permissions but you loose the automount feature for plug-in external usb devices, and that's not what I wanted...

The right answer is the very first  given in this thread: just change permissions to the mount point, for example ```
chmod -R +w /media/usbdrive
``` If the filesystem is ext2/ext3, the permission flags are written on the fs so they will stick regardless of the mount point (and, more to the point, you'll get the permissions 'automagically' every time you plug the drive in).

Hope this helps. Take care!

---

### Post by capnlester on 2008-01-07
i got my usb drive to work, combining sugestions from several threads, running hippo version.
first i did     
sudo bash                                 to become root

cd to media                           my drive was just labeled disk

sudo chown -R (username) disk
sudo chmod 777 disk

and now i own the drive and able to copy to it

Thanks
  Lester

---

### Post by free_flyer on 2008-01-30
I just found an 'easy' way. if you type ....   

"sudo nautilus" into the terminal
then you can right click on the drive, go to the permission tab and change the owner to your account - easy!

---

### Post by dryder on 2008-03-07
> I just found an 'easy' way. if you type ....

"sudo nautilus" into the terminal
then you can right click on the drive, go to the permission tab and change the owner to your account - easy!No you can't - not on all USB drives - a Seagate FreeAgent Drive simply reverts immediately to root.

David

---

### Post by emmerich on 2008-03-08
Hello. I am having issues writing to a Maxtor USB drive and have done everything in this thread short of reformating but still can't write to it. Should I try to reformat? Do I have other options here?

---

### Post by jollo on 2008-03-08
Hi emmerich! I don't presume I'm going to be able to solve anyone else's problems (I'm still stuck with mine) but I'll give it a try.

What fileystem is your externa USB dirve formatted with? A quick way to find out is System > Administration > GNOME Patition Editor (or sudo gparted from the command line).

---

