---
title: "More Problems With Ubuntu 6.06"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-08
I have a gateway with 640 mb of ram,and a 20 gig hard drive. Being a n00b at this, i dont know exactly how to fix an operating system....but everytime i try and login to my account it gives me an extensive error message.......i can only login using a failsafe mode....any help would be appreciated

---

### Post by Fondor1 on 2006-08-08
Would it be possible to post the exact error message you recieve when you boot up normally?

---

### Post by Sniper99 on 2006-08-08
yes hold

---

### Post by Sniper99 on 2006-08-08
sorry...i meant to say hold on...that was rude...here is the message



the error message is 

your session only lasted less than 10 seconds. If you have not loggged out yourself,this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem (then there is a check box) (~/.xsession-errors file)


(if box is checked this appears)

/etc/gdm/PreSession Default:registering your session with wtmp and utmp

/etc/gdm/PreSession Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0" "spencer"

/etc/gdm Xsession:Beginning session setup...

Inconsistency detected by ld.so: ../sysdefs/i386/di-machine.h657:elf_machine_rel_relative : Assertion ` ((reloc->r_info) & 0xff) == 8`failed!

damn that was long...that is the exact line that is displayed...

---

### Post by OU812 on 2006-08-08
I've had this problem before, perhaps with an older release of zenwalk. I either was able to get past the error by rebooting until I was able to log in and then doing an update, or I just installed a different distro. Sorry that I can't remember. I mostly just wanted you to know that it's not necessarily an ubuntu-only problem.

john

---

### Post by Sniper99 on 2006-08-08
well...this being the newest version...and i know that people are also not having this problem....so i am thinking of just reinstalling the OS

---

### Post by Sniper99 on 2006-08-08
some other people have said to make a new user account...but i tried that and it didn't work

---

### Post by Fondor1 on 2006-08-08
I've been scouring the net a bit hoping for a clue as to what caused this.  So far I haven't been able to find anything.

As OU812 mentioned, it appears to be distro-independant.

Considering the install process usually doesn't take too long, if you have your data backed up I think it's safe to say a fresh install would do some good.

---

### Post by Sniper99 on 2006-08-08
yeah....i think the software might be corrupted so...thanks...i just needed someone to second my opinion....thanks again

---

