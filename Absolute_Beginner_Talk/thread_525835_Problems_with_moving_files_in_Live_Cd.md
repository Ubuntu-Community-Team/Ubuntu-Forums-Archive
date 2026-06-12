---
title: "Problems with moving files in Live Cd"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zibeezibeehey on 2007-08-14
While using the live cd I tried to move a bunch of my files to my external hard drive. The live cd sees the hard drive and lets me open it but wont let me move any files to the actual hard drive. It says Error you do not have permissions to write to this folder.

Is there anyway around this because i seem to have a problem thats freakin me out, thanks.

---

### Post by Blutack on 2007-08-14
Can you right click on the drive icon, hit properties and tell us the filesystem?  Should be under the "Volume" tab...

---

### Post by bwtranch on 2007-08-14
Yeah, you have to be root user in the gui and I can't remember that command. You could do it in the CLI with mv or better cp

Edit: Found it gksudo nautilus

I always move or copy in the terminal

---

### Post by zibeezibeehey on 2007-08-14
the file system for my external hard drive is ntfs

---

### Post by zibeezibeehey on 2007-08-14
Im extremly noobie seriously I wish I knew what you meant bwtranch. lol

---

### Post by Blutack on 2007-08-14
Ok, you can't do it.  To move the files you would need the ntfs-3g driver, which lets ubuntu write to ntfs drives.  You can't install this on a live cd because the live cd will loose all its settings when you reboot (which you have to do to apply the changes the ntfs-3g driver makes).  Use Knoppix [http://www.knoppix.net/](http://www.knoppix.net/) instead or reformat the EXTERNAL hard drive to vfat using Gparted (System --> Admin)

---

### Post by zibeezibeehey on 2007-08-14
so knoppix is another distro that will let me use my ntfs harddrive with the live cd. and by vfat do you mean fat32. If i reformat to fat 32 i will have no problem using the live disc to move my files to the external hard drive?

---

### Post by Blutack on 2007-08-14
Yes, you got it.  If you have stuff you want to keep on the NTFS drive you are going to have to use Knoppix or something else with native NTFS writing support.  If not, just reformat the drive to fat32 (which both windows and linux can read and write to).

---

### Post by zibeezibeehey on 2007-08-14
ok now what is gparted how do i find it or whatever to format my external harddrive to fat32

---

### Post by Blutack on 2007-08-14
It is a program.  Click where it says System, then Administration, the GParted.
Open it up and select your external drive from the list - MAKE SURE YOU DON'T SELECT YOUR INTERNAL DRIVE.  Sorry about that but it will wipe everything if you do.  Delete the existing NTFS partition, create a new fat32 partition.  Should do the trick.

---

### Post by zibeezibeehey on 2007-08-14
im guessing that Gparted stands for GNOME Partition Editor

---

### Post by Blutack on 2007-08-14
Yep, sorry.

---

### Post by bwtranch on 2007-08-14
That's Ok. I understand. But, the terminal is really powerful and can do things that the gui has a hard time with. But, see my edit above.
Try this: open a terminal and type / . This is the root folder and everything is under that.
Now type ls <Ret>  This lists the folders (directories) under root
You can now cd (change dir) to any of those like cd /usr <Ret> that's a return
 Example:

jim@jim-desktop:~$ cd /
jim@jim-desktop:/$ ls
bin                                  home            mnt   tmp
boot                                 initrd          opt   usr
cdrom                                initrd.img      proc  var
cupswrapperdcp1000_1.0.2-1_i386.deb  initrd.img.old  root  vmlinuz
cupswrapperDCP1000-1.0.2-1.i386.rpm  lib             sbin  vmlinuz.old
dev                                  lost+found      srv
etc                                  media           sys
jim@jim-desktop:/$ cd /usr
jim@jim-desktop:/usr$ ls
bin  games  include  lib  lib64  local  sbin  share  src  X11R6
jim@jim-desktop:/usr$ cd /games
bash: cd: /games: No such file or directory
jim@jim-desktop:/usr$ cd /usr/games
jim@jim-desktop:/usr/games$ ls
atlantik   gnome-gnuchess  katomic       klickety   kreversi    ktuberling
banner     gnome-sudoku    kbackgammon   klines     ksame       kwin4
blackjack  gnometris       kbattleship   kmahjongg  kshisen     kwin4proc
fortune    gnomine         kblackbox     kmines     ksirtet     lskat
glchess    gnotravex       kbounce       knetwalk   ksmiletris  lskatproc
glines     gnotski         kenolaba      kolf       ksnake      mahjongg
gnect      gtali           kfouleggs     konquest   ksokoban    same-gnome
gnibbles   iagno           kgoldrunner   kpat       kspaceduel  sol
gnobots2   kasteroids      kjumpingcube  kpoker     ktron
jim@jim-desktop:/usr/games$ 

Notice the error bash. Play around with it. You'll get the hang of it. :)

---

### Post by zibeezibeehey on 2007-08-14
I went into gparted and found my external hard drive but all the partitions have locks on them? I cant seem to do anything nor do I know what to do to them, lol

---

### Post by Blutack on 2007-08-14
Erm...not being harsh to bwtranch but I think (s)he's missed the point or not refreshed recently.  He was trying to copy the files to an ntfs drive without the ntfs-3g driver installed.  Hence the permissions error.  Don't do any of the terminal stuff for now.
Locks - ah, right click on the external and click unmount.  That should do it.

---

### Post by zibeezibeehey on 2007-08-14
Im sorry bwtranch what you gave me there looks like its really helpful and all but i really dont know what it means, sorry.

---

### Post by zibeezibeehey on 2007-08-14
ok so now its unallocated so I should??? click on the new button up top there.

---

### Post by bwtranch on 2007-08-14
Oh, I was just trying to show you a little about moving around in the filesystem. You see everything in Linux is treated as a file. It's a little hard to get used to, but it has it's advantages.  But didn't gksudo nautilus allow you to change your file permissions?

Edit: Worked for me. Right click on the file(s) you want to change. Go to Properties and Tab to Permissions.

---

### Post by zibeezibeehey on 2007-08-14
i wish i knew, i didnt try it because I had no clue what it was or how to go about doing it in the first place. Like I have a really small amount of knowledge about ubuntu.

---

### Post by Blutack on 2007-08-14
Changing the file permissions won't help bwtranch, the ntfs-3g drivers aren't installed.  The system cannot physically write to the disc, it doesn't know how.

Zee, yes that's right.  Nearly there!

---

### Post by zibeezibeehey on 2007-08-14
whats the disk label I use? LOL im really impatient right now.

---

### Post by Blutack on 2007-08-14
No problem!  I learnt once as well.  Just take the default disk label and hit continue, then make sure you choose fat32.

---

### Post by zibeezibeehey on 2007-08-14
So Filesystem: fat32, create as: Primary Partition, Free space preceding: omb, new size: 114471 mb, free space folloring: 0mb and the round to cylinders box is checked. Is that what I want before I hit add?

---

### Post by Blutack on 2007-08-14
Sounds ok, yes.

---

### Post by zibeezibeehey on 2007-08-14
now i hit apply?

---

### Post by bwtranch on 2007-08-14
#-o

Sorry

---

### Post by zibeezibeehey on 2007-08-14
Dont worry its all good, im just really not into the lingo yet. im not even good with short form all I got is...lol...lmao

---

### Post by Blutack on 2007-08-14
Yes, now you hit apply.

---

### Post by zibeezibeehey on 2007-08-14
CRAP!!! it says and error occurred while applying the operations. Unable to open /dev/sda - unrecognised disk label. What to do, what to do...

---

### Post by Blutack on 2007-08-14
sda!  Erm...you remember what I told you about external and internal drives?  SDA is normally your internal drive (unless you are using Dapper Drake)!  The internal drive should hopefully be ok though.
Unfortunately real life calls and I've got to go.  The help function of gparted is pretty good though, and hopefully someone will take up where I left off...

---

### Post by zibeezibeehey on 2007-08-14
ok cool later, yeah the drives alright i made sure of it, i noticed from the get go that my external drive was sda as opposed to hda my other drives.

---

