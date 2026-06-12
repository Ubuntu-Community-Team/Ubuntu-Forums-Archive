---
title: "Install Problems - going bald fast!!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Gannett on 2007-04-06
I've searched the forums for help on this one, but nothing seems to help specifically for my system.

I am trying to install from the 6.10 live CD. The menu appears, but when I choose "Start / Install Ubuntu", the screen goes blank, then a load of text and the message "Kernel Panic, failed to synch, attempted to kill init".  

My system:  Intel Pentium4 3.2GHz, 512Mb memory, ATI Radeon X800 Pro.

I understand it is a problem with the X800 Pro.  I've tried the following, from various forums:

Pressing F6 and editing the boot settings - removing "quiet splash --" or adding "nofb".

I've seen alot of info for loading the ATI drivers using the command line, but I can't get that far.  

I've got really frustrated, I'm sick to the back teeth of Windows and Ubuntu looks best for me, but this experience is threatening to drive me back to the dreaded Windows!

Can anyone help, please!

Gannett

---

### Post by thefoolisme on 2007-04-06
Just to verify, you did check the disk for errors before installing, right?  I've had live CDs that worked great in the live mode, but failed the disk check for installation.  Just figured I'd start with the easiest issue first.  :-)

---

### Post by wpshooter on 2007-04-06
First thing, have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, have you tried booting the CD using the safe video mode parameter ?

See if either of these help and if so, then we can get your video card properly configured.

---

### Post by Gannett on 2007-04-06
OK, no joy, I'm afraid.
I've done the following:

When I chose to check CD, it gave me the Kernel Panic error.

Did the memory test - no problems with the test.

Downloaded alternate CD
Started installation in Text Mode - gave Kernel Panic error
Just for a laugh, I tried the OEM install and Console install, both gave me Kernel Panics.

Not doing too well, am I?  

This migrating to Linux is proving a bit of a headache!  I don't mind command lines, if they actually appear! :)

Thanks in advance for your help!

---

### Post by mikewhatever on 2007-04-06
I think you tend to get discouraged too quickly. There are cases when Ubuntu wouldn't work, so, you can spend a life time in figuring out what's wrong, or try another distro that might work. Check [http://distrowatch.com/](http://distrowatch.com/)
MEPIS for example is another debian distro similar to Ubuntu. Another thought is, Ubuntu 7.04 is comming out in e few weeks.

---

### Post by Maestro23 on 2007-04-06
> **mikewhatever said:**
> I think you tend to get discouraged too quickly. There are cases when Ubuntu wouldn't work, so, you can spend a life time in figuring out what's wrong, or try another distro that might work. Check [http://distrowatch.com/](http://distrowatch.com/)
MEPIS for example is another debian distro similar to Ubuntu. Another thought is, Ubuntu 7.04 is comming out in e few weeks.

I just recently installed Linux Mint on one of my systems.  It is just like Ubuntu, could be it's little brother, they are so similar.:)   Nice, lightweight, and installed with no probs.  Check it here: [http://linuxmint.com/](http://linuxmint.com/)

*Distrowatch.com is a great site

Good luck to the OP.

---

### Post by Gannett on 2007-04-06
Hello again.
Tried Linux Mint, same result.  Here is a screenshot.

[IMG]http://www.pbase.com/gannett/image/76739347/original.jpg[/IMG]

I'm going to give open Suse a go, but I'm really disappinted Ubuntu isn't working for me.

John

---

### Post by wpshooter on 2007-04-06
John:

What speed are you burning your Ubuntu CD at.  It really needs to be at 4X or less !!!

---

### Post by Gannett on 2007-04-06
I was burning at 48x.  The slowest I seem to be able to burn is 8x.  Giving it a try now.

---

### Post by thefoolisme on 2007-04-06
The slowest I could burn was 12x, and my disks worked for me.  But any faster, and you're not going to get anything to install.  After the burn, you have to check the disk before install, it'll save you time ultimately.  On the install menu, it's like the 3rd thing down the list.

---

### Post by Gannett on 2007-04-06
Thanks.  I'm going to let the SUSE finish downloading, so I'll have another option.  I'm not very hopeful of the Ubuntu - the original disc worked perfectly in my brother's computer.  But I'm determined to make it work!
Thanks for your help!

---

### Post by Maestro23 on 2007-04-06
> **Gannett said:**
> Thanks.  I'm going to let the SUSE finish downloading, so I'll have another option.  I'm not very hopeful of the Ubuntu - the original disc worked perfectly in my brother's computer.  But I'm determined to make it work!
Thanks for your help!

Don't give up....Never surrender.:guitar:

---

### Post by tgm4883 on 2007-04-06
> **Gannett said:**
> Thanks.  I'm going to let the SUSE finish downloading, so I'll have another option.  I'm not very hopeful of the Ubuntu - the original disc worked perfectly in my brother's computer.  But I'm determined to make it work!
Thanks for your help!

Did you burn it on his computer or yours?  I have seen CD's that only work on the burner they were burned on (due to being burned really fast)

---

### Post by Gannett on 2007-04-07
Hello
Well, I've got it sorted, but it was a real hassle!
Got a friend in to sort it, a real Linux evangelist.  
In the end, we had to replace my entire motherboard, as well as the graphics card, to get Linux to work.  Also, perhaps I shouldn't say this on the Ubuntu forum, but I now have Debian.  Suits me just fine, though.
Thanks for your help!

---

### Post by tgm4883 on 2007-04-07
> **Gannett said:**
> Hello
Well, I've got it sorted, but it was a real hassle!
Got a friend in to sort it, a real Linux evangelist.  
In the end, we had to replace my entire motherboard, as well as the graphics card, to get Linux to work.  Also, perhaps I shouldn't say this on the Ubuntu forum, but I now have Debian.  Suits me just fine, though.
Thanks for your help!

You can say that here.  We are a debian based distro.  We like debian.  There are some people like me that think ubuntu is an african word for "can't install debian" :)

---

