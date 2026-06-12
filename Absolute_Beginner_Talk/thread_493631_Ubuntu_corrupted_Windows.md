---
title: "Ubuntu corrupted Windows"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by androidkaita on 2007-07-05
SO yeah, I tried to Dual Boot Ubuntu with windows. It installled great, and everything was fine, until I went back to my windows XP partition. It gave me a BSOD everytime I tried. So I stuck in my XP disc and attempted to install it overwriting my entire hard drive (including Ubuntu) and it was going great, but after the setup was complete, it just kept repeating the setup over and over. So I turned it off, and tried to turn it on, and it said failure to read hard drive. SO i popped in Ubuntu Live CD, and it worked fine, and installed again, and it still worked fine. And atm i am using it, but want to get windows back. But I cant seem to install it. WTF is going on?

---

### Post by dhruva023 on 2007-07-05
that's not ubuntu, who corrupted the windows,

did you defrage the windows before u install the ubuntu?

and, if you want to install windows,  using gparted, reformate your hard drive, and then try to install it again.

---

### Post by androidkaita on 2007-07-06
I have no idea what gparted is, and I dont know how to do anything you said :(

---

### Post by Raineer on 2007-07-06
[Gparted]("http://gparted.sourceforge.net/livecd.php") is the ultimate tool for formatting and arranging partitions on your HDD (it can even be used to resize and move existing partitions safely)

Install Windows first, then install Ubuntu and Ubuntu will manage to dual-boot both.

---

### Post by southernman on 2007-07-06
> **androidkaita said:**
> I have no idea what gparted is, and I dont know how to do anything you said :(
First and foremost, Welcome to Ubuntu!

As suggested, Ubuntu didn't do anything to your Windows install... that you didn't allow to happen. Surely you've heard the old saying that, "A computer is only as good as the person using it." Now, for the hard reality check... your comment quoted above suggest that you didn't do your homework and in typical end user fashion, you choose to blame something or someone else.

There are a whole lot of information available at your finger tips in regards to **Dual Booting Windows and Ubuntu** specifically... Linux in general. If you take the time and google the bold text and search these forums (this problem is already covered in depth), you'll have a much better easier go at making this work.

> WTF is going on?
Look within to find the answer to that question.

---

### Post by sab0403 on 2007-07-06
Alright now...

Let's see. You say you installed Ubuntu over XP? Could you please enter into a command line: ```
sudo parted /dev/hda
``````
unit s
``````
print
``````
quit
``` and post the output?

What these commands do is output the state of your hard drive, what partitions it has, etc. After we understand that, we can help you restore the XP partition.

---

### Post by androidkaita on 2007-07-06
How do I enter the codes? (lol im such a noob)

---

### Post by splintercellguy on 2007-07-06
Assuming you're in Ubuntu, Applications -> Accessories -> Terminal.

---

### Post by GFC2 on 2007-07-06
Speaking as one noob to another, Applications>Accesories>Terminal will get you where you need to be.  The terminal will show you a prompt in the format username@computername followed by a flashing black box.  You can either enter the commands manually or copy/paste them from sab0403's post.

---

### Post by androidkaita on 2007-07-06
> **sab0403 said:**
> Alright now...

Let's see. You say you installed Ubuntu over XP? Could you please enter into a command line: ```
sudo parted /dev/hda
``````
unit s
``````
print
``````
quit
``` and post the output?

What these commands do is output the state of your hard drive, what partitions it has, etc. After we understand that, we can help you restore the XP partition.

ok, the first code gave me the result :sudo parted /dev/hda - no such file or directory
retry/cancel?

then

The program 'units' is currently not installed.  You can install it by typing:
sudo apt-get install units
Make sure you have the 'universe' component enabled
bash: units: command not found

trhen
 print does nothing at all

then
bash: command quit not found

---

### Post by whizbaby on 2007-07-06
> **dhruva023 said:**
> did you defrage the windows
This is essential. The windoze filesystem is so phreaked up that it manages to frag SYSTEM.INI to a point not readable anymore at startup(own experience, not only 1 time). I had to defrag system.ini manually by copying it to the ubuntu partition and back again lol(using ntfsmount).

---

### Post by twiceasworn on 2007-07-06
Well, looking at the state of things I would suggest googling the bolded text in the response above and get a step by step walkthrough on doing this.  If you don't know what defragging your hard drive means, than you really shouldnt be trying to dual-boot without a walkthrough.

As the previous poster said there is a wealth of information about this subject at your finger tips.

---

### Post by androidkaita on 2007-07-06
ok, so is the defragiing thing necceseary before I can go back to Windows?

edit

ok nevermind, I just realized you can only do it in windows.

so is it safe to go back now?

---

### Post by twiceasworn on 2007-07-06
Personally I think you are better off without windows.  If Ubuntu is working now, why not keep it?  What is keeping you tied to windows?

---

### Post by androidkaita on 2007-07-06
Because, Im just used to it, ive been running it all my life. I like Ubuntu, dont get me wrong, but I would much rather dual-boot than just have Ubuntu.

---

### Post by Catsworth on 2007-07-06
The reason that the command:

```

units

```

could not be found is because the command is actually:

```

unit s

```

Note that there is a space between 'unit' and 's'.

Please try the instructions that you were given again, and post the output here for us to check.

When you input

```

sudo /dev/hda

```

you will be asked for a password, you need to input *your* account password at this point.

---

### Post by androidkaita on 2007-07-06
> **Catsworth said:**
> The reason that the command:

```

units

```

could not be found is because the command is actually:

```

unit s

```

Note that there is a space between 'unit' and 's'.

Please try the instructions that you were given again, and post the output here for us to check.

When you input

```

sudo /dev/hda

```

you will be asked for a password, you need to input *your* account password at this point.

ok, for the sudo command I already put the password and got the result I already showed. and for unit s I still get Bash : Unit: Command not found.

---

### Post by Catsworth on 2007-07-06
Ok, do me a favour and just type:

```

mount

```

in a terminal and post the result back here.

---

### Post by androidkaita on 2007-07-06
> **Catsworth said:**
> Ok, do me a favour and just type:

```

mount

```

in a terminal and post the result back here.

ok, heres what I got:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by Catsworth on 2007-07-06
Ok, I'm fairly new to this as well.

But, I'm guessing that instead of:

```

sudo parted /dev/hda

```

you need to type:

```

sudo parted /dev/sda

```

followed by the rest of the commands, and then post the results.

---

### Post by sci-fi guy on 2007-07-06
> **GFC2 said:**
> Speaking as one noob to another, Applications>Accesories>Terminal will get you where you need to be.  The terminal will show you a prompt in the format username@computername followed by a flashing black box.  You can either enter the commands manually or copy/paste them from sab0403's post.

I personally have dragged the terminal shortcut to the top panel, next to FF, Evolution, and Help. Makes access much easier.

---

### Post by androidkaita on 2007-07-06
ok, so this is exactly what I did in terminal:

andrew@andrew-desktop:~$ sudo parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            

Disk /dev/sda: 390721967s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         388082204s  388082142s  primary   ext3         boot 
 2      388082205s  390716864s  2634660s    extended                    
 5      388082268s  390716864s  2634597s    logical   linux-swap        

(parted)Quit
Information: Dont forget to update  /etc/fstab, if necessary.

---

### Post by sab0403 on 2007-07-06
> **androidkaita said:**
> ok, heres what I got:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

It looks like you don't have a Windows partition, at least not one mounted. Don't panic, we can get it back.

Ok... please try the following commands:```
sudo parted /dev/sda
``````
unit s
```print```
quit
```and post the output. It looks like you have a Serial ATA hard disk, so we need to input these (slightly) modified commands instead.

---

### Post by androidkaita on 2007-07-06
> **sab0403 said:**
> It looks like you don't have a Windows partition, at least not one mounted. Don't panic, we can get it back.

Ok... please try the following commands:```
sudo parted /dev/sda
``````
unit s
```print```
quit
```and post the output. It looks like you have a Serial ATA hard disk, so we need to input these (slightly) modified commands instead.

I already did that in the above post.

---

### Post by Catsworth on 2007-07-06
> **androidkaita said:**
> I already did that in the above post.

Settle ;)  It's just posts getting crossed over - it'll al get sorted in the end :)

---

### Post by androidkaita on 2007-07-06
> **Catsworth said:**
> Settle ;)  It's just posts getting crossed over - it'll al get sorted in the end :)

sorry if that sounded like I was mad or something, I wasnt lol

heres the results again

andrew@andrew-desktop:~$ sudo parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) print

Disk /dev/sda: 390721967s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 63s 388082204s 388082142s primary ext3 boot
2 388082205s 390716864s 2634660s extended
5 388082268s 390716864s 2634597s logical linux-swap

(parted)Quit
Information: Dont forget to update /etc/fstab, if necessary.

---

### Post by Catsworth on 2007-07-06
LoL, np.  Just know that this stuff can get frustrating at times.  I'm totally new to Ubuntu as well (still consider myself new after nearly 8 months :)  ), it's all about the learning for me - I just wish things could be slightly easier some times.

It's worth sticking with though :)

---

### Post by androidkaita on 2007-07-06
> **Catsworth said:**
> LoL, np.  Just know that this stuff can get frustrating at times.  I'm totally new to Ubuntu as well (still consider myself new after nearly 8 months :)  ), it's all about the learning for me - I just wish things could be slightly easier some times.

It's worth sticking with though :)

well I hope to come back once I get all this dualboot stuff sorted out.

---

### Post by sab0403 on 2007-07-06
> **androidkaita said:**
> ok, so this is exactly what I did in terminal:

andrew@andrew-desktop:~$ sudo parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            

Disk /dev/sda: 390721967s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         388082204s  388082142s  primary   ext3         boot 
 2      388082205s  390716864s  2634660s    extended                    
 5      388082268s  390716864s  2634597s    logical   linux-swap        

(parted)Quit
Information: Dont forget to update  /etc/fstab, if necessary.

Great then. Well, it looks like you don't have a Windows partition anymore. It also looks like you have a big hard driver, around 200Gib, so you'll have no problem accomodating both Linux and Windows. What we need to do right now is to rearrange the size of your partitions so that you have space to create a Windows-compatible one (either NTFS or FAT).

What you need to do right now is boot from your LiveCD. To do that, please put the CD in your PC, and reboot. From the LiveCD, you'll be able to post here. We'll continue giving you directions once you've booted with the LiveCD.

---

### Post by androidkaita on 2007-07-06
> **sab0403 said:**
> Great then. Well, it looks like you don't have a Windows partition anymore. It also looks like you have a big hard driver, around 200Gib, so you'll have no problem accomodating both Linux and Windows. What we need to do right now is to rearrange the size of your partitions so that you have space to create a Windows-compatible one (either NTFS or FAT).

What you need to do right now is boot from your LiveCD. To do that, please put the CD in your PC, and reboot. From the LiveCD, you'll be able to post here. We'll continue giving you directions once you've booted with the LiveCD.

Ok then.

I reall appreciate ur help btw.

---

### Post by androidkaita on 2007-07-06
ok, Im on the liveCD now

---

### Post by sab0403 on 2007-07-06
No prob. :popcorn:

Please post when you've booted with the LiveCD.

---

### Post by Catsworth on 2007-07-06
I think (s)he is already on the LiveCd.

---

### Post by androidkaita on 2007-07-06
yes I (he) am. :p

---

### Post by Catsworth on 2007-07-06
> **androidkaita said:**
> yes I (he) am. :p

I tried to cover my bases, you never know :D

---

### Post by sab0403 on 2007-07-06
> **androidkaita said:**
> ok, Im on the liveCD now

Great.

What we'll run right now is a program called "GParted". Press <Alt>+F2 and in the box that pops up please write: ```
gksudo gparted
```You'll then see a window similar to this:

[IMG]http://upload.wikimedia.org/wikipedia/en/3/32/Gparted_1_big.jpg[/IMG]

Please take a screenshot of your particular window and post it.

---

### Post by androidkaita on 2007-07-06
[IMG]http://img.photobucket.com/albums/v629/androidkaita/Screenshot.png[/IMG]

---

### Post by sab0403 on 2007-07-06
Great. Give me a second so I can post back instructions.

---

### Post by androidkaita on 2007-07-06
ok.

---

### Post by lbelloq on 2007-07-06
This is plainly amazing. A system recovery and installation from a LiveCD, and getting supported through a forum on the Internet. And in real-time.
And free as in freedom and in beer, LOL.
This kind of things can only be done with Linux.
I promise that when I become an expert in Ubuntu installations, I'll post my Ekiga account and instructions for anyone who wants real-time support in his Ubuntu setup.

---

### Post by sab0403 on 2007-07-06
Ok, so here's what you'll do.

You're going to right-click on the FIRST partition (the biggest one), and then choose the "Resize/Move" option. That will pop-up a window where you'll see a physical representation of that partition, and three text boxes, of which only two (the last two) will be available to change. In the second one (labeled "New Size") please write```
80000
```, which will make this partition 80 Gib in size. Now click on the "Resize" button.

Next, right-click on the gray space that just appeared next to your resized partition, and click on "New" option. Again, this will pop up a window, but a bit different. Locate the "Filesystem:" option and click on the box next to it. Select "NTFS", to keep things simple. Then click on the "Add" button.

You'll be back at the main GParted window. Take a screenshot, upload it and please post it before continuing. Now simply click on "Apply", sit back, and let it do it's job. When it's done, it'll report that "all the operations have finished succesfully" or something akin to that. You'll click "OK", restart, and then you'll be able to reinstall Windows.

***WARNING*** --> After you install Windows, you'll no longer be able to boot to Ubuntu. However your Ubuntu installation will still be there; we'll just need to restore GRUB to work. I'm a bit unsure as to how to do that, but let me check around and I'll post back. Also... please boot to Ubuntu one more time before you install Windows, and post from there. I want to back up your GRUB file so we won't have to restore it from scratch.

---

### Post by sab0403 on 2007-07-06
> **lbelloq said:**
> This is plainly amazing. A system recovery and installation from a LiveCD, and getting supported through a forum on the Internet. And in real-time.
And free as in freedom and in beer, LOL.
This kind of things can only be done with Linux.
I promise that when I become an expert in Ubuntu installations, I'll post my Ekiga account and instructions for anyone who wants real-time support in his Ubuntu setup.

Oh, I'm not an expert by any means. I've just been down this road before.

Would you believe that I've had to reinstall Ubuntu about 12 times in a three week span? That includes two PCs, but still... mostly because I was too inexperienced and ended up screwing things up. I'm fairly comfortable reformatting/reinstalling, though, so that helped, but even so, it's a lot. So I gained a bit of experience. ;)

Also, I just had a problem with an NTFS partition that went AWOL. So I had to learn to use GParted.

My point is... you don't have to be an expert. If you're comfortable using graphics software, for instance, you can help out there. Or with IM software. Or even with text editing. Every bit of help is needed - when I first started with Linux (Mandrake, back in '99 or so) I didn't even know how to edit text files. Tutorials on this (yes, they existed!) helped me out, big time. But nice disposition... :D

Anyway, sorry for going into the sandbox.

---

### Post by sci-fi guy on 2007-07-06
Editing a text file isn't that simple if it needs to be opened as root and you have used Windows all your life.

---

### Post by androidkaita on 2007-07-06
> **sab0403 said:**
> Ok, so here's what you'll do.

You're going to right-click on the FIRST partition (the biggest one), and then choose the "Resize/Move" option. That will pop-up a window where you'll see a physical representation of that partition, and three text boxes, of which only two (the last two) will be available to change. In the second one (labeled "New Size") please write```
80000
```, which will make this partition 80 Gib in size. Now click on the "Resize" button.

Next, right-click on the gray space that just appeared next to your resized partition, and click on "New" option. Again, this will pop up a window, but a bit different. Locate the "Filesystem:" option and click on the box next to it. Select "NTFS", to keep things simple. Then click on the "Add" button.

You'll be back at the main GParted window. Take a screenshot, upload it and please post it before continuing. Now simply click on "Apply", sit back, and let it do it's job. When it's done, it'll report that "all the operations have finished succesfully" or something akin to that. You'll click "OK", restart, and then you'll be able to reinstall Windows.

***WARNING*** --> After you install Windows, you'll no longer be able to boot to Ubuntu. However your Ubuntu installation will still be there; we'll just need to restore GRUB to work. I'm a bit unsure as to how to do that, but let me check around and I'll post back. Also... please boot to Ubuntu one more time before you install Windows, and post from there. I want to back up your GRUB file so we won't have to restore it from scratch.

problem, the resize/move partition option is greyed out :(

---

### Post by lbelloq on 2007-07-06
Maybe you need to unmount the volume before resizing.

---

### Post by androidkaita on 2007-07-06
> **lbelloq said:**
> Maybe you need to unmount the volume before resizing.

Are you sure? I dont wanna screw anything up anymore than it already is.

---

### Post by eternalsword on 2007-07-06
if you're running from the livecd, you can unmount safely.

from the terminal
```
df
```

this will tell you what's mounted and the mount points.

you'd be looking for and /dev/sda1 entry.  see where it mounts to and then enter
```
sudo umount /path/of/mountpoint/here
```

---

### Post by androidkaita on 2007-07-06
ok, all is good now. Heres the screenshot:

[IMG]http://img.photobucket.com/albums/v629/androidkaita/Screenshot-1.png[/IMG]

(yes, I made Ubuntu 50gb, because thats what I originally wanted)

---

### Post by androidkaita on 2007-07-06
So am I ok to continue...?

---

### Post by lbelloq on 2007-07-06
I think you're OK. Just press the Apply button and wait (browse the Web, listen to music, etc.) until Gparted has finished the job.

---

### Post by androidkaita on 2007-07-06
> **lbelloq said:**
> I think you're OK. Just press the Apply button and wait (browse the Web, listen to music, etc.) until Gparted has finished the job.

ok, here it goes *crosses fingers*

edit

nope, didnt work.
[IMG]http://img.photobucket.com/albums/v629/androidkaita/Screenshot-2.png[/IMG]

---

### Post by androidkaita on 2007-07-06
grrr this is starting to get frustrating, somebody please help?

---

### Post by lbelloq on 2007-07-06
[http://ubuntuforums.org/showthread.php?t=493686](http://ubuntuforums.org/showthread.php?t=493686)

---

### Post by ndinadis on 2007-07-06
seems you guys know what you are doing, do you mind having a look at my thread "vista not working after ubuntu install" 
Thanks

---

### Post by androidkaita on 2007-07-06
> **lbelloq said:**
> [http://ubuntuforums.org/showthread.php?t=493686](http://ubuntuforums.org/showthread.php?t=493686)

thanks

---

### Post by androidkaita on 2007-07-06
so Im supposed to burn the gparted ISO, and then try it with that?

---

### Post by sab0403 on 2007-07-06
Umm... are you sure you booted from the LiveCD? I ask because GParted isn't supposed to report those kinds of errors from the LiveCD.

Does your Desktop show an "Install" icon?

---

### Post by lbelloq on 2007-07-06
> **androidkaita said:**
> so Im supposed to burn the gparted ISO, and then try it with that?

Not exactly. You remember the link I gave you? There was a post about forcing a file system check; use that command to check your /dev/sda1.
After the checking, try resizing your partitions again.

---

### Post by lbelloq on 2007-07-06
BTW, are you OK with wiping entirely your hard disk and starting over? Not that we're going to do that, just asking out of curiosity.

---

### Post by sab0403 on 2007-07-06
> **lbelloq said:**
> BTW, are you OK with wiping entirely your hard disk and starting over? Not that we're going to do that, just asking out of curiosity.

Sounds like my doctor.

"Are you ok with shots? Not that I'm going to have to give like 25 to you... just checking". :popcorn:

---

### Post by androidkaita on 2007-07-06
Right now im formatting my harddrive and trying to install windows XP over everything. It didnt work last time, but I hope it will this time.

thanks for all the help, but I just really want windows back ASAP, and this is probably the fastest way.

---

### Post by lbelloq on 2007-07-06
> **sab0403 said:**
> Sounds like my doctor.

"Are you ok with shots? Not that I'm going to have to give like 25 to you... just checking". :popcorn:

LOL.

---

### Post by androidkaita on 2007-07-06
Great, now my computer wont start. My god this is so annoying :@ Why is it that only Ubuntu works? Im gonna try Vista now I guess.

---

### Post by lbelloq on 2007-07-06
Wait.
Are you in Live CD right now?

---

### Post by androidkaita on 2007-07-06
nope, brothers comp

---

### Post by sab0403 on 2007-07-06
If you're dead set into reinstalling from scratch (and all partitions be damned), it's best to boot to the LiveCD and use GParted - simply erase every single partition, then create a new one that occupies the entire space of your hard drive. Create is as NTFS, and then install XP (or Vista, your choice).

Hopefully you'll try Ubuntu down the road. If you need more help we're here.

---

### Post by lbelloq on 2007-07-06
May I give you 2 advices?

1. Don't install Vista. It is known that in some cases, Gparted, GRUB and others don't work really well w/Vista. use XP instead.
2. When installing XP, DO NOT assign all the disk space to XP. You have a 200 GB disk I think; assign 150 GB for XP and leave the rest unassigned. It'll make things easier after.

P.D.: 3rd (LOL). If you can't boot XP installation from the CD, use GParted Live CD to remove ALL partitions from the disk and don't create anything. Make sure you remove GRUB too.

sab0403: Seconded.

---

### Post by androidkaita on 2007-07-06
> **sab0403 said:**
> If you're dead set into reinstalling from scratch (and all partitions be damned), it's best to boot to the LiveCD and use GParted - simply erase every single partition, then create a new one that occupies the entire space of your hard drive. Create is as NTFS, and then install XP (or Vista, your choice).

Hopefully you'll try Ubuntu down the road. If you need more help we're here.

ok thanks, Id much rather have XP than Vista, but its not working right now, so I may have to go to Vista. And I REALLY appreciate everyones help on here, and I hope to be back soon when I get this all sorted out and get Ubuntu Dual-Booted. If I never get Ubuntu Dual-Booted, Then Ill install it on my computer when I ge a new one.

---

### Post by xpod on 2007-07-06
> 
1. Don't install Vista. It is known that in some cases, Gparted, grub and others don't work really well w/Vista. use XP instead.
2. When installing XP, DO NOT assign all the disk space to XP. You have a 200 GB disk I think; assign 150 GB for XP and leave the rest unassigned. It'll make things easier after.

I certainly wouldn`t advise anyone to install Vista but i think many of the problems people had with Vista and gparted etc were occuring during resizing operations with Vista already installed.

I installed Vista a couple of times from scratch after creating the partitions with gparted and never had a problem with it but i can only speak from my own experience with it.I was quite suprised how simple it was in fact:D
Of course though,i only ever installed Vista to see "what might have been" and it was off again two months later.

There is no comparison imo.:D
Good luck people & good night

---

### Post by sab0403 on 2007-07-06
> **androidkaita said:**
> ok thanks, Id much rather have XP than Vista, but its not working right now, so I may have to go to Vista. And I REALLY appreciate everyones help on here, and I hope to be back soon when I get this all sorted out and get Ubuntu Dual-Booted. If I never get Ubuntu Dual-Booted, Then Ill install it on my computer when I ge a new one.

If you'd rather have XP, then lbelloq's 3rd option seems best (and then follow his 2nd option). Using the LiveCD and GParted to reorganize/delete/recreate your partitions doesn't mean you'll have to use Ubuntu - we point it out because it's an easy way to do work on partitions.

Again, my advice would be to delete all partitions with GParted on the LiveCD, then run the XP installation (and asign only 150 Gb of space to it, leaving the rest unpartitionted). Just as lbelloq suggested...

Good luck!

---

### Post by por100pre1 on 2007-07-06
My experience installing Ubuntu with Vista already installed has been sweet and painless at all.
Here's the way I have done it:

1. I shrink the Vista partition with Vista's Disk Management (it may be necessary to defragment the partition first).

2. When I install Ubuntu** I install GRUB right in the Ubuntu's partition instead of the MBR**.

3.After installing Ubuntu I add Ubuntu to the Vista's bootloader with [EasyBCD 1.6]("http://neosmart.net/dl.php?id=1").

Installing GRUB in the MBR is really safe but this is an alternative that works and can be an option for some users.

---

### Post by androidkaita on 2007-07-06
Everything is well now, I am installing Windows XP as we speak, and the installation is finally working perfectly. Thank you guys SOOOOO much for your help. And I assure you that If I ever get a new computer(or a PS3 lol) I will be installing Ubuntu on that. So expect more questions sooner or later :lol:

---

### Post by lbelloq on 2007-07-06
Ask as much as you want, good sir.
The Ubuntu Knights will always be willing to help you.

---

### Post by sab0403 on 2007-07-06
> **androidkaita said:**
> Everything is well now, I am installing Windows XP as we speak, and the installation is finally working perfectly. Thank you guys SOOOOO much for your help. And I assure you that If I ever get a new computer(or a PS3 lol) I will be installing Ubuntu on that. So expect more questions sooner or later :lol:

Glad to know.

Good luck! :popcorn:

---

### Post by djchandler on 2007-07-06
This thread is just too bizarre. I used to work in a store that specialized in selling used computers and used parts some 15 years ago. My co-workers and I used to joke that being able to even turn on a computer should require passing some sort of written test, just like you have to do to learn to drive and get a learner's permit. (That's how people legally learn to drive in Kansas, unless they live on a farm.) This thread really takes me back. We used to try to do this sort of support over the telephone when people were changing from DOS/Windows 3.1 to Windows 95.

androidkaita, we have no real idea of what's actually going on with your computer, as I in particular question the accuracy of what you reported from the very start. If there is a language issue, say so, and we'll find somebody that speaks your native language to help you. Ubuntu's installer will not overwrite used hard disk space unless you tell it to. It just doesn't work that way. Nobody told you to delete Ubuntu's swap partition, yet you seemed to try to do that. And you booted from the HDD, not the Live CD, and that's why you were not allowed to alter the HDD and create the NTFS primary partition.

I advise people, as a general rule, the advanced settings in your BIOS should be set to boot from removable media first, with the HDD being the second or even third boot device. For instance: the BIOS on the computer I'm on now is set to boot from floppy drive first, in case I need to boot DOS to run a DOS program to update my BIOS, so it is the least likely item to be booted from, then the CD or DVD drive second, which ever is master on its ide port, as it is usually used to install operating systems, and not likely to be needed often as a boot device, and then finally the hard disk. I know this sounds backwards, but if you think about it, it does make sense. Also disable floppy seek to avoid that grinding noise it makes when it tries to read from a floppy and one is not there. If you actually want to boot from the floppy, it will. Doing this kind of BIOS setup allows you to stop the operating system installed on the hard drive from booting so you can make changes if necessary. It takes surprisingly little time to bypass these two devices and to finally boot from the hard disk drive. What is your boot device setup? The reason why the Live CD did not boot and the hard disk did is because you have it before the CD or DVD drive in the advanced BIOS settings.

Finally, if you have no idea what I just wrote means, then by all means, wipe your hard drive and start over with XP. When you have learned enough to understand what I wrote in the preceding paragraph, you may know enough to be ready for a dual boot system.

The rest of you guys, you are just running up your bean counts, and I don't mean for that to be insulting. I don't think our thread starter is getting ***IT***.

DJ

---

### Post by por100pre1 on 2007-07-06
> **djchandler said:**
> 
The rest of you guys, you are just running up your bean counts, and I don't mean for that to be insulting. I don't think our thread starter is getting ***IT***.:lolflag:


**That's really insulting  DJ. I don't think any number of posts in this forum will change the life of anybody for the best. If you think some cheap beans are really something you can have the beans of my dish** :p .

---

### Post by lbelloq on 2007-07-06
Your post is just too bizarre. In case you haven't realized yet, this is a *help* forum; we're supposed to help the n00bs with problems to run Ubuntu. And for the last 8 pages, a LOT of people has tried their best to help OP. Sorry, but your post is exactly doing what you don't want: insulting all those who helped in this process.
I've worked for years in IT and support, and your rant is exactly how I feel after a day filled with uncooperative and angry users. But I can get over it, that's what experience taught me. And OP didn't seem like a dumb and uncooperative person.
So, please, if you can't offer your help in this forums, take it somewhere else. We don't need trolls here.

---

### Post by djchandler on 2007-07-06
> **lbelloq said:**
> Your post is just too bizarre. In case you haven't realized yet, this is a *help* forum; we're supposed to help the n00bs with problems to run Ubuntu. And for the last 8 pages, a LOT of people has tried their best to help OP. Sorry, but your post is exactly doing what you don't want: insulting all those who helped in this process.
I've worked for years in IT and support, and your rant is exactly how I feel after a day filled with uncooperative and angry users. But I can get over it, that's what experience taught me. And OP didn't seem like a dumb and uncooperative person.
So, please, if you can't offer your help in this forums, take it somewhere else. We don't need trolls here.

Are you serious? You should have advised him to re-install XP from the start. Besides which, I wasn't trying to be insulting, but if you are insulted, you need be tougher. If you don't like the rest of what I have to say, take it private, please. Go to my profile. I even allow direct emails and invite them.

I realize everybody was trying to help, and, whether you believe it or not, I was too. The guy didn't have a clue. Despite everything you tried to do to help him, he still managed to mis-understand. Go back and read the whole thread through. I did before I made that post, and if you take into account the actual outcome, I gave the newbie the best advice, as that was the actual outcome, even if I didn't do it first. The rest of you should have realized he was in over his head a lot sooner, and that his account of what was actually happening from the start was flawed. That should have been realized by everybody the first time he tried gparted and posted his screen shot. Even unmounted partitions should have shown there. Then he deleted the swap partition when he tried to create a primary NTFS partition, and it was obvious the guy was booting from his hard drive. Didn't anybody else notice the change from the default theme of the posted screenshot? Why would anybody change that when people are trying to help him in real time? What you should be insulted by was the way he named the thread, and then wasted all of your time. It is good that nobody actually jumped all over him. Everybody at least gave him the benefit of the doubt, but you all went way above and beyond what was necessary. Take the whole thread into account before you answer this post.

This post is not private because I lost track of how many people were involved. The best thing was there was no arguing between those trying to help. For that I must say I am actually impressed. The worst thing was there was an awful lot of "tunnel vision" on the part of those trying to help the thread starter.

As for your name calling, I will consider the source. You needed to be corrected, and I did so. If you can't take constructive criticism, it may be in your best interests to put me on your ignore list. I will continue posting when I see mistakes being made, especially by those who are misguided in their attempts to help others.

> Physician, heal yourself. How can you remove a splinter from someone else's eye when you have a log in your own (eye)?

If any of you have further comments about my post, please take it private. I was trying to be nice and not point out how many errors were made by those trying to help, but the previous two posts made my answer here imperative.

DJ

---

### Post by androidkaita on 2007-07-06
There is no language Barrier, im Canadian, and have spoken English all my life. I guess just the way I described my problem sounded so bad because I had no Idea what was going on. Anyway, Windows XP is fully running now, but it wont detect my internet cable, which is weird because Ubuntu could detect it fine >_<. So now I have to figure out how to connect to the internet, and then im happy.

and Im sorry for the thread title, I was in a panic when I named it, and Windows stopped working right after I installed Ubuntu, so I thought that it must have corrupt windows, because that was the last thing I did before the crash.

And I did boot from the live CD. I just changed the theme while I was waiting for the next reply in my thread.

And also, the reason I even attempted this in the first place, is because I have dual-booted XP and Vista before, and I didnt like Vista, SO I wanted to replace it with Ubuntu.

---

### Post by sab0403 on 2007-07-07
> **djchandler said:**
> Are you serious? You should have advised him to re-install XP from the start.

Well, this is *Ubuntu Forums*, after all.. first step should be to try and make the Ubuntu install functional. If the user feels it's not (because he can't dual boot, his background is not to his liking, whatever), we're here to help. The whole Ubuntu philosophy and all that... ;)

However, when he wanted to just-go-back, we helped him too. I can relate. I know what is like to have your PC taken hostage by a faulty/crappy install/OS; I spent *years* dealing with M$. I still have to deal with them. So yeah, I understand a guy who just wants things to go back to the way they were. And all that comes with it (being panicky, maybe skipping a step here or mistyping something there, projecting an attitude that's not really there). After years of IT support, you kinda take it as second nature.

I understand your POV, too. Or at least I think I do. But see... we were all newbies once. Just see my posts: not too long ago (read:a week, a month ago) I was the same way. I hadn't used Linux in a while, I had forgotten even how to list files, etc. Maybe you've been in the top for a while now. But remember you weren't born with the knowledge you now have. Furthermore, remember that computers are not meant to be high-precision tools to be used only by the initiated. They (like cars, something I like to remind my mechanic whenever I pay him a visit) are meant to be *a* tool, and while yes, there are experts, I don't have to know what a partition (or a camshaft) is (or how to work it) for me to use it. I shouldn't have to.

And I don't mean for this to be insulting either. Just a thought. :)

---

### Post by DiG3RATi on 2007-07-23
> **djchandler said:**
> This thread is just too bizarre. I used to work in a store that specialized in selling used computers and used parts some 15 years ago. .......

What a douche... 

Hey DJ, looks to me like everyone learned something from this exchange - that is prior to your spam.  So, we can go your route and the user learns nothing and is turned off by the whole experience... or we can post on and create a potentially useful thread for other newbs.  I, for one, vote the latter... 

<snip>

---

### Post by Computer Guru on 2007-07-24
*cough*

I think this thread needs some love from a moderator.........

---

### Post by anewguy on 2007-07-24
This is a classic example of an a**.  He comes in here after the fact and then wants to bitch - why didn't you post right from the start?  And you better give some of us a little more respect and credit than you seem to - some of us have some very technical backgrounds going back (in my case) to 1977.  The idea here is to help - and keep things light and encouraging.  You sound like the people who used to beep me at 2:30 in the morning because they didn't really know what they were doing but wanted to talk a big show.:(

BTW - 8 years of my technical work was in Kansas.

---

### Post by Malibu Illusion on 2007-07-24
To be honest, DJ is right.

Why all this trouble when all he has is a stock install of Ubuntu and wants to reinstall Windows?  The advice should have been to simply insert the Windows XP installation disk, delete all the partitions and use the full space for an XP reinstall.  All of this can be accomplished with the Windows installation disc.  Ubuntu could then be reinstalled after in a dual boot; this would have been preferential as doing it the other way around would mean he'd need further help reinstalling GRUB.  It's just not worth it when he had absolutely nothing on Ubuntu to begin with.  As I said, it was a stock install.

Why the messing around with partitioning and resizing?  The optimum choice here would be to start again and install Windows across the entire drive.  Simple as that.  No Gparted, no LiveCd just install from the Windows XP disc and you're done.  Ubuntu could have then been reinstalled **correctly** by setting up the partitions from within the Ubuntu setup, rather then telling it to use the entire drive.

The OP's original problem of it "repeating the setup over and over" was likely because he was rebooting from the CD constantly to begin with and hadn't removed it after the first stage of the installation was finished.

---

### Post by por100pre1 on 2007-07-24
> **Malibu Illusion said:**
> To be honest, DJ is right.

DJ was definitively wrong, besides I remember somebody recommending a poster to [ignore you]("http://ubuntuforums.org/showpost.php?p=3064399&postcount=4").

---

### Post by Malibu Illusion on 2007-07-24
It's easy to say someone is wrong while ignoring the perfectly valid points raised, isn't it? ;)

---

### Post by southernman on 2007-07-24
If the OP is up for some fun and *REAL* headaches, try downloading the minimal Gentoo CD and plan to take a day... just to get a basic operational system working! Better RTFM for sure here! Once you've got the basic sytem working, give installing Gnome a shot... it's only what, 479 packages that have to download, compile and install! Grief!

Not that I didn't before, but I have way more respect for Ubuntu as a "ready for primetime" distro... NOW!

*I am not knocking Gentoo at all. It's just a horse of a different color!

---

### Post by bapoumba on 2007-07-24
I'm posting this on behalf of the moderator who closed the thread: time for staff review :)

Edit: to androidkaita, if you would like to see your thread reopened, please PM a moderator. Thanks.

---

