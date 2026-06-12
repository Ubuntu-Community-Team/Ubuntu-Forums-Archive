---
title: "Ubuntu is booting very slowly/I had a solution but...."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-09-02
Hi,
I just did a reinstall of Ubuntu and it boots ok until the orange bar gets about halfway, and then it gets stuck there for at least 45 seconds to a minute. 

I actually had found an answer earlier on this forum and it worked on my last install, but this time on this install it works at the cost of Network manager disappearing and my wireless networks disappearing. 

The solution (I'm doing this from memory, so it may not be exact)  was to go into the /etc/network/interfaces file and comment out everything except any lines with 'l0' on them. (that's a small 'L' + 0 ....I think).

It works to speed up my boot but then I only have 'manual configuration' available where Network Manager used to be. 

Is there anything I can do to speed up my booting?

I appreciate any help on this situation....

Many Thanks, Frank B.

---

### Post by GSF1200S on 2007-09-02
> **Brightbelt said:**
> Hi,
I just did a reinstall of Ubuntu and it boots ok until the orange bar gets about halfway, and then it gets stuck there for at least 45 seconds to a minute. 

I actually had found an answer earlier on this forum and it worked on my last install, but this time on this install it works at the cost of Network manager disappearing and my wireless networks disappearing. 

The solution (I'm doing this from memory, so it may not be exact)  was to go into the /etc/network/interfaces file and comment out everything except any lines with 'l0' on them. (that's a small 'L' + 0 ....I think).

It works to speed up my boot but then I only have 'manual configuration' available where Network Manager used to be. 

Is there anything I can do to speed up my booting?

I appreciate any help on this situation....

Many Thanks, Frank B.

Well, first off, I would boot in recovery mode to ensure its actually the network interface causing the problem (it sounds like you pretty much know it is).

I really dont mess around with the network manager at all. On my lappie, just because im a speed freak, I dont even run the network manager. Whenever im on the run and I need an internet link, I type:

iwlist scanning

and take a look at the networks available. Lets say the network I wanted was called "default." I just type:

sudo iwconfig ath0 essid default

and im connected to that network (ath0 is my wireless device, may be wifi0 or something). 

Im sorry I cant be of any more help- I really dont need a network manager that much because my computer stays home most of the time. You could use the commands above until someone comes along with a solution for your network manager.

Also, you said that you didnt exactly know the solution... maybe you commented out one line to many and thats why its not working right. Just a thought...

Good Luck :)

---

### Post by Brightbelt on 2007-09-02
Many Thanks for helping. I did narrow down things a bit on the /etc/network/interfaces file. 

I got it to where I was commenting out only the last line and it still fixed the boot problem but also it still kept my Network Manager from showing up.

Once I removed every '#' from the file, Network Manager showed up again like a champ, but of course my boot time returned to being very slow again.

I'm open to any straightforward ideas or anything not too terribly complex to implement. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2007-09-02
Bump....

---

### Post by sailor2001 on 2007-09-02
is your timing set too high in: gksudo gedit /boot/grub/menu.lst  ?

---

### Post by Brightbelt on 2007-09-04
I imagine you mean the countdown to booting the first OS on the menu? I'll check it out.

Many Thanks for the idea there,....Frank B.

---

### Post by Brightbelt on 2007-09-04
Actually since I posted this, I had to reinstall Ubuntu and Ubuntu seems to have solved this by itself.

Now Ubuntu is the only OS on my menu, and it goes through fairly quickly now. 

Many Thanks for your ideas,....Frank B.

---

