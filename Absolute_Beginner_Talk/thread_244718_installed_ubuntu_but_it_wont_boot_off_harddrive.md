---
title: "installed ubuntu but it wont boot off harddrive"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by mr_tubaman2002 on 2006-08-26
I ran the ubuntu live CD (downloaded iso and burned to CD) and used the install program included with the CD but now when i try to boot up off of the hard drive this message appears

GRUB loading, please wait.....
Error 18

from this point the computer does nothing.  I am running a old computer with 512mb ram, intel pentium II 700mega hertz, its just a computer that i threw together with some old parts i found so its not a name brand comp.  
 
i would love any help anyone can give me, thank you

PS. this it the first time i have used linux (besides live CD versions) so if there is and technical stuff i might need a more step by step guide.

---

### Post by catlett on 2006-08-26
Is there another OS on the drive? Are trying to dual boot?
If this drive is entirely for ubuntu then run the installer again. You may want to re-burn the iso to disk at a slower speed to reduce tyhe chance of a bad burn.
If you have access to another computer, you may want to downl;oad another iso. You should always check the integrity of a download with a mid5sum test. This way you know for sure you have a good iso to begin with. Next time you download refer to this guide on how to verify from windows [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

Actually the site has lots of great information. It is maintained by Aysiu who is an "icon" of the ubuntu forum. Here is the link [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

So if you are dual booting, post back yes and detail the way your drive is partitioned. i.e. XP on 20gb ntfs. The installer made 2 partitions for ubuntu, 1 gb swap and 10 gb ext3. If you do not know how the drive looks, boot into the live cd session and go to Sytem<Adminikstration< gnome partition editor. That is gparted a partitioning aplication. It will give you a graph of your drive.

I was going to wait for your reply about dual bootinmg because I didn't want to make the post confusing but I'll explain why I am curious.
> 6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 
That is an explanation of error 18. It occurs when you try to boot an OS outside the boot sector of your drive. It doesn't occur with new machine but where you said yours was old. This should only be happening to you if Windows is at the front of the drive and you are trying to install behind it. If you are giving the whole drive to ubuntu, this should not happen.

FYI, your computer has plenty of resources to run ubuntu.

---

### Post by mr_tubaman2002 on 2006-08-26
There is only ubuntu on the drive, i formated the entire drive with the live cd and installed ubuntu.  I am using a western digital 160GB 7200RPM hard drive.  my drive is partitioned as follows:

**Partition              Filesystem           size**

/dev/hdc1                 ext3                 148.34 GB
/dev/hdc2                 extended             729.52 MB
   /dev/hdc5              linux-swap           729.49 MB
 
 i did use both the programs that catlett suggested and my iso was good and i burned the cd a 4x so it is good.  I download the iso from one of the sites linked from ubuntu.com (dont remember which one) so it is most likely a good copy.

Thank you for your help

---

### Post by catlett on 2006-08-26
Try running the installation one more time. Everything is setup correctly, it should install without an issue.
Run the installation again and see what happens. Since you are only using the drive for ubuntu and you just installed, you won't be loosing any data, only time.
If it fails post the point at which it apears to stop installing.

---

### Post by NetworkGuy on 2006-08-26
If your system is old as I read above..

You may need to create a /boot partition.   I remember having to do this with older computers and bigger than 8GB HD's.

100MB minimum is what used to be the standard.

It works, but it's not preferred nowadays.

---

### Post by mr_tubaman2002 on 2006-08-26
my computer knowledge is limited, how do i create a /boot partition.  I have never had a problem installing i just got that error 18 thing, i am going to reinstall but this time i will partition a smaller part of the drive to see if that helps a little.

---

### Post by NetworkGuy on 2006-08-26
You need to custom partition your hard drive.   Create a 200MB partition for /boot, a 768MB partition for linux-swap and the remainder for /

Take your time through the partitioner and you should be fine.

---

### Post by mr_tubaman2002 on 2006-08-27
ok im trying this again and im hopeing that just leaving things alone for a while would help me think a little better.  the problem im having now is that when i create a new partition i have to choose what type of filesystem to make it, i know to make the / ext3 and the swap a linux-swap filesystem but what i need to know is what the make the /boot.  every time i try now i get a message that says there is no OS.  i have done eveything stated above i just need to know how to do the /boot.

---

### Post by jerry_c on 2006-08-27
The expert who set my /boot partition a couple years ago used ext2. As I understand it, ext2 is an older style file system that is more universally readable. There won't be much in your /boot partition, anyway. Good luck.

---

### Post by NetworkGuy on 2006-08-27
The /boot partition I used to make was ext3.  Either filesystem will work.

---

### Post by mr_tubaman2002 on 2006-08-27
I just want to say thank you to all the guys that help me get going i finally got ubuntu to install and run (i tried about 9 times).  I made a /boot at the begining of the drive at 200 MB, 1GB worth of linux-swap at the end of the drive, and the rest of the drive in the middle is the /.  the /boot ran fine as soon as i made it a ext2 filesystem, and i know my linux-swap is really large but i figured that for now it wouldnt hurt to have pleanty of room.

Thanks everyone for the help!!!!!!!
Now I get to go see whatelse I can mess up??????

---

### Post by catlett on 2006-08-27
It appears the error 18 was correct. The boot folder was beyond the bios limit. This seems plausible if we are dealing with a 512mb limit. Do you suppose the ubuntu installer made a swap larger than 512mb and put it at the front of the drive? Effectively putting the boot folder beyond the 512mb limit.
I first assumed only another OS installation would cause this but since Network Guy's solution worked, the issue has to be location of boot. The only thing I can think of is a swap partition greater than 512mb being before the  root partition.
Does anyone know how the installer creates and positions the swap and root partitions on an installation where the installer is given the entire drive? Just curious if this is what caused the boot issue.

---

### Post by NetworkGuy on 2006-08-27
Catlett, Check out this site
[http://www.linuxhq.com/guides/SAG/x885.html](http://www.linuxhq.com/guides/SAG/x885.html)   (Near the bottom --> Partitioning a hard disk)

It's looks to be more of a cylinder thing.  The booting partition can not extend past the 1023 or 1024th cylinder on the hard drive.

It's starting to come back to me now..  :)

---

### Post by catlett on 2006-08-27
> **NetworkGuy said:**
> Catlett, Check out this site
[http://www.linuxhq.com/guides/SAG/x885.html](http://www.linuxhq.com/guides/SAG/x885.html)   (Near the bottom --> Partitioning a hard disk)

It's looks to be more of a cylinder thing.  The booting partition can not extend past the 1023 or 1024th cylinder on the hard drive.

It's starting to come back to me now..  :)

Thanks for the link. Now I see why a boot partition was imperative in early linux use. It's amazing how fast computer hardware changes. The writer of that manual had to have the latest hardware (I would assume if you are writing a system administrators manual that you had the latest but I could be wrong). Anyways a few pages into the manual he is describing a partitioning scheme and he is using his upgrade to a larger hard driuve as an example. He is going from a 109mb drive to a 330mb drive. Here is his allocation
```
5 MB	root filesystem
10 MB	swap partition
180 MB	/usr filesystem
120 MB	/home filesystem
15 MB	scratch partition
```
That amazes me. I have multiple partitions so I made my root 5gb and I was debating about making it bigger :D 
Thanks for the link and the info about boot in old hardware. I try to keep as much info on hand as I can about boot errors because they are a common occurence. Now I know to ask how old is their hardware from the beginning.

---

### Post by finferflu on 2006-09-03
Sorry for my stupid question, but I'm facing the same problem on an old machine (my mother's pc - I'm actually trying a phone installation, I thought it would have been nice and easy with Xubuntu, but appearently the old thingy doesn't want to collaborate)...

Should I set the /boot partition as primary or logical? If primary, shall I set it as bootable? And which order is preferred?

Thanks a lot for your useful hints!

---

### Post by jerry_c on 2006-09-03
It depends upon whether or not you're dual booting. If you're using only linux, it doesn't matter whether or not you use primary or logical for /boot because linux reads any partition. If you're using windows as well, here's what I'd suggest, and why:

1: windows boot sector - windows expects this to be first, particularly in recovery mode

2: windows - windows expects this here and sometimes has a problem finding itself in the extended partition

3: linux swap - windows will sometimes write beyond its partition boundaries, and you don't want it erasing part of your linux distro or data

4: extended partition pointers

5-8, in any order:

_: linux /boot partition

_: linux distro 1

_: linux distro 2 - having two distro partitions allows you to install another distro without wiping out your old one. If, for some reason, your new distro doesn't work out, you can always just boot to your old distro. It also makes it easy to copy config files for your favorite programs from your old distro to your new distro.

_: /home - this is where you keep your data and user settings. When you install another distro, this stays.

Some people also suggest a separate /var partition. If you store much there, you might want to consider that, too.
 
Good luck.

---

### Post by finferflu on 2006-09-03
Thanks, it makes sense now.. I'm installing only Linux, no dual booting, but the other information can be useful for the future, and maybe also for somebody else.

Thank you!

--UPDATE--

Yeah! It worked, I've been able to run Xubuntu! Thanks a lot guys! :)

---

