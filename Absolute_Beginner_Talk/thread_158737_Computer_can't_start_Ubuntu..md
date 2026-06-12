---
title: "Computer can't start Ubuntu."
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Zieb on 2006-04-11
Well, I had about a week of problem free computing since my last problem and was feeling pretty confident in my ability to handle all my Ubuntu related problems (I got mplayer, XMMS, some extra totem abilities and a bunch of other stuff without having to ask for help).  Well, today while I was at work my fiancee phoned to tell me the computer was "broke".  
Well, in this case "broke" means that Ubuntu doesn't fully load up.  When it gets to the part where it says something like "checking root" it freezes for a minute and then I get something saying:
"fsck failed.  Please repair manually and reboot.  Please note that the root file system is currently mounted read-only.  To repair...
bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#   

Any help will be appriciated.

---

### Post by bixin on 2006-04-11
Well, last night I wondered why on earth does it give me the option to throw something in the trash, but I have yet to get that "simple" function to work. So being inquisitive I found chown, yes damage did ensue. I changed owner to root and holy hell did i lock myself out of everything. 

I got dircolors message. I managed to get back in by first loading grub into recovery mode, to do that when ubuntu first starts hit esc and it will give you the option for recovery mode. My problem was that i changed the owner of the /usr directory so I went terminal (funnay) and changed ownership back to me, reboot and while my gui login screen has disappeard( trying to fix that now) it brought me to the login command line, entered my user name and password, then just put startx and voila, I was in like flynn. You probably know this but in recovery mode you  have the gates to the kingdom, don't do anything unless your sure, it seems to have that permanent look to it. Not sure if it helps, but thats my .02:KS

---

### Post by Herman on 2006-04-11
Zieb, will the information in[ this link]("http://ubuntuforums.org/showthread.php?t=124774") (and in sub-links of that one) help you?
Regards, Herman.

---

### Post by Mustard on 2006-04-11
[QUOTE=Zieb]Well, I had about a week of problem free computing since my last problem and was feeling pretty confident in my ability to handle all my Ubuntu related problems (I got mplayer, XMMS, some extra totem abilities and a bunch of other stuff without having to ask for help).  Well, today while I was at work my fiancee phoned to tell me the computer was "broke".  
Well, in this case "broke" means that Ubuntu doesn't fully load up.  When it gets to the part where it says something like "checking root" it freezes for a minute and then I get something saying:
"fsck failed.  Please repair manually and reboot.  Please note that the root file system is currently mounted read-only.  To repair...
bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#   

Any help will be appriciated.[/QUOTE]

It sounds like there have been errors detected on your hard drive that need to be looked at.  To fix them you would need to use the fsck command on the particular device that has the problems.  The catch however is that fsck will not be able to check a mounted filesystem, and most likely the filesystem that needs checking is your root filesystem.  What this means is that you are going to need to get hold of a live CD, boot up in the live CD and then use the fsck command to check you **unmounted hard drive**.

When you get hold of a live CD, you can try this command to see the fsck manual...

```
man fsck
```

Press 'q' to exit the manual.

Basically your fsck command would look something like this..

```
fsck /dev/hda1
#this is assuming the device you are checking is called /dev/hda1
#it may well be different on your system for example
#you may have ubuntu installed on /dev/hdb1 with windows on /dev/hda1
```

It really depends on what the final result of the fsck command is as to whether everything will work again.  It could be that the hard drive errors are beyond repair.  Most likely however is that it has just become mixed up due to some improper shutdowns by the user or power outages as well as other causes.

---

### Post by Zieb on 2006-04-11
[QUOTE=Herman]Zieb, will the information in[ this link]("http://ubuntuforums.org/showthread.php?t=124774") (and in sub-links of that one) help you?
Regards, Herman.[/QUOTE]
Well, I'm typing this on my computer right now, so yes, those links did help. :D  Thank you very much.

---

### Post by Zieb on 2006-04-11
[QUOTE=Mustard]It sounds like there have been errors detected on your hard drive that need to be looked at.  
It really depends on what the final result of the fsck command is as to whether everything will work again.  It could be that the hard drive errors are beyond repair.  Most likely however is that it has just become mixed up due to some improper shutdowns by the user or power outages as well as other causes.[/QUOTE]
Actually, for awhile there I was having a problem where my computer kept resetting itself, but itpretty much went away for a week and then did it once more last night.  Could those resettings be the cause of the hardrive problem?  I was having some errors a little while ago and people here told me it was probably my RAM.  I took the both of my sticks of RAM out, cleaned the slots and put them back in and the problem seemed to have gone away.  Is it possible though that the resetting is caused by something being wrong with the RAM?  I got one stick free off of a friend used, so it's entirely possible that something was less than perfect with it.

---

### Post by Mustard on 2006-04-11
[QUOTE=Zieb]Actually, for awhile there I was having a problem where my computer kept resetting itself, but itpretty much went away for a week and then did it once more last night.  Could those resettings be the cause of the hardrive problem?  I was having some errors a little while ago and people here told me it was probably my RAM.  I took the both of my sticks of RAM out, cleaned the slots and put them back in and the problem seemed to have gone away.  Is it possible though that the resetting is caused by something being wrong with the RAM?  I got one stick free off of a friend used, so it's entirely possible that something was less than perfect with it.[/QUOTE]

It's entirely possible, but at this stage I couldn't definitively say 'yes, that's the problem'. :)

I think it would be worth monitoring the situation, and try to think of all possible hardware causes ie RAM failure, hard drive failiure, power supply failure, graphics card failure, overheating problems.  It's usually in the description of the symptoms of the problem, when they occur, what happens when they occur and what happens after they have occured etc. that some type of direction can be taken to diagnose the issue further.

Running the memtest from the grub menu at startup should give you an indication of whether your RAM is faulty in some way.  If you get errors during the testing of the RAM then it is a likely cause.  Again you would have to work through the issue with a process of elimination, as it could be a number of things in conjunction, not just the RAM on it's own.

---

