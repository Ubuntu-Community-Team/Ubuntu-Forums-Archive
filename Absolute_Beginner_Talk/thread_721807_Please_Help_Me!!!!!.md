---
title: "Please Help Me!!!!!"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by niko123 on 2008-03-11
Hi guys....i was installing vmware..then ran into a small problem...so i had to un-install vmwares folders...

so i used this command 
```

sudo rm -R 

```

but carelessly i removed folders that SHOULDT have been removed and now i cant even boot into ubuntu...it just stays there on teh loading screen!!!Can someone PLEASE help me!!! i am desprite to get back into my  desktop!! i have my ework there...PLEASEEEE I AM DESPRRITE!!!

is there a way that i can boot of the ubuntu 7.10 to fix it...or from a live cd...

PLEASE!!!!

PLEASE!!!!

can someone provide me a step-by-step guide...or a ...how to..anything!! please i need my work back!

---

### Post by JoshuaRL on 2008-03-11
Wow, scary command there.

What errors are you getting?  Can you boot into Recovery Mode?  If not, what errors come up from it?

---

### Post by 1010011010 on 2008-03-11
I may be wrong, but you may have deleted everything.  -r is recursive, I've never tried it without a folder name... perhaps it deleted everything below the directory you executed the command in.  Good luck.

---

### Post by bumanie on 2008-03-11
I don't think you can get anything back by using a live cd, however if you go here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) and burn this disc, it is quite likely you will be able to retrieve most, if not all what you have deleted. It is a good data/partition recovery tool.

---

### Post by natehall on 2008-03-11
Boot into your computer using a live CD. Depending on whatever directory you were looking at the time its gone. History. I hope you were not in the root directory. If you do manage to get a terminal just use the up arrow to see what you actually did. If you didn't erase it a file called .bash_history shows your terminal commands pretty far back.

---

### Post by niko123 on 2008-03-11
ok i will try what you guys are suggesting...

and no i wasent in the root directory...i remember that when i was using that command i knew where most of the vmware files were at...so then...i carelessly like an idiot...didt check before i type...what i typed..now that i rember i believe...sudo r -RM /usr/vmwar...that deleted what i needed...then i went on..to attempt to delete all the other vmware files......so im sure i deleted a little bit of ...everything...

::sigh:: im stupid...

it does show the screen of grub loading...but when it gets to the loading screen...it stops...

---

### Post by JoshuaRL on 2008-03-11
Can you try going into the Rescue Mode in the GRUB menu?

---

### Post by sports fan Matt on 2008-03-11
this is a PRIME example why checking with a mod before you use any of those commands are ESSENTIAL!  My motto is, I check over everything 2x or 3x before proceeding in anything I do..

---

### Post by handydan918 on 2008-03-11
Boot the live cd and use it to back up all your important work, like onto a cd or some external storage. Then just reinstall Ubu.
Make sure you verify the integrity of the backup before hosing your hard drive!

---

### Post by Papa-san on 2008-03-11
What in the world were you doing running that kind of command, anyways? Who informed you it might be a good idea?

There are about FIVE or SIX people in these forums who I would trust to coach me in a 'sudo rm <anything>' command! I'm pretty sure that any of the names listed in red on the home page of this forum as 'Moderators' would be trustworthy. I would never suggest that kind of command, but I don't want anyone to think if I said to do it that it would be a good idea... There is a really good possibility that anything you had on your system may never be seen again... I personally don't think ANYTHING is worth that. 

Take the time to search the forums to find the RIGHT way to do something, or at very least, ask in an open thread. (Keeping things in the light tends to keep the bad seeds out...)

---

### Post by niko123 on 2008-03-11
im like scared to boot from the live cd...and im scared to do anything with this at the moment...

but i was able to get into the recovery mode from GRUB....

but the script stops...at

run-init:/sbin/init: No such file or directory
[7.656000] Kernel panic - not syncing: attempted to kill init!
_

::cries::i cant believe this happened!

---

### Post by niko123 on 2008-03-11
> **Papa-san said:**
> What in the world were you doing running that kind of command, anyways? Who informed you it might be a good idea?

There are about FIVE or SIX people in these forums who I would trust to coach me in a 'sudo rm <anything>' command! I'm pretty sure that any of the names listed in red on the home page of this forum as 'Moderators' would be trustworthy. I would never suggest that kind of command, but I don't want anyone to think if I said to do it that it would be a good idea... There is a really good possibility that anything you had on your system may never be seen again... I personally don't think ANYTHING is worth that. 

Take the time to search the forums to find the RIGHT way to do something, or at very least, ask in an open thread. (Keeping things in the light tends to keep the bad seeds out...)

i hear ya...but no one had informed me to use that command...i just knew it...so seeing that i was gonna remove those folders...i decided to use that sudo rm <folder> command....

guess i should have just removed it manually 

::sigh::

---

### Post by bumanie on 2008-03-11
The live cd won't do any damage to your sytem as it unpacks off your optical drive and runs in ram. It doesn't touch your hard drive. I would still try test disk. It would be best to burn it on another computer if possible, because there is a risk that the more your use the drive with the information you wish to retrieve, the more likely something important will get overwritten.

---

### Post by niko123 on 2008-03-11
Question::

In grub when i press ESC  i can see
-ubuntu
-ubunto (recovery mode)
-memory

i already tried the recovery mode...and it stops...but is there a command...that i can fsck...or a fix...or ...any command...that i can jest get to the document folder..? anything?

---

### Post by SunnyRabbiera on 2008-03-11
Yeh you see this is why so many of us have the warnings about using sudo rm -rf, if someone told you to do that on this forum do us a favor and report them.
I like to personally apologize for your misfortune, but even in linux we have troublemakers.
No system is invulnerable and i am sorry you fell into someones trap

---

### Post by rmtatum on 2008-03-11
How are your partitions setup? Do you have / (the root directory) and /home on separate partitions?  If so, just reinstall Ubuntu and  your applications.  Your user settings are stored in /home and will not be affected by the reinstall.

---

### Post by bumanie on 2008-03-11
For the sake of repeating what has already been said, the files are gone as far as retrieving them with anything you have at your disposal now. Your only hope is to use a data recovery program - test disk is good. A lady a few weeks ago deleted her entire windows partition by accident and installed ubuntu over it. She retrieved nearly all her windows information back with test disk - she only complained a few photos were fuzzy. You are presently in a situation where you can't boot into ubuntu, you've removed the files + more stuff seemingly to do with the system files - you need to try a data recovery program. I don't think there is any other choice (at least I don't know of another choice and seemingly neither does anyone else on this forum). You can wait longer and see if anyone comes up with a better idea if you like.

---

### Post by stalkingwolf on 2008-03-11
if you can get a command line you might try sudo dselect    I used it earlier today to repair
a couple things.  But I got there from the rescue option.

---

