---
title: "Not seeing my processor"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-10
I am using dapper 6.10 and when i goto device manager it shows unknown for my processor which is a amdx2 4200+ and i have a asus a8n deluxe mobo
it does not allow me to install amd64 things and does not allow me to do 64bit while i think this os is 64bit and my processor is 64 bit

---

### Post by lyceum on 2006-12-10
To make sure I am reading this right, you have a 64 bit processor and you installed 6.10 on it. Was it the normal Ubuntu 6.10 or the 64 bit version?

---

### Post by synt4xerr0r on 2006-12-10
> **lyceum said:**
> To make sure I am reading this right, you have a 64 bit processor and you installed 6.10 on it. Was it the normal Ubuntu 6.10 or the 64 bit version?

How can i know its 64bit OS? and if its not is it possible to upgrade to 64bit os without losing my files and settings

---

### Post by taurus on 2006-12-10
This command will tell you!

Applications -> Accessories -> Terminal
```
uname -a
```
And if you want to run it as 64bit, then you need to reinstall it...  In other words, backup your personal/important files before you do anything!!!

---

### Post by haxer on 2006-12-10
Pick out the cpu from the case and look at it :) ... no seriously did you even install 64-bits 6.10 ubuntu on your computer? ;)Aha already answerd :(

---

### Post by synt4xerr0r on 2006-12-10
Linux SyntaxError 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

---

### Post by taurus on 2006-12-10
```
Linux SyntaxError 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 **i686** GNU/Linux
```
It's an x86 version...

p.s.  Dapper is 6.06 while Edgy is 6.10.  Therefore, you are running Dapper because of the kernel version that you have.

---

### Post by synt4xerr0r on 2006-12-10
> **taurus said:**
> ```
Linux SyntaxError 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 **i686** GNU/Linux
```
It's an x86 version...

thought so

well i guess i will start backing up now thanks all

---

### Post by lyceum on 2006-12-10
> **synt4xerr0r said:**
> How can i know its 64bit OS? and if its not is it possible to upgrade to 64bit os without losing my files and settings

When you down load Ubuntu it gives you some options. If you took the first one on the list, it is the 32 bit. It will work fine, maybe better as there aren't too many 64 programs that I know of. You would just not be using your PC to ts full potential. 

As for an upgrade as mentioned above, you would need to do a clean install. I would hang out for a week before doing anything. Download the 64 bit version, just check it out, and it is the 3rd one down. 32 bit, Mac then 64 bit & servers (other install option). I would use the live disk for a week to see if you notice a difference. IF not, I would leave it as is. But that is just me.

Also, I checked the US for the download info. I am not sure where you are from.

---

### Post by taurus on 2006-12-10
You can't judge the speed of x86_64 from running off the LiveCD since the LiveCD is slow comparing to running off from the harddrive!

---

### Post by igknighted on 2006-12-10
If you create a new partition and copy your /home directory onto it, you can then reinstall, mount the new partition as /home via the installer, and then set up the same username as before, you will have all your files and settings restored.

---

### Post by lyceum on 2006-12-10
> **taurus said:**
> You can't judge the speed of x86_64 from running off the LiveCD since the LiveCD is slow comparing to running off from the harddrive!

Hmmm... good point! Did not think of that. ](*,)

---

### Post by synt4xerr0r on 2006-12-10
> **igknighted said:**
> If you create a new partition and copy your /home directory onto it, you can then reinstall, mount the new partition as /home via the installer, and then set up the same username as before, you will have all your files and settings restored.

Could u tell me that in more detail and how to do it exactly bcuz i rly dont want to f this up

---

### Post by synt4xerr0r on 2006-12-10
> **igknighted said:**
> If you create a new partition and copy your /home directory onto it, you can then reinstall, mount the new partition as /home via the installer, and then set up the same username as before, you will have all your files and settings restored.


> **synt4xerr0r said:**
> Could u tell me that in more detail and how to do it exactly bcuz i rly dont want to f this up

Ok im sorry for asking these stupid questions and double posting but plz just answer that bcuz i rly dont wanna mess up

---

### Post by taurus on 2006-12-10
You need to have an empty partition for it to work.  You first mount that empty partition somewhere and copy /home to that partition.  Then reinstall and now mount that partition to /home but do not format it.  That's why all your personal settings are reserved and you don't have to start from the beginning again...  

That's how you would do it.

Otherwise, read this...  [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by igknighted on 2006-12-10
Use synaptic to install a program called gparted.  With this program you can resize a partition, so I would recommend shrinking your Ubuntu partition by a large enough amount so you could have a decent /home drive later.  Then you can create a new partition in the space left over, formatted in ext3.  Once you get this far, post back and I will tell you how to mount this new partition.

---

### Post by taurus on 2006-12-10
> **igknighted said:**
> Use synaptic to install a program called gparted.  With this program you can resize a partition, so I would recommend shrinking your Ubuntu partition by a large enough amount so you could have a decent /home drive later.  Then you can create a new partition in the space left over, formatted in ext3.  Once you get this far, post back and I will tell you how to mount this new partition.
You have to use gparted from the LiveCD if you want to resize partition with Ubuntu on it because you **cannot** resize partition while it's in used...

---

### Post by max.diems on 2006-12-10
There isn't much point in bothering with the 64 bit version for now. Save yourself the trouble of a reinstall and stick with 32 bits.

---

### Post by synt4xerr0r on 2006-12-10
> **max.diems said:**
> There isn't much point in bothering with the 64 bit version for now. Save yourself the trouble of a reinstall and stick with 32 bits.

Why do u believe?

---

### Post by drphilngood on 2006-12-10
> **max.diems said:**
> There isn't much point in bothering with the 64 bit version for now. Save yourself the trouble of a reinstall and stick with 32 bits.

I agree.  You will run into problems with 64bit that you wouldn´t have with 32bit.

---

### Post by synt4xerr0r on 2006-12-10
> **drphilngood said:**
> I agree.  You will run into problems with 64bit that you wouldn´t have with 32bit.

A question: the 64bit capability will only work with certain programs or what?

---

### Post by igknighted on 2006-12-10
For simple day to day tasks (email, web surfing, etc) you will probably find more trouble and very little performance gains.  If you are doing very processor intensive stuff (compiling source code, video editing, etc.) then I would recommend going to 64 bit because you will see some significant speed gains.

EDIT: If you really want to try 64bit, you might want to try a different distro (like SUSE).  Ubuntu users frown upon 64bit because it is not well integrated with existing 32bit apps, however many other distro's (such as SUSE) do not have this issue.  You might want to try a few distro's before you settle down.

---

### Post by drphilngood on 2006-12-10
> **synt4xerr0r said:**
> A question: the 64bit capability will only work with certain programs or what?

It is harder to get many programs, especially those media related, to work with 64bit.  See here for more information:

[Firefox 1.5, Flash and Java in AMD64 Ubuntu]("https://help.ubuntu.com/community/FirefoxAMD64FlashJava")

With 32bit, you can install most all with Add/Remove which is much easier.

---

### Post by synt4xerr0r on 2006-12-10
> **igknighted said:**
> For simple day to day tasks (email, web surfing, etc) you will probably find more trouble and very little performance gains.  If you are doing very processor intensive stuff (compiling source code, video editing, etc.) then I would recommend going to 64 bit because you will see some significant speed gains.

Thanks for the help mayb later on i might install it right now i will stick to 32bit thx for all the help igknighted and all

and i know this is totally of topic but is it possible to skin the terminal
edit: nvm i found out

---

### Post by Brownedwg89 on 2006-12-10
I haven't had that much of a problem with 64-bit. Everything I want to do works...

all you need to do is use this script to install firefox and its all set
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

---

