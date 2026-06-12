---
title: "Newbie Installation problems"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by oxboy on 2005-12-27
Hi all!

I'm new to linux/ubuntu and decided to give it a try.  I followed the dual boot (ubuntu + NTFS) instructions from one of the posts.  The link I went to is this: 

[http://www.users.bigpond.net.au/hermanzone](http://www.users.bigpond.net.au/hermanzone)

Stage 1 of the installation went smoothly.  I was able to re-partition and install grub and was able to select ubuntu as my OS to load.  I reached the part where there is the black screen that loads modules, and also the part that takes some time installing packages, but when it finishes, all I get is an underscore on the upper right corner and  a black screen.

I tried rebooting the computer, and again, I get to the load module screen, and when it finishes, I get a blinking underscore on the upper right corner that eventually stops blinking and my system kind of freezes.

I don't get any error messages (or at least not that I know of)... just a blank screeen.  

System Specs:
Intel Pentium 3, 800 MHz
512 MB RAM
Radeon 9200

I'm sorry for not being able to give any more indication of what the problem might be.... I wish I had some sort of error msg or something I could post but I don't get anything.  I've tried reinstalling a couple of times but I get the same problem.  Any ideas?

Thanks very much for your help!

---

### Post by pelle.k on 2005-12-27
My first thougt is your X server isn't working or something...
If you press control+alt+F2 this should take you to a command prompt (Do this when you see nothing).
So what happened?

If that's not the problem. try starting with the recovery mode in grub. let us now how it went...

---

### Post by Herman on 2005-12-27
oxboy, well I don't know why, but it happens to me sometimes too, and I usually just mutter something unprintable at my old computer and put the CD back in the drive, delete all the partitions (except the XP one), and start over again fresh, hoping for better luck next time. That's the simple solution, and it usually works for me. (Persistence, perseverance, repetition, and dogged determination).
There is quite possibly a more scholarly and gentlemanly approach, something involving a neat command, like may be typing 'startx' or something similar.
A search of the forums here using the search function is likely to reveal quite a number of good, logical, sensible methods for dealing with this that would be better than my simple but time consuming way. This problem has been reported before. I'll start searching now and see if I can turn up something. :D (Herman)

EDIT No1: It looks like pelle.K has you on the right track - thanks pelle.k

EDIT No.2: Here are links to three of the most promising looking threads I've read so far on this subject:
[http://ubuntuforums.org/showthread.php?t=107398&highlight=black+screen+install]("http://ubuntuforums.org/showthread.php?t=107398&highlight=black+screen+install")
[http://ubuntuforums.org/showthread.php?t=93540&highlight=black+screen+install]("http://ubuntuforums.org/showthread.php?t=93540&highlight=black+screen+install")
[http://ubuntuforums.org/showthread.php?t=90497&page=2&highlight=black+screen+install]("http://ubuntuforums.org/showthread.php?t=90497&page=2&highlight=black+screen+install")

---

### Post by oxboy on 2005-12-27
[QUOTE=pelle.k]My first thougt is your X server isn't working or something...
If you press control+alt+F2 this should take you to a command prompt (Do this when you see nothing).
So what happened?

If that's not the problem. try starting with the recovery mode in grub. let us now how it went...[/QUOTE]

I tried pressing ctrl+alt+F2 while the underscore was blinking and when the screen was blank.  Nothing happens =/.  I went into recovery mode and typed in startx it tried to load something but then the screen goes blank again.  

I will try re-installing it again and see what happens... but I've tried doing that before and I got the same problem =/.

Is there anything I can type into when I'm in recovery mode to look for some errors that could help indicate what could be the problem?  (although i think pelle.k may be right in that the x server isn't running)

---

### Post by pelle.k on 2005-12-27
:) well if recovery mode works for you, then theres hope...

I would say:
First login yourself. If thats already done by the system you should see a # at the prompt. Thats because you are super user or root, when using recovery mode.

If you want to take a look at som log, type "nano /var/syslog" use page up, page down to scroll up, down. control+X to quit. but i think you will see mostly jibberish. ;) 

Bite the bullet and and use this haxxor comand "dpkg-reconfigure xserver-xorg" this will ask you som questions, press return for default answer for the most part, but be sure to choose ati or radeon as your x-server, because you have a 9200 right? :)

what are you waiting for! report back when you are done! :D

---

### Post by oxboy on 2005-12-27
Sorry for taking so long but I think it worked! Thanks pelle.k! Thanks Herman!

---

### Post by pelle.k on 2005-12-27
You're welcome, and remeber that i've been in the same situation swearing and cursing many times before. :)

Don't hesitate to ask about anything else, but remeber that the search funtion is your friend too. The search menu here at ubuntuforums is really cool. thread history and stuff.

---

### Post by Herman on 2005-12-27
Well done oxboy and pelle.k :D An excellent show! Congratulations! :D

---

