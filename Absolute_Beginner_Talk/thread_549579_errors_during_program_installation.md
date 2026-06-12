---
title: "errors during program installation"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by j0nes on 2007-09-12
Whenever i try to install a program via the add/remove feature, the installation details report that there were errors.  It seems to encounter the same problem regardless of the program i try to install.

For example, i chose a program at random called 'Alexandria' and watched the details while it unpacked and installed.  Sure enough, it gave the same error message.

E: proftpd: subprocess post-installation script returned error exit status 1

I should also add that about a week ago i installed GProftp just to try it out.  It installed without any errors, and i used it to download a readme file from the OpenBSD FTP site just to see if it worked.  And it did.

Since then i have not done any FTP'ing.

Now i encounter this problem with any programs i try to get.  Here is a screen shot, although it's not the clearest.

---

### Post by Harpoon on 2007-09-12
This sounds like a configuration problem in proftp.  I can't read the screenshot, so it is a guess.

Quick fix would be to go to the synaptic package manager, choose proftp and mark for complete removal (this will get rid of configuration fisles).  You can exit and try add/remove to confirm that it works, though it is unnecessary if you are already in the package manager.

Once you've confirmed things are working, select proftp and install.  This time, carefully not how you are configuring it.  It will help if the installers choke again.

---

### Post by Harpoon on 2007-09-12
I managed to get a readable screenshot.  I got the impression that programs would not install, but this does not seem to be the case.  E.g., alexandria appears to have installed properly, but then the system choked in trying to fix a failed proftp install.  Complete removal/ateempt to install again still applies.  If the installation chokes, post a new question with a title like "proftp install fails" to get quicker on target help.  Also include what version of ubuntu you are running (that is important)

---

### Post by j0nes on 2007-09-13
I'm using Ubuntu 6.10 Edgy...

I got the same impression that Alexandria did infact install, then it tried to finnish up something related to the FTP software.  Alexandria does work, but it crashes after a few minutes.  The bug reporting tool didn't know where to send it's info, so it told me to save it (i can post that info if you like).

Prior to making my first post, i did go into add/remove and un-checked the relevant FTP stuff.  I re-booted my machine (dont know if that was necessary) and then did the Alexandria install (the screen shot).  But as you can see, it still had the same problem.

If for some reason it's still hung up on this FTP software, is there a way that i can tell the system to skip, or forget about it?

Later this afternoon when i have some free time i will try to install another random program and see how that goes.  Alexandria could have crashed for some unrelated reasons i guess.

---

