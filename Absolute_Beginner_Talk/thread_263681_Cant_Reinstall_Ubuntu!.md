---
title: "Cant Reinstall Ubuntu!"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-23
Hi all,

I have (had) a dual boot system with 2 harddisk. Ubuntu and Xp were installed on the same harddisk.
I tried to reinstall ubuntu with the LiveCD. I did the following things:
1. Put the ubuntu cd and booted from it
2. After ubuntu loaded, I run Gparted and deleted the existing Linux partitions (/home, /root and /swap).
3. I made new ones in place of them and formated them to ext3 and swap (still with Gparted)
4. Closed Gparted and clicked "install", chose language, time zone, filled in name and user password etc..
5. Chose "manual edit partitions" and the scanning process of "prepare partitions" started (you know that orange block moving left to right and back)
And what now happens is that the process freeze (at the "scanning all devices"...!! First i thought the Cd was not ok, but i rewrited it.

If i run fdisk from the terminal with the Ubuntu CD, i see on the list all the partitions. If I delete the partitions with Gparted then is the list empty, except Windows Xp partitions.

Dont know what to do, how to solve this problem.

---

### Post by shashank on 2006-09-23
> **bubi1980 said:**
> Hi all,

I have (had) a dual boot system with 2 harddisk. Ubuntu and Xp were installed on the same harddisk.
I tried to reinstall ubuntu with the LiveCD. I did the following things:
1. Put the ubuntu cd and booted from it
2. After ubuntu loaded, I run Gparted and deleted the existing Linux partitions (/home, /root and /swap).
3. I made new ones in place of them and formated them to ext3 and swap (still with Gparted)
4. Closed Gparted and clicked "install", chose language, time zone, filled in name and user password etc..
5. Chose "manual edit partitions" and the scanning process of "prepare partitions" started (you know that orange block moving left to right and back)
And what now happens is that the process freeze (at the "scanning all devices"...!! First i thought the Cd was not ok, but i rewrited it.

If i run fdisk from the terminal with the Ubuntu CD, i see on the list all the partitions. If I delete the partitions with Gparted then is the list empty, except Windows Xp partitions.

Dont know what to do, how to solve this problem.
hey dont worry
1)logon to xp
2)right click the "my computer" icon and click "manage"
3)goto "disk management"
4)delete all swap and other linux partitions
5)re-run ubunto live cd
6)it shuld work now
7)and remember there can be 2 xp on grub boot now! one of the would work!

---

### Post by xpod on 2006-09-23
Try Gparted on it`s own live cd.
I too had problems when doing my re-install second time round.
Just did third one today with gparted to first create the partitions then used ubunto cd.

Dont know why it should be any different but it can have probs

---

### Post by bubi1980 on 2006-09-23
ok i gona try it again:)
thanks for the replies

---

### Post by bubi1980 on 2006-09-24
hi again,

I tried it in different ways, but while installing ubuntu it freezes!!
It freezes when the "scanning all devices" is running in "prepare partitions" after i selected manual edit partitions.
Dont know what do to, I tried it like you told me guys, but it still freezes.
 
I was on the way to switch over to Ubuntu, but i think i have to return now to windows xp.

---

### Post by xpod on 2006-09-24
Dont do THAT...try this..
I know it`s mad when it mabey worked before but live cd`s are a law unto theselves it seems.Try getting the "alternate" cd as i have had to do a couple o times....

Thats all I can suggest but it might be your pc and not the cd so im only giving you another possibility to try

---

### Post by bubi1980 on 2006-09-24
what do you mean by 'alternate cd'? is it a cd i can download or i have to order it?

---

### Post by bulldog on 2006-09-24
Can I ask why you have to reinstall in the first place?

Did you had some hardware trouble which makes a reinstall neccessary?

Running the live cd,are all of your hdd's proper recognized and readable when they are mounted.

Alternate cd is a textinstall based Ubuntu cd which needs less resources then the live cd what makes instaling Ubuntu easyer on your computer.
Also you should have the choice where you would install GRUB.

You just can download the alternate cd the same way as you did the live cd.

A good day Master XPOD,everything like it should be?

---

### Post by xpod on 2006-09-24
> A good day Master XPOD,everything like it should be?

Well THAT depends on your point of view bulldog my trusty friend:D 

The clan are all going to the mum in laws for dinner so I have some peace and quiet and THATS "how it should be"..:biggrin: 

BUT of course many people are still banging their heads on the ubunto "walls"
and THAT is something that "should`NT" be:D ...

"PPP" i say......patience,persistance and perseverance....:D

---

### Post by bulldog on 2006-09-24
BUT of course many people are still banging their heads on the ubunto "walls"
and THAT is something that "should`NT" be ...

Be prepared Master XPOD because I don't see a change in the near future.
But we'll help them anyway we can,don't we?

---

### Post by xpod on 2006-09-24
> But we'll help them anyway we can,don't we?

I was just asked if i had a life outside of this thing considering my many posts in such a short time.But as you may guess i have a very hectic life outside of ubunto and it`s forums but i am a great multitasker:shock: .....so if i can give someone a wee bit of encouragement OR point out the errors of their ways when they are telling us how crap it really is AT THE SAME time as i run around after my own large community then im a happy haggis

And thats WITH my many pc calamitys..

THIS is the only break i get FROM my mini clan:twisted: 
Or the only break they get from ME depending on your point of view

EDIT:....You can download the alternate cd at
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)
Scroll down

---

### Post by missmoondog on 2006-09-24
if you already re-partitioned the drive, why can't you just tell the installer to use the largest continuous free space? usually works very well then.

---

### Post by bulldog on 2006-09-24
> **missmoondog said:**
> if you already re-partitioned the drive, why can't you just tell the installer to use the largest continuous free space? usually works very well then.

Think the problem should be the same.

Can only talk about my experience and that includes ** not ** to preformat the hdd,but let the space unallocated.

Then choose manual partitioning and create the desired partitions in the unallocated space.

It has worked for me in the past,but have to say I only installed Ubuntu twice,once the 64bit,and now 32bit without a problem.

I used the the manner as discribed and created my folders but have to say,look twice before you apply and be asure the hdd which you want to alter isn't mounted,because a mounted hdd will not be formatted in any way.

I think this is the case [unmounting] in most of the trouble.

---

### Post by xpod on 2006-09-24
> It has worked for me in the past,but have to say I only installed Ubuntu twice

Ive only re-insatlled it twice too..(this month):D 
My original live cd worked a dream on this pc but when it came to my first re-install i had some strange problems with grub and booting....I ended up with the "alternate cd" which worked fine but NOW i use Gparted live cd for partitioning prior to installing..No doubt my own ignorance to start but i now have my own wee routine that works great.

I dont use any of them for windows IF it`s getting on the same hd(which it dosent now)....I resorted to using "fdisk" for any xp space THEN using gparted for the Ubunto stuff..

---

### Post by bubi1980 on 2006-09-24
thanks for the replies.

I still have some questions, if a choose for automatic installation what happens with my 2 existing partitions of windows (NTFS and Fat32, they are full with data, and they are on the same harddisk), will they deleted or messed up by automatic installation of ubuntu??

I had some problems with Grub after the unsuccesfull reinstallation (all linux partitions were deleted and reformated), i couldnt boot (to Windows XP) the computer because some grub error 17, which is fixed now by using the recovery console of windows xp and fixing the MBR.

I even tried to run the GParted Live CD, it worked fine, made all ex-linux partitions "unlocated" (first deleted etc..). After using the Gparted cd I tried to install ubuntu again with the ubuntu cd, but frozen again at "scanning all devices".

Actually I reinstalled ubuntu one week ago (on the same harddisk next to Windows XP), everything worked fine. Now it would be the second time to reinstall it, but cant get further then "scanning all devices" in the partition prepare section.

The reason I want to reinstall ubuntu (again) is because i downloaded and isntalled to much stuff, I experimented with ubuntu (because I am a newbie) and after a while i wasnt even able to change my desktop background...dont misunderstand me, everything was working fine, but i wanted to take a clean start again!

so thats it, [-o<

---

### Post by bulldog on 2006-09-24
You can let gparted do the partitioning by it self.

But it should be better to create a separate /home in case of a reinstall you can safe your stuff much easier.

It will not mess up your existing NTFS partitions,the only thing I ran into,it doesn't use all the free space I provided.

But as said look twice if you do your partitioning manually to be absolutely sure it's the way you want it.
Look which boxes are ticked and be sure no NTFS partition will be formatted  by accident.
Then you have to unmount the hdd and choose apply.

So there was space lying around on my hdd which was useless to me and I hate that:D

---

### Post by bubi1980 on 2006-09-24
I am still here waiting for solutions....

---

### Post by xpod on 2006-09-24
"Alternative" not an option then??

---

### Post by bubi1980 on 2006-09-24
I started downloading it, but why was I able to reinstall it one week ago without problems and if i try now its just impossible?;)

---

### Post by bulldog on 2006-09-24
> **bubi1980 said:**
> I am still here waiting for solutions....

Well make us a good offer and we'll be working for you alone :D

scroll a little back and read,then you can try,we are no magicans who can do it for you..........:|

---

### Post by xpod on 2006-09-24
> I started downloading it, but why was I able to reinstall it one week ago without problems and if i try now its just impossible?

Nobody was more confused by that than me when mine did it :D .
Just another point i forgot to mention but even when the original live cd did install to this pc i had to chose "safe graphics mode" at boot up..

Dont know why that was either(had less mem back then)
If i used normal mode it too stuck at stage 5\6 of the install....
Safe graphics mode whizzed along though:confused: 

I eneded up with live`s and alternatives of both Ubu,Kubu and even Xubu..

Got there in the end though.....Just the third pc upstairs needing it`s emergancy transplant now from the M.E it currently is:D ..

See what happens once you try that mate...hope it works

---

