---
title: "Live support for ubuntu installation"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-02
Hello, I just downloaded ubuntu installer, burned it on CD and now I'm going to install it on my laptop. I'm sitting at my office desktop-pc and my laptop is also here. Can anyone support me while installing? I've never installed before neither linux, nor windows. 

I don't have Windows CD, so I'm leaving the old windows XP. right now I'm defragmenting my single drive c, which is 35 GB. there are no more drives on my lap.

---

### Post by aysiu on 2007-04-02
I'd say don't install it yet.

Play with the "live CD" (otherwise known as the Desktop CD) for a couple of weeks. Get used to Ubuntu first. Playing around with it will also give you an idea of whether you will want to install it.

You may also want to read this:
[Is Ubuntu for You?](http://www.ubuntuforums.org/showthread.php?t=63315)

Slow is good. The faster you rush in, the more likely you are to be overwhelmed by problems you can't handle.

---

### Post by oilchangeguy on 2007-04-02
what do you mean, ubuntu installer? did you burn the iso file to cd, or did you burn an image to cd?

---

### Post by O-pos on 2007-04-02
I have iso file on CD. No, I know I want it, I was reading and reviewing materials about linux long time ago. so I know I want Ubuntu Linux, but I want to leave windows for a transitory period.

---

### Post by oilchangeguy on 2007-04-02
if you've burned the iso file to cd, you've made a nice drink coaster. you have to burn it as an image. please advise your computers specs, and what version of ubuntu you are hoping to try.

---

### Post by O-pos on 2007-04-02
as an image? :confused: I have no more CD :(

It's 6.10. My windows is hanging several times/day and so I see no point to wait before I "get used" to the CD.

---

### Post by aysiu on 2007-04-02
This is how you burn the ISO to CD as an image:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by oilchangeguy on 2007-04-02
yes, as an image. most newer cd burning software has the ability to correctly burn an iso file as an image. you may have to hunt for it(the burn as image feature), but it's probably there. and burn it at the slowest speed.

---

### Post by O-pos on 2007-04-02
This is very good step-by-step manual that'll be really useful. However, I think I didn't burn the iso file as an image, I just opened nero, then burned as data file. So should I wait or should I get new CD and try again?

I have broadband internet here, and I downloaded the iso file in 20 minutes. However, I've never seen any MD5SUMS file. should I find it?

---

### Post by aysiu on 2007-04-02
The quick way to tell whether you burnt as data or as an image is to open the CD contents.

If you see one big file, you burnt it as data. If you see a bunch of files and folders, you burnt it as an image.

Checking the MD5SUM isn't necessary, but it's a good idea just to make sure your ISO didn't get corrupted during download.

---

### Post by O-pos on 2007-04-02
I've checked. There's one file which looke like winRAR file. It can be opened and then there appears bunch of files and folders, including starte.exe or something like that. 

Is it bad?

---

### Post by rjfioravanti on 2007-04-02
One way to know for sure, put it in your CD drive and restart your computer!

Make sure your computer's BIOS settings are set with the CD drive having higher boot priority than your hard drive. 

If it boots to the Ubuntu install screen. If the CD spins around a bit and then gives up and boots windows from you hard drive, then you messed up the burn. 

You can get a really good burning app called imgburn to do it for you. It is free and fast to download and start using. It is the one Ubuntu recommends I think

---

### Post by aysiu on 2007-04-02
Are you looking at the CD or the ISO?

Do not look at it with WinRAR. WinRAR thinks the ISO is a zipped file.

Look at it with the regular Windows Explorer and see if it's one big file or a bunch of files and folders, or take rjfioravanti's suggestion, and just boot the computer up with the CD in the drive.

---

### Post by O-pos on 2007-04-02
how can I enter the bios and check what's of higher boot priority?

---

### Post by aysiu on 2007-04-02
> **O-pos said:**
> how can I enter the bios and check what's of higher boot priority?
It kind of depends on your computer. Usually when the BIOS screen flashes when you first boot up the computer, it'll tell you what key to press, but if it doesn't, the keys are usually one of the following:
Esc
F2
F1
F12
Delete

---

### Post by rjfioravanti on 2007-04-02
depends entirely on your machine

Try restarting your computer and pushing buttons as it is booting up. Often F1, F2, Del, Backspace, F8 are good ones to try

If you get to the screen that says its loading windows you are too late!

---

### Post by O-pos on 2007-04-02
OK. I tried and it stopped just at the beginning, where "TOSHIBA" logo appears in red letters. below are five options: one icon with many (three) CDs, next icon with one single CD, floppy, two laptops in network, and USB flash.

I pressed the right arrow several times, so I don't remember which wan was the priority.

which one should I select? many cds oder single cd-icon?

---

### Post by O-pos on 2007-04-02
OK, I managed to change the priority, but after checking the CD it just wrote check failure, starting widnows

---

### Post by dorcssa on 2007-04-02
I think you should write a new cd, but this time as an image. You can do that by opening the iso with the burning application(like nero).

---

### Post by aysiu on 2007-04-02
Here's a HowTo on burning disk images with Nero:
[ HowTo: Burn an ISO disc image with Nero in Windows](http://www.ubuntuforums.org/showthread.php?t=111589)

---

### Post by O-pos on 2007-04-03
OK, I've got another CD and burned iso as an image using CDBurnerXP, lowest speed possible, using [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) as a guide. Now, I should reboot my laptop. One question: I'm leaving old windows version on my lap, I didn't have windows CD, so I'm not installing windows simultaneoslly. I defragmented drive C twice, it's the only drive on my lap. Is it ok now for ubuntu installation? Or do I need to do something in addition?

---

### Post by question_chick on 2007-04-03
Yes, you need to partition the hard drive in your computer.

Decide how big you want the windows portion of the drive and then partition off the rest.

---

### Post by O-pos on 2007-04-03
Help! I don't understand any more! I selected "manual" to make partitions. 

Now I have table "prepare partitions" showing this marked with colors:

/dev/hda1   ntfs    35,24GB   used 10,56GB   24,68GB boot
/deev/hda2 fat32  2,01GB     used 1,71 GB   314,99MB hidden, lba
unallocated           7.84Mb    ---                    ---


I want to make partitions like it's showed in 5th choice here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Windows XP (ntfs) + ubuntu home/shared data (ext3) + ubuntu/ext3 + swap

what is next step I should undertake?

---

### Post by question_chick on 2007-04-03
So are you halfway through the installation?

have you read what is on [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

there is some useful information on there that will walk you through a lot of the installation

If you are stuck with the manual partitions you could always go with the auto option, it's more newbie friendly (like me :D)

---

### Post by O-pos on 2007-04-03
I managed to shrink the ntfs to the minimal required space for windows and deleted another partition fat32. now I have 13 GB ntfs and the rest-unallocated. is it OK?

---

### Post by question_chick on 2007-04-03
yes, that is ok, although are you sure you want the mimimum space for windows? 

That's fine if you don't plan on using windows much but windows seems to like having room to breath and sulks when it only has the bare minimum of space.

aside from that you are doing well so far. So what are you planning on doing with the rest of the space i.e. how do you want your ubuntu partitions set up?
Are you going to have a FAT32 partition for storage?

---

### Post by O-pos on 2007-04-03
Thanks for reply!!! [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) -here, the 5th choice is my favorite choice, I already created corresponding partitions and now I'm about selecting in "prepare mount points" where to put /, /home, swap (these are I was prepared for) and also /boot, /usr, /var, which  I don't know where to put. any ideas?

---

### Post by question_chick on 2007-04-03
I can't be too much help here because when I installed I was the ultimate wuss and installed on a completly separate hdd and I let the installer do all the work for me.

As far as I can tell it shouldn't matter where you put them but the sizes could be important so hopefully someone else can help you out with this part of the installation.

Hope I helped some, I will keep checking back to see if I can help with things I am a little more familiar with.

---

### Post by O-pos on 2007-04-03
I tried my best and I started the installation. Let's see how it works. For OS language I chose english, but It also automatically assigned english language to the keybord, which I didn't want, because I have german keybord. Is it possible to change keybord language to german like in Windows?

---

### Post by question_chick on 2007-04-03
Yes, once the instalation has finished go to system - preferences - keyboard and on the second tab from the left it will give you the option of adding other language keyboards

---

### Post by O-pos on 2007-04-03
Wow, I have Linux! :)

it worked with keyboard language:)

where can I change theme from this red/brown to blue-colored?

---

### Post by question_chick on 2007-04-03
Almost the same place as the keyboard
 System - preferences - themes

also a right click on the background will give you the option of changing the background image

---

### Post by question_chick on 2007-04-03
Now that you have got the installation sorted just have a play around, once you start playing it wont take you long to find your way around.

Good Luck. Have Fun with it.

---

### Post by O-pos on 2007-04-03
It's qool. As soon as I'll have all needed programes, I'll delete windows.

ciao

---

### Post by Degeim on 2007-04-03
I think you may be able to change the Linux-language from English to German if you want to. I assume the German support is far better than Norwegian support, and mine is very good.

In gnome, try System -> Administration -> Language support (or perhaps it is System -> Preferences -> Language support) if you're interested in trying it.

Degeim

---

### Post by O-pos on 2007-04-03
No, for OS language I need english, for keyboard german. I've already done it.

---

### Post by O-pos on 2007-04-03
After just installing Ubuntu Linux, first question I've encountered:

I have dual boot windows/linux and additional partition for shared files, ext3, with ext driver for windows to recognize ext3, like it's described in 5th variant on [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

So now both windows and Linux have access to this partition, but the files, which I put there from windows, cannot be deleted when I'm in Linux, because it says that "not allowed" or "no permission", I don't remember exactly..

How can I get the permission to delete these files?

---

### Post by rjfioravanti on 2007-04-03
Well to see the permissions of files, you can use the following command

```

ls -l

```

you will see each file has 7 properties

_  _ _ _  _ _ _  _ _ _ 

The first one is a d if its a directory, and nothing otherwise, the other groups of three are  read, write and execute permissions for owner, others, and group. 

The first thing to look at is who the owners of the file are, if the owner is not your login name, and the others section does not have read, write permissions, then you won't be able to delete. 

Look up the chmod command for how to modify permissions the way you want

Also look up the chown command for how to change the ownership of a file

Also you can do anything if you run your commands with root privileges, using 

```

sudo rm <file>

```

so look up sudo as well

let me know how it goes

---

### Post by lamalex on 2007-04-03
you will need to edit your fstab. this page was very helpful to me when I used to dual boot. [http://www.linuxjournal.com/article/8761](http://www.linuxjournal.com/article/8761)

---

