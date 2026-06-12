---
title: "Bash comand not found when loading an exe"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-05-28
Hi,
Im trying to load FAH . I have created a dir and downloaded it however i cant seem to run it manually or view the license.  when ever i do i get this error
```
bash: FAH502-Linux.exe: command not found
```this is what i have done so far
```
mkdir /folding
cd /folding
wget http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe
chmod +x FAH502-Linux.exe

cd /folding
./FAH502-Linux.exe -license | less
```Im sure this is the same for any other .exe that i use 
Anyone know what I'm doing wrong?

I'm using this wiki as a guide :[http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux](http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux)

---

### Post by lazyart on 2007-05-28
You might want to do```
which FAH502-Linux.exe
```to be sure you're in the correct directory.

Do this:```
cd /folding
ls
``` and see what's in the directory.

---

### Post by dbott67 on 2007-05-28
Assuming that you're in the correct directory & preceding the command with ./,  the problem may be 64-bit vs. 32 architecture.  Are you running 64-bit?  If so, this is from another thread I posted in a few months ago.**  Tintazul** provides the answer at the bottom:

> **dbott67 said:**
> Well, how's this for irony?  I was googling for "folding at home dash bash linux" and got this hit:
[http://ubuntuforums.org/archive/index.php/t-314483.html](http://ubuntuforums.org/archive/index.php/t-314483.html)

Heck, I was evening trying to help the guy (I don't remember doing it though!).  Anyhow, here's what he did to fix it:

> [COLOR=Blue][B][I]Tintazul
December 11th, 2006, 06:24 PM[/I][/B][/COLOR]

Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, [COLOR=Red]here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs[/COLOR]. It's now working fine! The solution was found on this thread of the Folding Community forum: 64 Bit Linux Needs 32 bit compatibility libraries? [YES] ([http://forum.folding-community.org/viewtopic.php?t=17223](http://forum.folding-community.org/viewtopic.php?t=17223))

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

-Dave

---

### Post by Zzl1xndd on 2007-05-28
if you downloaded the latest FAH you should switch the 502 to 504 they don't update that in the instructions and it cought me off gaurd when I installed it.

---

### Post by pfwd.tech on 2007-05-28
hi i installed the 32bit libs and it ran fine untill the last part of the configuration i got this output and then it loop back to the user name part.
```
Change advanced options (yes/no) [no]? 
[17:28:13] Could not write MyFolding.html.

[17:28:13] Configuring Folding@Home...

User Name? 

```
i made sure that the dir was had chmod

---

### Post by dbott67 on 2007-05-28
I've never used FAH before, but if it's like SETI@home or other similar apps, it may be requesting your FAH user account info (generally, you would register a username at the FAH site and then the app would be able to track your stastics, join teams, etc.).

Do you already have a FAH account setup?

-Dave

---

### Post by pfwd.tech on 2007-05-29
Yeah ive had one for nearly a year now

---

