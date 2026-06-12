---
title: "Finally installed Ubuntu . . . need a quick hand"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by furiousV on 2006-09-13
I finally installed Ubuntu 6.06 on this system where SUSE 10.0 used to be.

I moved the two hard disks ("/" and "/home") over to a Dell system we recently received. Installation was a breeze.

Rebooted, put in my name and password, only to get an error message back. After a little messing about, I realise *all* of the contents in "/home" belong to root, and root only. So I chown all the files, no problem.

I log-in fine, add the rest of my family to the users, then chmod their home folders so they can log too.

Then I run "sudo apt-get update" and "sudo apt-get upgrade", let it download the 200+ packages. No problem . . . yet . . . 

I click on the Firefox button, only to be told that Firefox is already running, but not responding. I should kill the process or reboot the system. Hmmm. Run system monitor, but no Firefox there. Also run "ps -aux | grep firefox" nothing there. OK, I'll reboot the computer after the updates finish.

I leave the PC for a while, and my sister hops on, she clicks Switch User, and guess what . . . . first thing she clicks is Firefox, and that works no problem!

She finishes off, logs herself out, and I log back into my running session, updates have finished, and I try Firefox again, no luck. I reboot, log-in again, and find out the hard way that **KDE was trying to load!** 
Seems that the update turned my installation into Kubuntu, with the loadup/shutdown screens being Ice-Blue colours.
I manage to get back into Gnome, and yet Firefox still doesn't load. Now, Konqueror doesn't load anymore . . . it did before :???: 

Ironically, Firefox and Konqueror work fine for all the other user accounts, but mine. :-k 

In short: Firefox says it is running when it isn't. Konqueror doesn't start up at all - but ONLY in my user account. Works fine for everybody else.

Any suggestions guys?

Apart from that, Ubuntu is looking Kick-***! Looks great, works fast and has an amazing repository, finding more than I did in SUSE.
I'll figure out about turning it back into Ubuntu from sorta Kubuntu properly, and getting my Radeon 9800 Pro to use hardware acceleration, I saw threads on that floating about :)

---

### Post by Christopher Cook on 2006-09-13
I would reinstall Ubuntu or Kubuntu. Then make sure everything works right.

---

### Post by nalmeth on 2006-09-13
Are you using the previous Suse 10.1 /home ?

---

### Post by furiousV on 2006-09-14
> **nalmeth said:**
> Are you using the previous Suse 10.1 /home ?

It was a SUSE 10.0 install I had previously, which was a SUSE 9.1 install before, but the transition wasn't the smoothest there either.

One thing to note, I moved the contents of the /home hard-disk to the other one before I installed Ubuntu, which caused all ownerships to be root. I manually sorted this out myself.

I guess I could re-install, though that would be my last resort :-? 

In case it helps any, I installed from the Linux Format DVD (LXF83).

---

### Post by Leeghoofd on 2006-09-14
Reinstalling seems like the safest way to go about..
Alternatively you can also try to remove the KDE desktop environment. Command for this should be on this forum somewhere..

or try and see if this link is usefull
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by furiousV on 2006-09-14
> **Leeghoofd said:**
> Reinstalling seems like the safest way to go about..
Alternatively you can also try to remove the KDE desktop environment. Command for this should be on this forum somewhere..

or try and see if this link is usefull
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)


Thanks for the link. What I did last night was, I used Synaptic to remove Kubuntu-desktop and anything related, including Edubuntu-desktop, leaving just Ubuntu-desktop.

I think I shall go with the re-install now. Before I do so, is there any home folder dot-files I should remove, which might save another headache? Things like the KDE config files and so on.

---

### Post by hoagie on 2006-09-14
Start synpatic. Then search for kubuntu dektop. If it's installed unistall it. Also try to reinstall firefox using the synaptic package manager.:D

---

### Post by monktbd on 2006-09-14
i would try to remove/rename the hidden .kde config folders and the .gnome .gnome2 .gconf .gconfd folders to see whether it is a settings problem.
maybe remove/rename all the config folders you suspect to make problems.

---

### Post by furiousV on 2006-09-14
I got it sorted now guys! :D

I tried re-installing Firefox and Konqueror, but that didn't help.

I moved all dot-files/folders beginning with K and G(that looked like KDE/Gnome-related) as well as .mozilla to a seperate folder, and suddenly everthing works!

It also turns out all files/folders within dot-folders were owned by root (just my home folder) :confused: should be all sorted now.

I guess a full system re-isntall wasn't necessary after all :biggrin: 

Thanks for all your help everybody!

---

### Post by monktbd on 2006-09-14
> **furiousV said:**
> 
I guess a full system re-isntall wasn't necessary after all :biggrin: 


with linux this is very very rarely really necessary.

glad you got it sorted out :).

---

