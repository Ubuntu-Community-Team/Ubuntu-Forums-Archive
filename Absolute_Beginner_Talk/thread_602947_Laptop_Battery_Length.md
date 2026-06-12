---
title: "Laptop Battery Length"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-04
is there a setting in gnome that allows you to go in to a power saving mode for laptops?

---

### Post by Perpetual on 2007-11-06
```
sudo gedit /etc/default/acpi-support
```

Set ENABLE_LAPTOP_MODE from false to true.  There is a comment in the file (you will see it) that some users may have adverse effects when enabling laptop mode.  I personally have not had any issues on my Dell D600 laptop and it definitely extends battery life.

---

### Post by DutyDuty on 2007-11-06
Hey thanks. That really extended my life. Hope it helps the OP.

---

### Post by Perpetual on 2007-11-06
No problem.  Something I stumbled upon while roaming our lovely forums here.

---

### Post by dashnak on 2007-11-06
You should probably check this out:
[http://ubuntuforums.org/showthread.php?t=591503&highlight=killer+bug](http://ubuntuforums.org/showthread.php?t=591503&highlight=killer+bug)

---

### Post by Perpetual on 2007-11-06
Thanks dashnak.  I have read that before and have read as many posts saying it's not an issue.  I dunno, haven't noticed any problems but we'll see I guess...

---

### Post by SomeGuyDude on 2007-11-06
I have a 12 cell battery on mine, and my battery life is the exact same as it did under Windows without having to go into that razz and enable any laptop mode. On a full charge, I get about five and a half hours.

---

### Post by jordank on 2007-11-08
i changed the laptop mode to true, yet i get no more battery time whatsoever. anything i can do? any other settings?

---

### Post by jordank on 2007-11-14
even after a complete reformat and changing laptop mode to true once again, i still get no improved battery life. any other suggestions?

---

### Post by jordank on 2007-11-15
Alright, let me try a different question.  
How long do people usually get on their laptops running ubuntu 7.10? I heard someone get 5 hours out of his laptop, which is extremely high in comparison to what i'm getting. What are other people getting?

---

### Post by jordank on 2007-11-15
bump

---

### Post by Perpetual on 2007-11-16
> **jordank said:**
> bump

I am getting roughly 110 to 120 minutes on a Dell d600 laptop.  Now, I did not buy this new, it was a refurbished unit purchased from Dell so I have no idea how old the battery is.  I found a review online that said the battery got about 4 hours.  So, mine is obviously old.  I have xp on this also and I get about the same battery life as I do with Ubuntu.

Also, I did a reinstall of 7.10 after trying out a couple other distros and this time I have not enabled laptop mode.  One reason was it seemed that the Menus were slower bringing up the icons when laptop mode is enabled.  I assume this is due to the disc spinning down when idle?  Honestly, I can't say that I am seeing much difference either....

---

### Post by jordank on 2007-11-16
I'm on a brand new computer, and only get about roughly 2 hrs from my battery.  You would think it would contend with the 4 hours people claim to be getting if it's a brand new comp.  Are there no other solutions to enhancing battery life?

---

### Post by silent1643 on 2007-11-16
might help you save some power by detecting the power hog programs
[http://www.littleubuntu.com/blog/?p=99](http://www.littleubuntu.com/blog/?p=99)

also
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

---

### Post by Sims2789 on 2007-11-16
> **Perpetual said:**
> ```
sudo gedit /etc/default/acpi-support
```

Set ENABLE_LAPTOP_MODE from false to true.  There is a comment in the file (you will see it) that some users may have adverse effects when enabling laptop mode.  I personally have not had any issues on my Dell D600 laptop and it definitely extends battery life.

Couldn't this ruin your hard drive, though?

---

### Post by Depressed Man on 2007-11-16
How? 

Anyway I get 1:45 - 2 hours on my 9 cell battery..shopping for a 12 cell (ironically Sony's laptop batteries are rated worse then the 3rd party ones)

---

### Post by Perpetual on 2007-11-16
> **Sims2789 said:**
> Couldn't this ruin your hard drive, though?

I have seen threads here about that and elsewhere and from what I could gather, it's debatable whether or not the spin downs do anything.  Personally, I don't know but laptops have been around for years and I've never seen anyone having this issue.

---

### Post by Sims2789 on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/104535](https://bugs.launchpad.net/ubuntu/+bug/104535) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Depressed Man said:**
> How? 

Anyway I get 1:45 - 2 hours on my 9 cell battery..shopping for a 12 cell (ironically Sony's laptop batteries are rated worse then the 3rd party ones)

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

[https://bugs.launchpad.net/ubuntu/+bug/104535]("https://bugs.launchpad.net/ubuntu/+bug/104535")

---

### Post by silent1643 on 2007-11-16
like i posted before you might want to read this
**[Ubuntu is NOT causing aggressive power management]("http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/")**

---

### Post by compmodder26 on 2007-11-16
Usually the two biggest power hogs (at least on my T60) are the display and my wireless card.    When I switch to battery, I dim the display and lower the power level on my wireless card (read up on iwpriv).  You can set up scripts in /etc/ac.d and /etc/battery.d that will adjust the power.

Disclaimer: I have an Intel 3945 wireless card.  I think that not all wireless cards support this.  But if you have the same card or one that supports it, you can take advantage of this.

---

### Post by rundee_f on 2007-11-19
> **jordank said:**
> Alright, let me try a different question.  
How long do people usually get on their laptops running ubuntu 7.10? I heard someone get 5 hours out of his laptop, which is extremely high in comparison to what i'm getting. What are other people getting?

okay to be honest, when i used Feisty my battery can last for about 2 hours after full charge, but when i use Gutsy it can only last for approx 45 mins!

i do some suggestion on this forum such as installing **powertop** and **laptop-mode-tools**.. last night i calibrated my battery and it increased my battery life for about 13%...

maybe another way??

---

### Post by jordank on 2007-11-19
what exactly is powertop // laptop-mode-tools?

---

### Post by rundee_f on 2007-11-19
try to follow this link

[http://ubuntuforums.org/showthread.php?t=600810&highlight=battery](http://ubuntuforums.org/showthread.php?t=600810&highlight=battery)

---

