---
title: "xorg.conf and mysterious errors--please help!"
date: 2006-09-20
forum: Apple PPC Users
---

### Post by k49 on 2006-09-20
I tried to boot my G3 iMac from both Ubuntu and Xubuntus CDs (which work fine on other computers), and got the same problems each time.

I read that I was supposed to to edit the xorg.conf file (like this: [http://www.ubuntuforums.org/showthread.php?t=234437)](http://www.ubuntuforums.org/showthread.php?t=234437)). I pressed control-alt-F1 to get to the command line, but before I could do anything, the following text appeared:

	Authentication token is no longer valid; new one required.
	You are required to change your password immediately (root enforced).

This repeats several times, and is followed by:

	* INIT: Id "1" respawning too fast: disabled for 5 minutes
	* INIT: Id "2" respawning too fast: disabled for 5 minutes
	* INIT: Id "3" respawning too fast: disabled for 5 minutes
	* INIT: Id "4" respawning too fast: disabled for 5 minutes
	* INIT: Id "5" respawning too fast: disabled for 5 minutes
	* INIT: Id "6" respawning too fast: disabled for 5 minutes
	* INIT: no more processes left in this runlevel

After this I can't do anything. If I wait, eventually the same text is printed out again.

Any ideas?

---

### Post by Melcar on 2006-09-20
This exact same thing happened to me when I installed a new HDD on my laptop and tried to install Ubuntu again.  I just started the Ubuntu install with the safe-graphics mode (it's one of the options from the LiveCD).

---

### Post by totvos on 2006-11-09
I had the exact same issue, and it was driving me insane! It happened both with Dapper and Edgy and, being very naive on all things linux, I had no idea how to get into "safe mode".

I did do the suggested "video=ofonly", to no avail.

My solution turned out to be very simple. Start using "live-powerpc", not the default "live". For whatever reason, that allowed Ubuntu to boot up "normally" (that is, with a black screen), but then the Ctrl-Alt-F1 did get me to a usable command prompt where I could then manipulate xorg.conf. BTW, I did not modify the bit depth value, and it worked just fine.

Hope this helps.

-- tomo

---

### Post by rafrombrc on 2006-12-13
I'm experiencing the same problem on a 400MHz G3 IMac.  It's happening for me using both Edgy and Dapper.  Both CDs used to work, and I was able to edit xorg.conf to launch the installer.  But due to partitioning problems I had to reboot, and after a couple of reboots neither of the CDs will work at all.  I've tried using 'live', 'live-nosplash', 'live-powerpc', and 'live-nosplash-powerpc' all to no avail.

Google finds this thread and some obscure posts in other forums related to advanced PAM configuration.  I'd be happy to edit the PAM setup if I were able to get to the console, but for now I'm completely locked out.

Does anyone have any idea what's going on, and how to get around it?

Thanks!

---

### Post by gooner on 2007-04-30
sorry to bring this old thread back to life, but i found the solution after running into this same problem. You have to set the macs clock to the correct time. I had this issue when the ppc thought it was some time n day in 1970.

---

