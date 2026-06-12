---
title: "please help!  borked my system...  -cries-"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-22
i just borked my system.  i accidentally un-installed the graphics driver and my live cd won't let me view the files i need to edit and back up.  how can i fix this?

---

### Post by taurus on 2007-05-22
What do you mean the LiveCD won't let you view xorg.conf?  You first need to mount your / before you can edit anything in it.  **Assuming** / is on /dev/sda1, run

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/X11/xorg.conf
```

---

### Post by locke.dragon on 2007-05-22
i don't need to view xorg.conf.  i need to either re-install the proper graphics driver or back up my school work and other data and re-install (which is probably a good idea cause i've learned alot about linux in the four months i've used it and i've got alot of crapware that i installed just sitting on my drive).  how can i view a file it says i don't have permission to view?  i can't even look at my school folder.  :(

---

### Post by taurus on 2007-05-22
Post 

```
sudo fdisk -l
```
Otherwise, boot into recovery mode from GRUB menu and reconfigure X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by viva_cthulhu on 2007-05-22
Greetings.
While it would help to describe the nature of the problem more precisely, I have had a similar one (X's graphic interface would refuse to start upon tinkering with the driver, and Ubuntu would boot in terminal mode).
Please ensure you are sharing my problem before acting, and by all means take someone else's advice rather than mine if possibile - I am far from expertise myself.
In my case, resetting /etc/X11/xorg.conf proved sufficient - you should have a backup called "xorg.conf~" in the same directory, you could replace the original with that.
If I am not wrong, there is a terminal command that will accomplish this resetting easily - while I do not recall it, I remember not having to look it up anywhere - the terminal suggested it to me on bootloading, you would probably see it suggested on screen as you load. It will boot some sort of "select video cart" utility - you would have to choose "Mesa" as your video driver then.
Best of luck!

---

### Post by locke.dragon on 2007-05-22
ok.  here goes.  i'm gonna try to explain the problem in PRECISE detail (i was a tad flustered before [my computer is VERY important to me.  :P ])  

as mentioned in some former threads of mine, i tried to install kiba dock (didn't work) which then messed up direct rendering which them messed up beryl.  because i love beryl so much, i immediately set out to attempt to correct the problem.  i've tried anything and everything to no avail.  i'm planning on just re-installing ubuntu as direct rendering works in the live cd (i don't need any help with the previous mentioned problems...  at least not in this thread...).

thinking that un-installing and re-installing the graphics driver would fix the problem, i tried it.  it didn't work.  all it did was TOTALLY mess up my resolution (should be set to 1280x800 but was stuck at 640x480).  915resolution wouldn't fix the problem.  so i un-installed the working driver and installed one that looked like it would work better.  WRONGO!!!  all it did was make it so the GUI would only open the login screen.  

now what happens is that i boot up ubuntu.  it opens the login screen.  i punch in my login data, it waits a few seconds, and then jumps back to the login just so i can repeat the process.  this goes on and on and on.  now i would just like to figure out how to view my files, back them up, and re-install ubuntu.  it would fix many other problems in the process too.

please let me know if i need to be more clearerererer on anything else.  :P  thanks for all the help.

---

### Post by taurus on 2007-05-22
Since your computer is real important to you, why did you even consider playing with beryl because it is only a beta and beta can sometimes work and can sometimes break your machine?  Stay away from beryl, kiba-dock, etc.

At the GUI login screen, press <Ctrl><Alt>F2 to get into a console.  Log in with your name and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure xserver-xrog
```
If you are not sure about a question, just use the default.  Then, use either **vesa** or **i810** driver for your Intel graphic card.

---

### Post by locke.dragon on 2007-05-22
yeah.  i know i shouldn't play around with them.  but beryl hasn't given me any trouble.  and it was REALLY stupid of me to try to install kiba dock.  it's a flaw of mine.  i want to always have my computer up and running perfectly, but i also want it to be on the bleeding edge with the newest stuff that makes my friends go all googly-eyed.  :P

and thanks for that bit of advice.  i'll try it later.  but will that fix the un-installed graphics driver?  i thought doing that would only help you reconfigure your xorg.conf...  -confused-

---

### Post by locke.dragon on 2007-05-22
but how can i view and backup my files on my ubuntu partition through the live cd?  that's what i really want to do.  i'd like to just start over with a fresh install.

ooooo!  lookie!  i hit my 300 post mark!  -does a happy dance-  sorry about that.  :P  a tad off topic.  ;)

---

### Post by taurus on 2007-05-22
Okay, then you need to post the output of this command from a terminal while you are booting from the LiveCD.  You need to mount /home (if you have a separate /home partition; otherwise, you need to mount /) before you can access it to backup your personal stuff.

```
sudo fdisk -l
```

---

### Post by locke.dragon on 2007-05-22
o...k...  but why right now?  all i'm doing is using the live cd.

---

### Post by irish_flu on 2007-05-22
> **locke.dragon said:**
> yeah.  i know i shouldn't play around with them.  but beryl hasn't given me any trouble.  and it was REALLY stupid of me to try to install kiba dock.  it's a flaw of mine.  i want to always have my computer up and running perfectly, but i also want it to be on the bleeding edge with the newest stuff that makes my friends go all googly-eyed.  :P


I have the same problem, buddy.  IMHO it's just part of geekery. :KS

---

### Post by Sparkster185 on 2007-05-22
I'm also pretty new to Linux (converted in Sept 2006), so I screw stuff up sometimes still.

What I found is nice is if you partition your harddisk so that /home is on a completely separate partition from /.  This way, if you do need to re-install your O/S, your user data (documents, music, pictures, application settings, etc.) is protected.  Simply mount your other partition as /home when you re-install and you're all set.

The only thing you need to do after a re-install is to put back all your applications, but with package mangers this only takes me about an hour, if that.

---

### Post by locke.dragon on 2007-05-22
yeah.  i know about the separate /home partition, and i want to do it, but my computer won't let me.  because it's a dell and i still have windoze xp installed as a crutch, i can't make another partition.  it gives me an error saying i already have 4 primary partitions and can't make any more.

---

### Post by Sparkster185 on 2007-05-22
> **locke.dragon said:**
> yeah.  i know about the separate /home partition, and i want to do it, but my computer won't let me.  because it's a dell and i still have windoze xp installed as a crutch, i can't make another partition.  it gives me an error saying i already have 4 primary partitions and can't make any more.

Really?  My primary HD has 6 partitions on it, I believe.  One for the boot loader, one for XP programs, one for XP user data (like /home), one for /, one for swap and a remaining one that's unformatted (it's only 8-10MB).

When you install Ubunutu, you should be able to create as many as you want (I think. Like i said, I'm still learning, too), assuming you don't invade/re-size the XP partition space.

---

### Post by taurus on 2007-05-22
You can only have four primaries partitions but you can have many logical partitions.  To create logical partitions, you need to make one of those primaries into extended partition and then create logical partitions under that extended partition.

Again, if you want to learn how to mount your Ubuntu so you can backup your personal stuff, you need to post the output of your harddrive layout.

```
sudo fdisk -l
```

---

### Post by locke.dragon on 2007-05-22
that may be the problem.  i have to resize my xp partition to make room for the new one.  i think the reason you have so many partitions if because you have some of them housed within another.  you probably only have one or two primary partitions that are then broken down into smaller, separate partitions.  could anyone tell me how to make a new partition when i already have 4 primaries?  i have a small one from windows that i don't know what it's for, the primary windoze partition, my primary linux partition which houses my linux swap and home folder, and a dell system restore partition.  the two extra windoze ones were installed by default.  any ideas?

---

### Post by locke.dragon on 2007-05-22
here's what i get when i do that in the live cd.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2873    23037210    7  HPFS/NTFS
/dev/sda3            6507        7112     4867695   db  CP/M / CTOS / ...
/dev/sda4            2874        6506    29182072+   5  Extended
/dev/sda5   *        2874        6409    28402888+  83  Linux
/dev/sda6            6410        6506      779121   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

---

### Post by taurus on 2007-05-22
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda5 /mnt/ubuntu
ls -la /mnt/ubuntu/home/**username**
```
where **username** is your actual login name.  Or you can use nautilus to browse to /mnt/ubuntu/home and all your personal stuff is in **username** directory.

---

### Post by locke.dragon on 2007-05-22
it still tells me

> 
You do not have the permissions necessary to view the contents of "BYU".


(BYU is my school work folder)

---

### Post by taurus on 2007-05-22
Where is BYU located on the harddrive?  Is is located under /home/**username** like /home/**username**/BYU?

```
ls -la /mnt/ubuntu/home/**username**
```

---

### Post by locke.dragon on 2007-05-22
it's located at 
/home/link/Documents/BYU
and then all my school stuff is organized in an extensive system of files.  :P

---

### Post by locke.dragon on 2007-05-22
hmmm.

```

ubuntu@ubuntu:~$ ls -la /mnt/ubuntu/home/link/Documents/BYU
ls: /mnt/ubuntu/home/link/Documents/BYU: Permission denied
ubuntu@ubuntu:~$ 

```

---

### Post by taurus on 2007-05-22
Try

```
sudo ls -la /mnt/ubuntu/home/link/Documents/BYU
```

p.s.  And just so you know, you can access Ubuntu (harddrive) from XP with [http://www.fs-driver.org](http://www.fs-driver.org).

---

### Post by locke.dragon on 2007-05-22
this is what i get now.

```

ubuntu@ubuntu:~$ sudo ls -la /mnt/ubuntu/home/link/Documents/BYU
total 20
drwx------  4 1000 1000 4096 2007-04-16 12:28 .
drwxr-xr-x 25 1000 1000 4096 2007-05-17 15:55 ..
drwx------  3 1000 1000 4096 2007-04-01 15:21 8th Grade
drwx------  9 1000 1000 4096 2007-04-01 15:20 9th Grade
-rw-r--r--  1 1000 1000  367 2007-04-16 12:27 Codes
ubuntu@ubuntu:~$ 

```

but it won't let me look at it in nautilus.  and i'd like to avoid win xp at all costs.  i don't trust it anymore and wouldn't want to trust it with my school work that's taken half a year to complete.  yipes!

---

### Post by Sparkster185 on 2007-05-22
Maybe you could .tar.gz up your school work and burn it to a CD via the command line?

---

### Post by locke.dragon on 2007-05-22
care to tell me how to do that?

---

### Post by taurus on 2007-05-22
Run nautilus as root.

```
gksudo nautilus
```

---

### Post by Sparkster185 on 2007-05-22
> **locke.dragon said:**
> care to tell me how to do that?

I'm not sure how to insert the "CODE" quotes, so I'll just type it out.

*Creating the tarball*

cd SCHOOL_DIRECTORY
tar -cvfz schoolwork.tar.gz *

*Burn to a CD via command line*
 (Note, I've never actually done this, so I can't help beyond this link)

[http://sharkysoft.com/tutorials/linuxtips/cdcommands/](http://sharkysoft.com/tutorials/linuxtips/cdcommands/)

---

### Post by locke.dragon on 2007-05-22
ok.  thanks.  but just like the idiot i am, i was looking in the wrong directory.  after following the mount instructions, i needed to look in 
> 
/mnt/ubuntu/home/link/Documents/BYU

after doing
```

gksudo nautilus

```
DUH!!!  and as for how to do the code box, just type 
> 
[*CODE*]
code goes here
[/*CODE*]

be sure to remove the asterisks.  you can also do that for the quote box.  just replace "CODE" with "QUOTE" and you're all set!  :D  thanks for all the help up to this point.

could someone point me in the direction of a how-to on how to re-install ubuntu?

---

### Post by Sparkster185 on 2007-05-22
> 
could someone point me in the direction of a how-to on how to re-install ubuntu?

I just download the lastest version and burn the install CD.  Boot from the CD and follow the instructions.  Beware though, this will re-format your / partition (it's not a choice), so if you don't have /home mounted somewhere else (separate partition), you'll loose your data.

---

### Post by Terl on 2007-05-22
> **locke.dragon said:**
> 

could someone point me in the direction of a how-to on how to re-install ubuntu?

[Installation Help]("https://help.ubuntu.com/community/Installation")

---

### Post by locke.dragon on 2007-05-22
hey thanks!  this is EXACTLY what i need.  so as long as i make a backup of my data, i can re-install ubuntu and then just put my data back right?

---

### Post by Terl on 2007-05-22
> **locke.dragon said:**
> hey thanks!  this is EXACTLY what i need.  so as long as i make a backup of my data, i can re-install ubuntu and then just put my data back right?

Yes.  If you can back-up your data and then do a reinstall, you should be ok.

---

### Post by locke.dragon on 2007-05-22
and i don't have to do anything out of the ordinary like delete my current ubuntu partitions right?

---

### Post by locke.dragon on 2007-05-22
does anyone know of any other ways to access my ubuntu partition from windows?

---

