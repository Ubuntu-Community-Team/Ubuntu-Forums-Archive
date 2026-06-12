---
title: "Install Freezes at 15% detecting file system"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by PrairieShaman on 2007-10-26
I am installing ubuntu on my sisters Certified Data pc. I am using it right now, actually because I was able to install 6.06LTS on this system and it works fine.. The only problem is that I want to get her up to date running 7.10. This very same problem occurs with 7.04 also. 

I boot from the disc, and open the install. I follow through all of the windows and everything  is going good.. Once I click to confirm my installation settings it gets to 15% of the way done the install and the screen/computer freezes up and I have to restart the computer to get it to do anything. At 15% i believe it says "Detecting file systems" or something along those lines.. 

Any idea why this is happening?

---

### Post by agurk on 2007-10-26
Have you tried installing using the 'Alternate CD'? I've sometimes had better luck using that one than the 'Desktop CD'.

One other thing comes to mind: I remember the Ubuntu Edgy installer used to hang when there was no Internet connection available. You were able to solve it by pressing ctrl-alt-F1 and kill the offending process named ...update...something.

Sorry, that's all I can come up with.

---

### Post by PrairieShaman on 2007-10-26
thanks I'll give the alternate CD a try. 

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3610867](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3610867)

that thread is of people experiencing the same issue.. :guitar:

still not working though.

---

### Post by Toribor on 2008-01-18
I am having the exact same problem and the alternate CD wont work correctly. None of the options do anything, and it boots up just like the Live CD... Maybe I messed something up but I'm tired of downloading ISo's... after like the 3rd time... I'm about to completely give up on Linux. An install shouldn't be this buggy for so many people.

---

### Post by sweb on 2008-01-20
yes i have a 2 hard drive with the windows xp and when i try to install ubuntu in 15% the progress is freeze, i test it when my hard is empty (havn't any data in each partition) the progress will be gone good but when is have some data this progress is freezing.

**[COLOR="Red"]please remove this shamefull bug.[/COLOR]**

---

### Post by frup on 2008-01-20
Weird. what happens if you leave it and hour or two :D

---

### Post by zipperback on 2008-01-20
> **Toribor said:**
> I am having the exact same problem and the alternate CD wont work correctly. None of the options do anything, and it boots up just like the Live CD... Maybe I messed something up but I'm tired of downloading ISo's... after like the 3rd time... I'm about to completely give up on Linux. An install shouldn't be this buggy for so many people.


It generally isn't this buggy for most people. In fact it installs without problems for most people.

Please tell us which version you are using.

Please tell us what hardware you are installing it on.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-20
Also, when you boot up the live cd and get to the boot menu, select the verify media option and make sure it's not the media thats causing the problems.

-zipperback
:popcorn:

---

### Post by sweb on 2008-01-20
i use Gusty 7.10 . and i have test my media. the silver cd that cononical send to me.

i have 40gb and 80db both IDE hard drive.
i have 1700 Celeron with 256SDram.
when i want install i have this partiotion style:
[LIST]
[*]40gb :  **16gb *(NTFS) Windows XP* (2gb data is there) | 2gb *SWAP *| 6gb *UBUNTU *| 16fb *empty EXT3***
[*]80gb :** 20gb *Windows Programs FAT32* (2gb data is there) | 60gb *temprari drive FAT32* (just 10mb data)**
[/LIST]

first install windows xp and then want to install Ubuntu 7.10 ...

this problem is every time that i have to isntall ubuntu, i my only way to install without any problem where is my other hard drive is empty.

---

### Post by kernst on 2008-02-29
> **sweb said:**
> yes i have a 2 hard drive with the windows xp and when i try to install ubuntu in 15% the progress is freeze, i test it when my hard is empty (havn't any data in each partition) the progress will be gone good but when is have some data this progress is freezing.

Hi, all. I think I found a solution which may work for some folks....

Try running the installer without any preexisting filesystems mounted, or following the steps in my post at [http://ubuntuforums.org/showthread.php?p=4429985]("http://ubuntuforums.org/showthread.php?p=4429985#post4429985"), which basically involves unmounting all filesystems and killing off [FONT="monospace"]/lib/partman/commit.d/01unmount_busy[/FONT] to allow the installer to continue.

Hope this helps.

---

### Post by Randomperson_1000 on 2008-03-20
Ok i had the same problem and i found a fix (atleast it worked for me) plz keep in mind i am a ubuntu noob so i apologize for any incorrect terms beforehand.

my partitions -160 gb hardrive in total
                        50 gb vista drive
                        5gb recovery drive
                        80 gb for stuff
                        8gb partition
                        1.5 gb unallocated
i decided to install ubuntu on the 8gb partition and make the 1.5gb a swap partition
i had this problem where it wouldnt go past 15% from what i read there are two fixes, get more ram or kill the process that mounts the drive you are partitioning.
The second time i tried to install ubuntu it worked fine this is what i did:
1- when you are at the partition screen first set up your swap partition and select the option 'set to end'
2- now you can go ahead and set up your ubuntu files partition and normal and remember to set ot to the end like the previous one.

now it should work, the reason i think is that it partitions the swap first thus giving you more ram and while i was looking at gnome-system-monitor while the installation i was occurring my comp. was using some swap memory. I have read having more memory fixes this issue and this is what this fix will do.

---

### Post by some1l8 on 2008-05-25
or when partition hd, set each partition as main partition

---

