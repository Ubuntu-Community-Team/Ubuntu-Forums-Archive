---
title: "non stop problems with permissions root user downloads etc the list goes on"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by FOBBEDOFFWITHCRAP on 2007-09-24
HELLO PEOPLE
Why is it that linux makes it so difficult for noobs like me to get onthe linux ladder.
No sooner have you downloaded the program you have to set up this file that folder , commands for various programs that you haven't a clue how to do.
Its like sending a learer driver on a trip down the motorway , they haven't a clue what to do.
Ever time it try to install a program on my linux pc like avg anti virus for example , i downloaded the deb file in firefox it loaded up all ok and i try to do an update for it and all i get is that i don't have permissions , sorry but i am the only user on the pc am i missing something here.
The same with firestarter i downloaded it through snypix or whatever it is called and it download ok spent nearly all of last night to try and work out how to get the thing to load on boot up with piles of different answers but no success.
I have to say i like the whole ubuntu os apart from the permissions / files folders / sudo kawasaki cobblers.
Please help an avid ubuntu noobie
Cheers Dave

---

### Post by mikewhatever on 2007-09-24
To update AVG check out their manual. There is also a lot of stuff on installing AVG, here, I've even searched for you [http://www.google.co.il/search?q=avg+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=avg+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a). Anyway, that's AVG's problem, not Ubuntu's. Try to remember you are not in Windows, where the default user is also the almighty administrator, the dumbest approach possible. Read this for more [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions).
After installing Firestarter, it appears in System>Admin>Firestarter. Not sure what the problem was.
Overall, it looks like the source of your frustration is a strange expectation that Ubuntu should be like Windows. It is not, and there is a learning curve, like it or not.

---

### Post by arvevans on 2007-09-24
First, please let me assure that Linux is not Windows, and that it works a bit differently.  You may have to learn a few new ways to do things...just like you did when first learning to use Windows.

Part of the security features of Linux, and all UNIX derivatives, is the concept of permissions for almost everything.  Being the only user on the system does not eliminate the need for security or automatically give that user master control over the system.

In a Linux system you as a user own almost everything in your home directory (/home/username) but may have no permissions, or read-only permissions, for files and directories that are outside that area of control.  Others using your system via their own username will have control of only that which resides in their own /home/username space, but will not normally have access to your area of control.

Specifically in Ubuntu Linux, the concept of a super-user has been further modified from other UNIX-like OS in that it is not possible to log into the system as the "root" user.  This is good because if minimizes a number of possible security problems.  In Ubuntu, the first user ID defined at install time also sets the "root" password, and that user can use root permissions along with this password to perform system administration functions.  This is accomplished by using one of the several commands that temporarily give this ID super-user privileges (sudo, gksudo, etc.).  But, even this first user does not operate routinely in a root or super-user mode. When doing administrative tasks you still have to invoke root privileges by using the appropriate command and giving the password.

There are a number other differences between UNIX-derived OS and CP/M derived ones.  As you become more familiar with network-centric operating systems such as Linux, OS-X, BSD, UNIX,, etc., you may come to prefer the flexibility, security, and robustness that these systems provide.

Arv
_._

---

### Post by skyjacker on 2007-09-24
> **FOBBEDOFFWITHCRAP said:**
> 
The same with firestarter i downloaded it through snypix or whatever it is called and it download ok spent nearly all of last night to try and work out how to get the thing to load on boot up with piles of different answers but no success.
You need to realize that Firestarter is only a GUI to tweak aptables (which is the firewall in Ubuntu). This program runs whenever you start Ubuntu. After you are in the user window, if you wish to monitor what Firestarter is doing you should enable it under Apps, internet,firestarter. it will then be active. Don't fret, Ubuntu is different, but if you download programs with add/remove programs, it will be easier because it downloads, extracts, &installs in the proper place.

---

