---
title: "Canon printer setup and root access"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Soapy on 2007-07-09
> **PurplePenguin said:**
> I'd like to join the chorus of people trying to talk you out of this.  Ubuntu (and linux in general) is secure because users do not have permanent root access.  Entering your password and adding sudo before a few commands here and there isn't too much of a hassle! :)

I am in the same boat.  The system is telling me that I have to be logged in as Root.

I am trying to install a Canon LBP1210 according to the procedure on the forum (This is incredibly complex for such a basic requirement, and has almost put me off Linux) 

 I have to do the final step.
 sudo ccpdadmin

Then it tells me that I have to be logged in as Root.

---

### Post by aysiu on 2007-07-09
Canon and [CUPS](http://en.wikipedia.org/wiki/Common_Unix_Printing_System) do not mix. If that puts you off Linux, it'll probably put you off Mac as well.

As long as you have that Canon printer, you might as well stick with Windows.

If you insist in trying to get that Canon printer working with Ubuntu, instead of summarizing the output, can you copy and paste the exact output of the command ```
sudo ccpdadmin
``` and also a link to the HowTo procedure you're using?

---

### Post by Soapy on 2007-07-09
> **aysiu said:**
> Canon and [CUPS](http://en.wikipedia.org/wiki/Common_Unix_Printing_System) do not mix. If that puts you off Linux, it'll probably put you off Mac as well.

As long as you have that Canon printer, you might as well stick with Windows.

If you insist in trying to get that Canon printer working with Ubuntu, instead of summarizing the output, can you copy and paste the exact output of the command ```
sudo ccpdadmin
``` and also a link to the HowTo procedure you're using?

Thanks,

That is very frustrating to hear at this point. This is the kind of thing I was hoping to avoid by leaving MS behind.  It is a very good printer, and common, so why does Linux not accommodate it?

The response to sudo ccpdadmin is : "this command must be run as root"

The procedure is from this forum at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

### Post by aysiu on 2007-07-09
It's not really Linux not accommodating Canon. It's Canon not accommodating Linux ([or Mac, for that matter](http://ubuntucat.wordpress.com/2007/06/11/macs-are-just-computers-not-magic/)).

---

### Post by notepad on 2008-01-21
i set this printer up on ubuntu 7.10 lastnight. i have tried many times before without success but lastnight it finally worked. i made a complete list of instructions on what i did if you want to try it.

---

### Post by Golem XIV on 2008-01-21
Hey, please post the instructions!  I'm trying to connect to a Canon PIXMA iP1700 hooked into my XP desktop from my Gutsy laptop.  Maybe your experiences will help.

---

### Post by notepad on 2008-01-21
hi golem! i have posted the instruction at this thread
[http://ubuntuforums.org/showthread.php?t=447406&highlight=lbp1210](http://ubuntuforums.org/showthread.php?t=447406&highlight=lbp1210)

 i found it hard to follow the original instructions at help.ubuntu.com and i failed trying numerous times before so when i got it going i made sure to write down what i did to share it with others who seem to have the same trouble i did. please let me know if the instructions i posted help you!

---

