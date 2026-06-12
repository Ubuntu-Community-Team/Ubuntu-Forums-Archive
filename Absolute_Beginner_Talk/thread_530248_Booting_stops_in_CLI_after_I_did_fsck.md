---
title: "Booting stops in CLI after I did fsck"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by kptariq on 2007-08-20
Hi All,

I am just a newbie to the linux world.. so pls help me

I have an Ubuntu Desktop installed few weeks back and I ran "fsck" for fun [really, just wanted to try].. and looks like I am screwed.. system now stops at CLI while booting with the below message..I know I can get this rectified by running fsck [pardon me if this is wrong] again from CD.. but the problem is that I cannot connect a CD Drive [it's not allowed in my office]... So guys please give me an option if I can rescue my installation through any other means...may be using a pendrive.. give me the steps I need to perform to create a bootable pendrive and run fsck from that..

meesage while booting:
--------------------------------

…………..
………….
fsck: symbol look up error : fsck : undefined symbol : blkid_get_cache
fsck died with exit status 127 					[Fail]

*An automatic filesystem check (fsck) of the root filesystem failed

A manual fsck to be performed and system restarted

manual fsck must be performed in maintenance mode wit the root filesystem mounted in read only mode

* root filesystem is currently mounted in read only mode

After........press bla bla bla


bash : no job control in the shell
bash : groups : command not found
bash : lesspipe :  command not found
bla bla bla

the program apt-get currently is not installed . 
You can install it by typing apt-get install apt [Doesn't it look funny :-)]

$%$^%#$#: [I mean prompt]


Thanks in advance...

---

### Post by ukripper on 2007-08-20
you shouldn't have run fsck on filesystem when you already using it . Always boot through Live CD if you want to run fsck to check integrity of file system. Now lets try resolving your problem.

EDIT:
Try this link to make USB as a live CD
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by kptariq on 2007-08-20
Thanks a lot for the reply.. now I know it. :-( .. but I thought fsck is like running "error-checking" in Windows...problem is that I am new to linux ..I still think in "Windows" and execute commands in linux.. it will take sometime for me to change this..So pls help me.

---

### Post by ukripper on 2007-08-20
> **kptariq said:**
> Thanks a lot for the reply.. now I know it. :-( .. but I thought fsck is like running "error-checking" in Windows...problem is that I am new to linux ..I still think in "Windows" and execute commands in linux.. it will take sometime for me to change this..So pls help me.

No worries mate. I understand because in windows it asks you whether you want to run it and in linux it doesn't coz linux consider u as you are owner of your system not microsoft and you should know better. Also, that is how you learn from your own mistakes.

we are always here for help so don't hesitate ask anything

---

### Post by Dr Small on 2007-08-20
Does your screen look similar to this:
[http://ubuntuforums.org/attachment.php?attachmentid=28337&d=1174947464](http://ubuntuforums.org/attachment.php?attachmentid=28337&d=1174947464) ?

If so, try reading here:
[http://ubuntuforums.org/showthread.php?t=394375](http://ubuntuforums.org/showthread.php?t=394375)

Dr Small

---

### Post by kptariq on 2007-08-20
> **Dr Small said:**
> Does your screen look similar to this:
[http://ubuntuforums.org/attachment.php?attachmentid=28337&d=1174947464](http://ubuntuforums.org/attachment.php?attachmentid=28337&d=1174947464) ? 

The screen looks almost the same.. I think that's fine..

> If so, try reading here:
[http://ubuntuforums.org/showthread.php?t=394375](http://ubuntuforums.org/showthread.php?t=394375) 

I can't run fsck again.. it gives the message I quoted in first mai " fsck: symbol lookup error :fsck: undefined symbol : blkid_get_cache"

I can't reinstall fsck too.. apt-get isn't working either.. :-( 

-kpt

---

### Post by kptariq on 2007-08-20
--

---

### Post by kptariq on 2007-08-20
> 
Try this link to make USB as a live CD
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Do I really need to go through all this.. sorry if am asking a wrong question.. Is this OK just to create a bootable pendrive and run fsck from that...pshhh.. I may be thinking again in Windows.. I will need the instructions to create bootable pendrive and run fsck command from it... if my thinking is right..

---

### Post by mstephens on 2007-08-20
If  you installed it, I am unclear as to why you are unable to put it right booting from CD. It  must be a strange organisation that allows people to install new operating systems but doesn't allow them  access to their CD drive.

If its an official install, why don't you go back to the person who did it and say that it's stopped working and get them to re-install ? Its highly unlikely anyone would know what happened unless you told them.

---

### Post by kptariq on 2007-08-24
Reinstalling was the last option I wanted to try.. That's history even in Windows now.. Anyway.. I am sorry guys.. I did try couple of other options.. but eventually I had to reinstall..

---

### Post by ukripper on 2007-08-24
Is it working fine now?

---

### Post by kptariq on 2007-08-24
Ya... but it's completely a new OS.. I didn't have any data to loose.. That's way it was OK..

---

