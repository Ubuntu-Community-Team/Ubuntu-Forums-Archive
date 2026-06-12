---
title: "Problem logging in on powerpc"
date: 2009-04-15
forum: Apple Hardware Users
---

### Post by newbiexubunt on 2009-04-15
I installed the alternate version of ubuntu jaunty jackalope on my Mac Lombard Powerbook G3 (PowerPC).  It installed successfully but will not let me log in.  It keeps saying I have the "wrong username/password".  I re-installed and tried again but the same thing keeps happening.  What should I do?

Thanks!

---

### Post by cyberdork33 on 2009-04-15
> **newbiexubunt said:**
> I installed the alternate version of ubuntu jaunty jackalope on my Mac Lombard Powerbook G3 (PowerPC).  It installed successfully but will not let me log in.  It keeps saying I have the "wrong username/password".  I re-installed and tried again but the same thing keeps happening.  What should I do?

Thanks!
boot into recovery mode and change the user password.

---

### Post by random_mike on 2009-04-24
Yes exact same thing happens to me, I've installed ubuntu 3 times already. I'm sure I did not mistype Username/Password. I'm on a G4 1.5GHz 17" Laptop.

Must be a install bug.

BTW, how do you boot into recovery mode on a powerpc install?

---

### Post by tiresia on 2009-04-24
> **random_mike said:**
> BTW, how do you boot into recovery mode on a powerpc install?
Boot from the alternate CD and press TAB at the yaboot prompt

---

### Post by random_mike on 2009-04-24
Thanks, but i can't get to the recovery console, screen just stay black.

I used tab then typed "boot: Linux single".

Thanks anyway, time to buy a new computer i guess

---

### Post by moocow1452 on 2009-04-27
Try burning the powerpc daily at the lowest possible speed you can, 1x is preferable. Then reformat and reinstall. Worked for me with the live.

---

### Post by jazzop on 2009-05-03
Can anyone give a helpful recommendation for dealing with the original problem (unable to login following install/upgrade to 9.04) that does not involve:
(a) having a CD
(b) reinstalling the whole damn system
(c) anything to do with GRUB, since ppc platforms use Yaboot

?????

I just upgraded via Synaptic from 8.10 to 9.04 and it won't let me login even once.

---

### Post by tiresia on 2009-05-03
At the second yaboot prompt, where you can choose a Kernel type ```
Linux single
``` After that you should be able to work as root. You can add another user. At this link you can see how the command 'adduser' works
[http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html)
Please, read the link above carefully, you may want to add your /home directory and to specify to which group your new user belongs

---

### Post by jazzop on 2009-05-03
> **tiresia said:**
> At the second yaboot prompt, where you can choose a Kernel type ```
Linux single
```

Doesn't work.  I get the following:

[COLOR="Blue"]Please wait, loading kernel...
/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:3,\\linux: No such file or directory
boot:[/COLOR]

As you can see, it just returns me to the boot prompt.  The only "option" I appear to have is to hit [enter] and it boots to the ubuntu login screen.

---

### Post by tiresia on 2009-05-03
Can you please press TAB at the (second) yaboot prompt and post here what you get?

---

### Post by jazzop on 2009-05-03
I get:

[COLOR="Blue"]linux               old[/COLOR]

If I type either "linux" or "old", I end up at the same point-- the ubuntu GUI login screen where it won't accept my login.

---

### Post by tiresia on 2009-05-03
Sorry, if I repeat the same, but you should try to boot like this```
linux single
```

---

### Post by stream303 on 2009-05-03
Be SURE you are using the proper capitalization and make sure that Linux is entered at that second stage boot prompt with a capital L.  Otherwise, the system will look for a lower-case linux kernel and not find it.

After booting up with **L**inux single, you should be presented with a text-based recovery menu.

The goal here is to try the quick fix and get the updates.  With ethernet connected, cursor-down and choose

**netroot**

Then at the prompt, get the updates:

```
apt-get update
```

You don't need to precede the command with sudo since you are already root as Linux single.

If this doesn't work after a reboot, at least you can get to a root prompt to take other actions if needed.

---

### Post by jazzop on 2009-05-03
Nothing worked.  I don't have time for this BS, so I just reinstalled 8.10 and I will leave it at that.  Based on the pages and pages of gripes about install- and upgrade-related bugs with 9.04, I'm beginning to think this should not have been released yet.

---

### Post by Edman274 on 2009-05-07
I had an identical situation with Ubuntu Server 9.04 for PPC. Like OP, I reinstalled more than five times and tried to boot to recovery disk, and tried single user mode. Every single time it asked for root's password. What's aggravating is that since root's not enabled by default, I have no ability to enable it since I can't log in even once. 

Like OP, I'll have to deal with going back to 8.10. I guess since PPC isn't officially supported I can't fault Ubuntu for this bug but it sucks all the same.

---

### Post by mkvnmtr on 2009-05-07
These are problems I have never encountered on my G4 Ibook. Every time I upgrade it is something different but never anything this serious. I always seem to try another method to upgrade and get a good stable system. This time 9.04 seems to be working well but I wonder how long it will last. I sometimes think it is time for my Ibook to die but it just won't quit.

---

### Post by moviemaniac on 2009-05-20
I just ran into the same bug installing Jaunty PPC on a 12" PowerBook G4 with the alternate CD. Investigated with an old 8.04 Desktop CD and found out that the Jaunty-installer didn't even create the user (not even the home-folder!) - no wonder I can't log in.

As the "Linux single" boot-option doesn't boot into a shell but brings up the graphical login-screen I'd say I'm royally fu***d.

The bug is also perfectly reproducable (already installed twice).

---

### Post by stream303 on 2009-05-20
We may be seeing a combination of problems here.  If it is just the inability to enter the user password, even though you know it was good during setup, you can try this:

At the second-stage yaboot boot: prompt, hit TAB to stop the countdown.  Then

```
Linux nosplash rw init=/bin/bash
```

then at the prompt, change the user password:

```
passwd <username>
```
where <username> is the name of the user you chose to make initially.

reboot the machine,
```
reboot
```

See if this gets you into your normal account after reboot.

However, in the other case where /home doesn't even seem to be created, I'm not sure what is going on there.  About the only thing I can think of in that case is ask if you are dedicating the entire disk by letting guided-partitioning "use the whole disk", or are you deleting older partitions from earlier installs before trying to install 9.04?  Is it a free-space issue where the installer just installs as much as it can and not notify you that it didn't have enough space to really complete the install?  Hmmmmm..

---

### Post by moviemaniac on 2009-05-20
well, in my case I was dedicating my entire disk (80GB) to Jaunty. Even a manual partitioning with a separate /home partition didn't change anything. However I now used the Desktop-CD and the installation went well so that's at least a workaround.

---

### Post by stream303 on 2009-05-20
You may have stumbled across something - 99% of the time I use the "alternate" installer.  However when I used Jaunty, for the first time in my life I used the desktop installer.  No troubles.

We'll have to keep an eye on this and see if A) upgrades bork - not unheard of, and B) there might be something wrong with the alternate-installer for Jaunty.

Let's keep our eyes peeled for any further reports!

---

### Post by Biggysmiles on 2009-05-21
I also ran into this problem after upgrading a 12" powerbook g4 to Jaunty 9.04.  I managed to login after doing the following: 

Got to the root prompt after using stream303's suggested boot: ("Linux single" also didn't work for me)

Linux nosplash rw init=/bin/bash
[FONT=monospace]After getting to "root@(none):" I tried "passwd <username>"

[/FONT]passwd: Authentication token manipulation error
passwd: password unchanged
[FONT=monospace]
I then tried "adduser test" (successful), created a password, and rebooted.  Still no joy, same result for all users.

I booted to recovery mode again, verified that /home still had my original user and "test" user directories (it did) and tried changing the password again for test (successful) and for my original user (failed). (not sure if changing the password was significant or not so I'm making a note of it) 

From another thread someone suggested typing "pwconv" with success so I tried it and rebooted.

After rebooting my original user failed to login but "test" user and password returned the message "adding user test" and logged me in!

I booted to recovery mode again to see if I could repeat the "authentication token manipulation error" when changing my original user password but this time it was successful.  I was able to login with my original user after rebooting.

I'm not sure which actions did the trick as I'm a noob but maybe it'll help.





[/FONT]

---

### Post by stream303 on 2009-05-21
NICE WORKAROUND!  Reports like that make my day for sure.

I wonder if we can simplify the process...maybe:

1) Get into rescue mode with Linux rw init=/bin/bash

2) run pwconv

3) Just delete your existing user and add it back again?

```
deluser <username>

adduser <username>
```

4) reboot.

Maybe this will do the trick.  Wish I knew if it was a PAM issue, something hardware-related like the G4 powerbook clock somewhow messing with the password file entries.....

Anway, glad you got it running and thanks again for the detailed work around.  1st-post to boot!

---

### Post by johntoups on 2009-07-07
This variant was almost exactly my fix.  I installed 9.04 and was unable to login. I followed the procedure quoted below, with the minor exception that the deluser command failed - *user did not exist!*

I performed an adduser as below, but before rebooting ran **visudo** and duplicated the root user sudo permission line for my new user.  I am now functional.

Subjective diagnosis - the install failed to create the user.

This answer also applies to [this]("http://ubuntuforums.org/showthread.php?p=7576840") thread...

> **stream303 said:**
> NICE WORKAROUND!  Reports like that make my day for sure.

I wonder if we can simplify the process...maybe:

1) Get into rescue mode with Linux rw init=/bin/bash

2) run pwconv

3) Just delete your existing user and add it back again?

```
deluser <username>

adduser <username>
```4) reboot.

Maybe this will do the trick.  Wish I knew if it was a PAM issue, something hardware-related like the G4 powerbook clock somewhow messing with the password file entries.....

Anway, glad you got it running and thanks again for the detailed work around.  1st-post to boot!

---

### Post by Vlammetje on 2009-10-28
Well, thanks for the tips! I managed to create a user with a working password, nbut that had to be the end of the joy. There is no group admin on my system, and I do not know how to create one. Thus my user has no sudo rights, and I am stuck now :(

Any suggestions?

---

### Post by dragonhunter on 2009-11-07
Hi Guys

I've have an eMac power pc at the school that I work for, and I was founding exactly the same problem as most of you. I've followed Stream303 and BiggySmiles tips but no success. Then I figured out as BiggySmile said that PAM has a problem with dates, and as most of those computers already has a certain age the CMOS battery doesn't hold the date anymore.
So to make a workaround on this issue I would suggest to do that

1) Get into rescue mode with Linux rw init=/bin/bash

2) run pwconv

3) Change your system time with "date -u MMddhhmmYYYY"

4) Synchronize your CMOS time with the system time using "clock -w"

5) adduser --home /home/<username> --ingroup sudo <username>

6)exit


At this point my machine said there was something wrong with the filesystem and didn't boot up. So I've restarted it into single mode without mounting the filesystem to run the fsck

Linux nosplash init=/bin/bash

then

fsck -ry

Restart it and everything was working perfectly!

Hope it helps!

---

### Post by 96fps on 2011-08-30
I'm having the same problem here (installed Ubuntu 9.04 ppc using the alternate cd), along with me needing to edit xorg.conf as I'm using a very picky iMac G3. I had the same problem when i installed bare-bone debian from a net-install disk without internet on the iMac. It may be inherited from the new ppc debian releases(?), but i have no idea. also sorry for resurrecting an old thread.

All the suggested solutions ask me to login (or do after i hit control-option-f1 when the launch X.

Someone told me i should try installing ubuntu 6, and upgrading from that.

~thank you for reading this.

---

