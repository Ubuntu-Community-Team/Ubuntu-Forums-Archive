---
title: "A little guidance for new user"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by oldcotton1 on 2006-12-31
Hello all,

I am a complete newbie to Ubuntu and linux in general.  I have tons of experience in DOS / Windows based workstations and servers and decided it was time to take up a new challenge.

Well a challenge it is.  I have a test bed machine consisting of a P3 600 processor, 512MB RAM, 2X 40 GB Samsung HDs, (set as master and slave on IDE 1) 16X DVD ROM as Master on IDE 2 and a 32XCDRW as Slave on that bus. 3.5 Floppy drive.  Video is ATI Rage 128 AGP, 3Com NIC.

Through the 6.10 Edgy Eft Live CD in the DVD drive and let it load up and then hit the install icon.  Just kept clicking forward.  So far so go and I liked the simplicity.

Once it had rebooted and told me there were updates, I let it run throught the 82 updates and installs.  I then started looking around and playing .  First thing I did was open Computer and saw that I had a drive called Filesystem , a DVD/CD ROM drive, A CDRW and TWO Floppy drives.  One called Floppy the other Floppy 1.  Seemed strange.  I tired opening Floppy and was told it needed a disc which I provided.  Tried opened Floppy 1 and was told could not mount - not block device or something of that nature.

The second hard drive was nowhere to be seen.  Well I started reading and searching came across some excellent tutorials, and quickly realized that there were many things one can't do from the graphical interface and that command line was the way to go.  Learned about sudo etc and had some fun trying to fdisk the 2nd drive (It doesn't like the  number of cylinders), mkfs.ext 3, elabel etc all to no avail.  I reread the official and unofficial user guides again without a great deal of success ](*,) .  I have blown away the install at least a half dozen times by now still trying to get the second drive to show and then set it as my data drive.  Several times in the instructions it states to System Administration Disk.  Well in my install there is no disk listed under the admin functions.  Downloaded and ran Gparted now have the drive partitioned and formated as ext3!  However if I switch to terminal mode fdisk will not show its properties.  Just the long message about the number of cylinders and that though it might work older versions of DOS etc may not be able to access data hit M for command menu.

Now I am sure this is a combination of not seeing the forest for the trees and being somewhat visually impaired in one eye and not seeing well out the other.  Have I missed something terribly obvious?  Is it time to grab the Linux for Dummies book again and relearn "DOS with Degree"?  Would some one kindly guide me to the place with the answers.

From everything I've read about this OS I'm still looking forward to working with it and once I get this test install working; playing with an old server and laptop that are kicking around here.

Looking forward to participating in these forums and hopefully one day being able to offer advice to other newcomers.

Sorry for the lengthy dissertation :-)

---

### Post by bulldog on 2006-12-31
Is the second disk properly recognized in the BIOS?
Because if fdisk can't see it there should be something wrong.

The mounting is done in fstab,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by oldcotton1 on 2006-12-31
> **bulldog said:**
> Is the second disk properly recognized in the BIOS?
Because if fdisk can't see it there should be something wrong.

The mounting is done in fstab,

[http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572](http://www.ubuntuforums.org/showthread.php?p=1837572#post1837572)

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

Hi and thanks for the quick reply.  Yes the drive shows up fine in the bios.  If I use a DOS boot disk with MS fdisk, it sees it  allows me to partition it and I can even format it FAT32 if I so choose.

I have tried the instructions exactly as listed in this article ([http://www.cyberciti.biz/faq/format-add-new-sata-scsi-hard-disk-for-backup/](http://www.cyberciti.biz/faq/format-add-new-sata-scsi-hard-disk-for-backup/)) and all goes well until I attempt to mount then it states device not found. I mad sure i had the correct device /dev/hdb (even tried hdb1)    Did a reboot after that and the OS hung and came up to the command line indicating that there was no device by that name. 

I failed to mention in my original post this is a single boot machine so it is not related to a dual boot issue.  Both drives have been cleared of any data.  My next step is to use something like Microsope and low level format the drive just to be sure.

As there is no data on the machine I can blow it aways as often as required so any an all suggestions are welcome .  Just love these 90 degree learning curves;)

---

### Post by handy on 2006-12-31
Hang in there, this is the hardest part of the whole Ubuntu (linux) experience...  Looping the loop learning curves become history, & you have this amazing community behind you.  Wellcome :KS 

The offending drive = **hdb1**

Is it formatted, & if so which file system?

We will have to get these details so that we can edit your **/etc/fstab** file, then your system will recognise the drive.

Also, the help you were reading was Red Hat oriented, there are differences in Ubuntu, I would suggest that you only use Ubuntu help at this stage of the game...

---

### Post by handy on 2006-12-31
If your drive is formatted to **ext3** file system, the Ubuntu default, then you could try adding the following line to your **/etc/fstab** file, using the **Text Editor** from the **Applications / Accessories** ***Menu***:

**/dev/hdb1       /data           ext3    defaults        0       2**

You must also make a directory so:

**/media/data**

Quickest way to create the **/media/*_data_*** directory directly is via the Terminal:

**sudo mkdir /media/data**

After having done the 2 steps above, enter the following in the Terminal:

**sudo mount -a**

If nothing unforeseen raises it's head you should now have access to your 2nd drive called **/data**

---

### Post by oldcotton1 on 2006-12-31
> **handy said:**
> If your drive is formatted to **ext3** file system, the Ubuntu default, then you could try adding the following line to your **/etc/fstab** file, using the **Text Editor** from the **Applications / Accessories** ***Menu***:

**/dev/hdb1       /data           ext3    defaults        0       2**

You must also make a directory so:

**/media/data**

Quickest way to create the **/media/*_data_*** directory directly is via the Terminal:

**sudo mkdir /media/data**

After having done the 2 steps above, enter the following in the Terminal:

**sudo mount -a**

If nothing unforeseen raises it's head you should now have access to your 2nd drive called **/data**


Hi Handy,

Thanks for the words of encouragement and advice.  As soon as the low level format is finished, I'll partition it and format  it (again) as ext3, follow the rest of your advice and see if that takes care of it.

I'll post my results.

---

### Post by handy on 2006-12-31
No worries mate,

If you strike problems, or no one is answering, try searching the forums for **fstab**, you will find more than enough help, this is a very common problem for new linux users, & as stated earlier, the different distributions all have their own flavour, or way of doing things....

& who would expect a new user to know to search for **fstab**! :KS

---

### Post by oldcotton1 on 2006-12-31
Well handy, i followed your directions after doing the low level format.  Or at lest I tried.  Now the problem is that I can not edit /etc/fstab!  It only read only and I do not have permission to change it.

I guess being used to being a sys admin in Win2K / XP environments doesn't help me here.  How the heck to I manage to write to the file.  I tired running sudo gedit in terminal, but that got me no where.

Grrrrr, but still having fun.  So the next battle is getting rights to the files!

BTW fdisk now shows the drive correctly so getting somewhere with that

OK found out about gksudo and open with custom :-)  so now have the fstab edited as follows:

/dev/hdb1 /data ext3 defaults 0 2

problem is now this:

when I do sudo  mount -a  the result is this:

mount: mount point /data does not exist


Well it is now 2007 in my time zone has been for a little while now and it
s been a long day.  Think I'll call it a night an be happy with what I've learned so far.

Happy New Year to all who celebrate such things at this time of the year.

---

### Post by handy on 2006-12-31
Oops, sorry about the sudo bit, I should have told you to enter the following in the Terminal:

**sudo gedit /etc/fstab**

You have make the **/media/*_data_*** directory:

**sudo mkdir /media/data**

Then enter the following in the Terminal:

**sudo mount -a**

Let's know how you go?

---

### Post by oldcotton1 on 2007-01-01
Well I'm finally getting somewhere :) 

I had to modify the fstab line to read :

dev/hdb1 /media/data ext3 defaults 0 2

now it mounts, show up on my desktop and in computer but seems that I can't make new folders in it or save things to it. I wanted to set it up for holding things like downloaded files etc, but just doesn't seem to work (yet)

I'll keep plugging away and learning as i go:-k

---

### Post by oldcotton1 on 2007-01-01
Ah ha - gksudo nautilus and change file permissions.  I think I'm catching on.  Bit of a pain continually haing to switch to root mode, but I like so far :)

---

### Post by smoker on 2007-01-01
> **oldcotton1 said:**
> Ah ha - gksudo nautilus and change file permissions.  I think I'm catching on.  Bit of a pain continually haing to switch to root mode, but I like so far :)

you're doing fine, and pretty soon it will be second nature:D 

welcome to ubuntu:D

btw - there are some scripts on this page you might find usefull
[http://doc.gwos.org/index.php/Nautilus_Scripts](http://doc.gwos.org/index.php/Nautilus_Scripts)

---

### Post by mgmiller on 2007-01-01
Welcome to Ubuntu

Now that you've had all the fun of using the command line for creating your mount points, there is a nice graphical package available that does the same thing for you.
```
sudo apt-get install pysdm
```
It creates the following entry: System>Administration>Storage Device manager

Between gparted and pysdm,  You have a nice GUI way to do this whole procedure.

With your level of expertise, it's probably better that you learned the CLI way of doing this first as it forced you to learn a lot of other things also.  Linux is like that.  You often learn a lot of other things applicable to many other tasks as you climb the learning curve.

---

### Post by smoker on 2007-01-01
hi, mgmiller,

thanks for the info, alas i installed pysdm, but it won't work, i guess maybe cause my drives are sata - app briefly opens and closes with no reason, tried opening through the terminal and got this:

boss@boss-desktop:~$ gksudo pysdm
Not suitable dev for sda
Not suitable dev for sda1
Not suitable dev for sda2
Not suitable dev for sda4
Not suitable dev for sdb
Not suitable dev for sdb1
Not suitable dev for sdb2
Not suitable dev for sdb3
Not suitable dev for sdb4
  File "pysdm.py", line 457, in ?
    main()
  File "pysdm.py", line 452, in main
    main_window = Mainwindow()
  File "pysdm.py", line 47, in __init__
    SimpleGladeApp.__init__(self, path, root, domain, **kwargs)
  File "/usr/share/pysdm/SimpleGladeApp.py", line 108, in __init__
    self.new()
  File "pysdm.py", line 64, in new
    self.refresh_partitions(self, None)
  File "pysdm.py", line 219, in refresh_partitions
    if is_mountable(self.blocks[partition].dev):
AttributeError: Block instance has no attribute 'dev'
boss@boss-desktop:~$

not sure what any of that means, though, as i said, my drives are sata, so maybe that is the reason.
EDIT: just found out i need a later version of gnome apparently! - will have to upgrade.

---

### Post by oldcotton1 on 2007-01-01
Thanks to all who have offered advice.  I'll take a look at the graphical interface mentioned above.  I certainly don't mind using the command line.  Brings back to when I first started playing with computers in the early 80s.  Had to write the program before you could get the good old ZX80 to even do anything. Have become slightly spoiled with all the point and click stuff courtesy of Mr "640K of RAM is enough for anybody" ;) 

I have to admit I like using my brain to work things out.

Now that I have the basics working to my current satisfaction it is time to tackle printing to the network printers, seeing just what i can do with running VM etc. I think I found the fun in computing again!

---

### Post by Lord Illidan on 2007-01-01
> **oldcotton1 said:**
> Thanks to all who have offered advice.  I'll take a look at the graphical interface mentioned above.  I certainly don't mind using the command line.  Brings back to when I first started playing with computers in the early 80s.  Had to write the program before you could get the good old ZX80 to even do anything. Have become slightly spoiled with all the point and click stuff courtesy of Mr "640K of RAM is enough for anybody" ;) 

I have to admit I like using my brain to work things out.

Now that I have the basics working to my current satisfaction it is time to tackle printing to the network printers, seeing just what i can do with running VM etc. I think I found the fun in computing again!

Nice to find more users who like tinkering!!!

---

### Post by handy on 2007-01-02
This community makes it so enjoyable, if you are patient there is no problem too big... Someone has the know how & is willing & happy to share... :KS  :cool:  :KS

---

