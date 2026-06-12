---
title: "Things are bloating up."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Paragdim on 2005-11-16
Hi everyone.

Just switched to Ubuntu (and Linux for the first time) :p.

Everything is going great and I've fiddeled around quite a bit with different applications and system settings. Now, my only worry is this: Ubuntu seems to bloat and eat hard drive space like a monster.

I'm only running Ubuntu on the machine. I've installed som patches, add-ons and programmes via the update manager and synaptics. Also I've added kubuntu via synaptics so I got a dual boot. 

The hard drive is 160 gb. 150 is hda1 which the whole works lies on. I now got 106gb left. Yesterday it was 127gb. I installed some little things today, which should not be more than a few 100mb. So what's happening?

Basically it's just the operating systems Ubuntu/Kubunutu and apps here with 400 mb worth of personal files like word docs, pics etc. The whole thing should be less than 10gb so I should have about 140gb left, give or take.

I'm afraid that in about a week there will be no space left at this rate. 

I would really appreciate if someone had some good sugestions as what to do.:confused: 

Well I'm calling it a night now. :-k

---

### Post by Kyral on 2005-11-16
Uuhhh

You don't dual boot Ubuntu and Kubuntu. They are the same thing. Its just that Ubuntu uses GNOME by default and Kubuntu uses KDE by default. Same repos same support same devs.

Anyway, try doing some things like 

```
sudo apt-get autoclean
``` to purge the Apt-Cache of downloaded package files (This will clean AT LEAST a GB I bet)

---

### Post by Paragdim on 2005-11-16
[QUOTE=Kyral]Uuhhh

You don't dual boot Ubuntu and Kubuntu. They are the same thing. Its just that Ubuntu uses GNOME by default and Kubuntu uses KDE by default. Same repos same support same devs.

Anyway, try doing some things like 

```
sudo apt-get autoclean
``` to purge the Apt-Cache of downloaded package files (This will clean AT LEAST a GB I bet)[/QUOTE]

He he. Well, I'm a complete newbie you see. I remember the Kubuntu package taking about 600mb on the harddrive to install so it's obviously not a completly new operating system as you say. I did the trick with sudo "apt-get autoclean" and it deleted 100mb.

Thanks for the quick help. 

Well now I better go to bed. Burning the midnight oil here

---

### Post by bored2k on 2005-11-16
Try sudo ```
apt-get clean
```every once in a while.

---

### Post by xequence on 2005-11-16
I had my ubuntu install for a week and it had 600 MB of apt cache. Crazy =P

I think you can turn it off in synaptic somehow.

---

### Post by Paragdim on 2005-11-17
Cheers guys. I've done the sudo apt-get clean and installe ccache. Got 500mb back from that. Maybe it's quirte normal then that the system should take 30+gb worth of space??

anyways. thanks again.

---

### Post by lerrup on 2005-11-17
[QUOTE=Paragdim]Cheers guys. I've done the sudo apt-get clean and installe ccache. Got 500mb back from that. Maybe it's quirte normal then that the system should take 30+gb worth of space??

anyways. thanks again.[/QUOTE]

Err, I don't think so as I run gnome and kde on a laptop as a dual boot with Windows.  The size of the hard disc is 30gb. i think ubuntu is on about 12gb.

Are you sure you haven't installed everythng in the repos? ;)

---

### Post by nocturn on 2005-11-17
The key is to find out what part of your HD is filling.

I do this command line (but there are GUI's for this):

```

cd /
sudo du -ms * 2>/dev/null| sort -nr |more

```

Will list the size of each directory (but not their subdirectories) in Megabytes (-ms).  The 2> redirect filters the errors out and sort -nr does a numerical reverse sort to place the largest directories on top.  More just makes it easily readable.

Once you find directories that are unusually large, move into them and repeat the du and sort command to find out which subdirectory is large.

It is quite possible that your space is being filled with log files, stored in /var/log.

---

### Post by ubuntu_demon on 2005-11-17
and for a graphical way to see where your space is :
$sudo apt-get install xdiskusage
$xdiskusage

---

### Post by Paragdim on 2005-11-17
[QUOTE=nocturn]The key is to find out what part of your HD is filling.

I do this command line (but there are GUI's for this):

```

cd /
sudo du -ms * 2>/dev/null| sort -nr |more

```

Will list the size of each directory (but not their subdirectories) in Megabytes (-ms).  The 2> redirect filters the errors out and sort -nr does a numerical reverse sort to place the largest directories on top.  More just makes it easily readable.

Once you find directories that are unusually large, move into them and repeat the du and sort command to find out which subdirectory is large.

It is quite possible that your space is being filled with log files, stored in /var/log.[/QUOTE]


No I certainly haven't installed the lots from the repos:)  Well, at least not to my knowledge. Synaptics says I've got 1647 packages installed from a total of 17,000 something.

I've run the command as you suggested nocturn and this came up:

2494    usr
1442    home
515     proc
139     var
86      lib
37      etc
9       sbin
8       boot
4       bin
3       dev
1       tmp
1       srv
1       root
1       opt
1       mnt
1       media
1       lost+found
1       initrd
1       debootstrap
0       vmlinuz
0       sys
0       initrd.img
0       cdrom
= 4746 megabytes on my calculator

(I frankly thought /etc would be much larger)

I also looked into var/log and it contains 14,7 mb.

beats me!

When I started the installation I fiddeled around with the partition manager for a while, but couldn't make heads and tails out of it. (That and Wifi - which took forever to sort out- is what I reckon Linux/Ubuntu needs to sort out to ease the transition for us newbies) So I just went back and took the standard settings suggested. Which put 1,5gb as swap and about 150gb as hda1 and formatted the whole thing. I suppose the extra 8,5 gb went missing in the formatting and structuring.

I also transfered 6 of my music CDs into *.ogg in my home directory. The only thing I can think of is that Soundjuicer have installed som *.wav files somewhere as well, even though that shouldn't happen, and I can't find any. Or some hacker has got control over my computer and is having a ball.

At least it looks like its stabalised around 107gb of free space now. Just have to wait and see if it eats more I guess. Be a shame to have to re-install the whole thing and get all the packages, fixes and applications again.

edit: just add that I looked into the Disks admin application. This is what I got:
device:/dev/hda1 Filesystem: Extended 3. Size 151.94 gb - 107.34gb free.

Ubuntu Deamon, I ran  $sudo apt-get install xdiskusage but it didn't work. This is the message I got back:
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Not asked for my password or anything and all the reps should be open as I've installe things from the multiverse etc earlier with apt-get commands.

---

### Post by ubuntu_demon on 2005-11-17
If you can't install something you are probably doing it during the the daily cron apt-get update or you have update-manager/synaptic/gnome-app-install or some other program running that's locking the apt database. So make sure no such programs are running and try again.

---

### Post by Paragdim on 2005-11-17
[QUOTE=ubuntu_demon]If you can't install something you are probably doing it during the the daily cron apt-get update or you have update-manager/synaptic/gnome-app-install or some other program running that's locking the apt database. So make sure no such programs are running and try again.[/QUOTE]

I managed to find xdiskusage via synaptics. But can't find the application button to launch it though. Dosen't matter too much since I can do the command in the monitor now.

I've installed XNC (X Northern Captain) and it comes up with a lot of files and directories that I'don't normally see. They all start with a . dot. - like .beagle or .wine.

I'm wondering if this is the harddrive size detection that has got a bug in it. I also remember installing a Windows system way back and there were something about a file filling up a whole sector on the hard drive even though it was much smaller. i.e a file of 100 bytes would still occupy a territory of 1kb or something and nothing else could get to use that space.

Anyways I still got 107 gb so things seems to have stabilized. and 107 would last me for donkeys.

Thank you all so much for the help :D 

Really love linux and the whole interface look damn better than windows when you install some xtra bits and bobs.

ps: whats the best antivirus program? I've been running Aeigus so far and firestarter for firewall.

---

### Post by Tiede on 2005-11-17
Euh... Easy answer... NONE!
Welcome to linux. No viruses running around.

---

### Post by Chayak on 2005-11-17
[QUOTE=Paragdim]ps: whats the best antivirus program? I've been running Aeigus so far and firestarter for firewall.[/QUOTE]

Antivirus program? Are you looking for windows viruses or something?

There have been very few linux virii made and none have ever spread very far.  A *nix virus will normally target a specific vulnerability in a particular program or service.  BIND, Apache, SSL to name a few.  If you don't run any servers and use some common sense (ie. don't use root as your user account...) you'll probably be more likely to get the bird flu than linux get a virus (Unless it was lindows which runs users with root permissions as default).

---

### Post by philipscard on 2005-11-20
Helpful advice above - apt-get clean/autoclean gained me over 600MB, no small fry on a 3GB disc! My installation is now down to about 1.5GB. 

Some other careless disc usage by ubuntu:
1. the folder ./thumbnails in my home folder was hitting 100MB with thumbnails of all pictures I'd ever put through the drive (1000s...). Easily removed.

2. I have an hfs+ partition with an old MacOS on, also used for storage from ubuntu. This acquired a folder 'HFS+ private data', tagged hidden in the MacOS and totally invisible to ubuntu, but which ubuntu filled with copies of many of the mp3/m4a files I opened in kaffeine, totalling 100s of MB. Easy to delete with ResEdit in MacOS, impossible to touch (it seems to me) with linux.

---

### Post by Cyril on 2005-11-21
Might wanna check for hidden files.  I recently found out there were tons of files  hiding in my trash folder.

---

### Post by marksi on 2005-11-21
If you're looking for a small install you might like to check out xubunutu. Check it out at [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu) It doesn't have all the features of Gnome or KDE but it is a lean desktop that does all I want it to.

---

### Post by Paragdim on 2005-11-21
My trash didn't have any hidden files. Thumbnails is big. But i noticed there is are some pics in there that i probably like to keep like cd covers that shows up in the players etc. Or are they stored somewhere else too?

Don't have any other partitions than hda1 and the swap. The size dosen't bother me too much. It just seemed at one point that everything was being gobbled up, but it's stabalised now so thats ok. But is funny that when I run the

> cd /
sudo du -ms * 2>/dev/null| sort -nr |more

command I only get 5gb of space used. Still my hda1 insists that I've used 45gb. Can't understand where the extra 40gb is hiding. But as mentioned earlier I've still got more than 100gb left which is plenty for my use.

---

### Post by Tiede on 2005-11-21
There must be a glitch somewere in there... I remember nautilus reporting the wrong amount of Free Disk Space while I was under Hoary... I don't know why, it just fixed itself one day amd it never happened again... So I think that the 40 Gigs are free but a miscaculation occured somewhere...

---

