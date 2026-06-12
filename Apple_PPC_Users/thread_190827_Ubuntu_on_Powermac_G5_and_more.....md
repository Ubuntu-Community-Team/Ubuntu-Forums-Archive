---
title: "Ubuntu on Powermac G5 and more...."
date: 2006-06-06
forum: Apple PPC Users
---

### Post by elementxyz on 2006-06-06
Hi,
i just installed ubuntu 6.06 on my moms pc. Now i want ubuntu as my 2nd system on my mac. I have a few questions.
1. The important question for me is, is there now a programm who manages the fan ( i dont know if this word is right. I mean the air thing so that the machine is quiet like osx)
2. Is there a good how to anywhere which tells me the right way to have a dual boot osx and ubuntu?
3. What is with the 64bit?
4. Can i get the xgl desktop to run? (ati 9600 128mb)
5. Must i recompile every single programm?

thanks

---

### Post by tidris on 2006-06-06
You might want to wait a while before trying to install on a G5. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=189133](http://www.ubuntuforums.org/showthread.php?t=189133)

---

### Post by swartzfeger on 2006-06-07
[QUOTE=elementxyz]Hi,
i just installed ubuntu 6.06 on my moms pc. Now i want ubuntu as my 2nd system on my mac. I have a few questions.[/QUOTE]

snip

[QUOTE=elementxyz]2. Is there a good how to anywhere which tells me the right way to have a dual boot osx and ubuntu?
[/QUOTE]

This is what I'm currently dealing with (Tidris is referencing the G5 thread I started).

I'm very close to getting my setup working; basically, it's a matter of creating a boot partition *first* before installing Ubuntu, because Ubuntu/Kubuntu's graphical installer can't create the right type of boot partition for yaboot (HFS+).

Now that (I think) I have the boot partition problem solved, I appear to have some freezing issues during the install. I'm hoping to get through an entire install tonight with no freezes.

Bottom line -- do you have an extra hard drive in your Mac to install Ubuntu, or will you have to install on you primary disc?

---

### Post by snown on 2006-06-08
I am very interested in installing Ubuntu on my 17" powermac G4 as a dualboot like the thread starter is talking about. But in my case I can only use one drive, and I would prefer not to have to re-format, is there a way to do so?

thank you for your help

---

### Post by djroadrash on 2006-06-08
i would say this to people that are experimenting with their primary drive, back up all files and bookmarks because if u have any problems, u might have to erase your drive. unless u are very good at solving problems with booting partitions with grub or what ever u are going to use. i had to erase a linux-windows partition because i installed windows and could not boot linux after that, but it was a computer that was used for experimenting so i didnt have any data that was important.
good luck i imagine there are not very many g5's (i have one but i dont play with it, its the only one i have not even tried a livecd on.) to play with linux out there, it sounds like there are some problems installing ubuntu.  make a search on the forums im sure there are some answers out there.
:KS

---

