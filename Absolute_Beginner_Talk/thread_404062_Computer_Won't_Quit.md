---
title: "Computer Won't Quit"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-04-07
Hi, I have discovered an odd behavior. Suddenly, my computer won't complete its log off procedure. It goes all the way to the end, to "will now halt", the computer clicks...and it stays there. I've had to force a power off to complete the log off procedure. Do I need to reinstall Ubuntu? Will I lose my files if I do so? Any suggestions?

Thanks in advance.

---

### Post by LaurelLynn on 2007-04-07
Dear wmichaelb,

Sounds like a program is refusing to shutdown.

The ¨shutdown¨ command has options like ¨-n¨ which will kill everything running.

The ¨kill¨ command also has options to stop programs without waiting for a reply.

The real question though, is what is still running? 

The System Monitor :   System->Administration->System Monitor   gives you more information about what programs are running, and what they are doing.

It is probably something you installed recently, so uninstalling the last thing you added might solve the problem.

Laurel Lynn

---

### Post by mac.ryan on 2007-04-07
> **wmichaelb said:**
> I've had to force a power off to complete the log off procedure.

Do you mean you can effectively halt the system issuing:

```
sudo poweroff --force
```or do you mean that you had to press your computer power button?

Anyhow, if you haven't tried yet, you might try the command above and see if it work. Forcing the poweroff that way skips some of the scripts for shutting down (but it is not the best thing for the software health of the system). If it works, then my guess (I am far from being an expert) would be that the problem has to do with some program refusing to shut down as it should and blocking the halt script. In that case it would be probably sufficient to purge the culprit program and things should get back to normality.

Anyhow: I am not an expert in bootscripts, so some other linux-guru might come up with a more exact analysis and a better suggestion... best luck! :)

EDIT: ...I've been too slow to type... somebody already answered! ;)

---

### Post by confused57 on 2007-04-07
This method works for Edgy, I don't know about Dapper:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by wmichaelb on 2007-04-09
Laurel Lynn, thanks for your reply. The only process that System Monitor notes as running is - you guessed it - gnome-system-monitor. Is there somewhere else I should look?

Thanks! 

- Michael B. in Cincinnati
> **LaurelLynn said:**
> Dear wmichaelb,

Sounds like a program is refusing to shutdown.

The ¨shutdown¨ command has options like ¨-n¨ which will kill everything running.

The ¨kill¨ command also has options to stop programs without waiting for a reply.

The real question though, is what is still running? 

The System Monitor :   System->Administration->System Monitor   gives you more information about what programs are running, and what they are doing.

It is probably something you installed recently, so uninstalling the last thing you added might solve the problem.

Laurel Lynn

---

### Post by wmichaelb on 2007-04-09
mac.ryan: to be more specific, I attempted to turn off the computer using the appropriate icon on the icon bar. When the shutdown procedure got to the last line ("system will now halt"), the computer clicked, the 3 LED's over the number pad flickered, and the computer stayed in that state. I forced it off with the power switch. 

When I attempted your suggestion above in terminal, I got the following message:

usage: poweroff [-n] [-w] [-d] [-f] [-h] [-i]
        -n: don't sync before halting the system
        -w: only write a wtmp reboot record and exit.
        -d: don't write a wtmp record.
        -f: force halt/reboot, don't call shutdown.
        -h: put harddisks in standby mode.
        -i: shut down all network interfaces.

Also, please see my other note below. Any new suggestions are welcome, and thank you for your reply.

---

### Post by wmichaelb on 2007-04-09
Confused 57: I executed the suggestion noted, but the behavior did not change. New suggestion?

Thanks for your reply!

---

### Post by Swab on 2007-04-09
Have you recently changed your BIOS settings?  There is sometimes something in there about soft power of similar, try changing that.

---

### Post by mac.ryan on 2007-04-10
> **wmichaelb said:**
> When I attempted your suggestion above in terminal, I got the following message:

Yes, sorry... I poorly formatted the command in my previous post (now fixed). Just try:

```
sudo poweroff --force
```If this command will effectively shut down the system, then the the it's just a matter of "killing" a non-responsive program, while if it doesn't that it must be something wrong with the interactions between ubuntu and your bios....

Anyhow, from your answer to other poster, I understand you neither manage to leave the GUI, as you can still access your menus. From the outcome of your test, I would conclude the problem is not with a program you are running _within_ your GUI, but with something running _behind_ your GUI (possibly even on a lower runlevel).

Final question: does logging off from your user and selecting the shut down option from the login graphical menu works for you?

---

### Post by wmichaelb on 2007-04-11
mac: first, I appreciate your time and attention to my problem.

Second: when I cut and paste the command above into terminal, I get the same error that I did before:

usage: poweroff [-n] [-w] [-d] [-f] [-h] [-i]
-n: don't sync before halting the system
-w: only write a wtmp reboot record and exit.
-d: don't write a wtmp record.
-f: force halt/reboot, don't call shutdown.
-h: put harddisks in standby mode.
-i: shut down all network interfaces.
 
Do I need to add a flag of some sort?

Third, logging off from my user logon and selecting shutdown from the login graphical menu generates exactly the same results as before. I still get down to "system will now halt" - but it will not go that last bit and shut off. My sense of this problem is that it is hardware or BIOS; but I don't know where to go from here. Is there somewhere I can look to see the shut down sequence?

Thanks in advance!

---

### Post by wmichaelb on 2007-04-11
Ooooh...looky what I found!

[http://forum.notebookreview.com/showthread.php?t=115355](http://forum.notebookreview.com/showthread.php?t=115355)

I don't have a notebook; this machine is a homemade model with an ASUS A7N266 mobo, a 1.4 GHZ Athlon, and 1 GB of RAM. But the issue described in the link above is exactly what I'm seeing. I have to run off to teach now, but when I get some time, I'll try the upgrade to Edgy and see if that helps.

Thanks!

I chose 6.06 LTS for stability; but this may be a case where newer is stabler.

---

### Post by dstew on 2007-04-11
I had the same problem on my HP Xe3. After I installed Edgy, it would halt the system, but not turn off. The following edit fixed it.

Open a terminal window. Do **sudo gedit /etc/modules** and add the line **apm power_off=1**. Save the file, reboot and try to shutdown again. It should work. At least it did for me with Edgy.

---

### Post by wmichaelb on 2007-04-11
dstew: thanks, I did try that with my Dapper installation. I reopened /etc/modules, and noted that the change had indeed been accepted. But the edit did not change the behavior.

One of the editors of LINUX World mentioned having a similar problem with an ASUS motherboard; I may have the same issue as he. If I learn something, I'll post it.

---

### Post by mac.ryan on 2007-04-11
> **wmichaelb said:**
> Second: when I cut and paste the command above into terminal, I get the same error that I did before [...] Do I need to add a flag of some sort?

The key point here is to use the "force" flag (as this will skip most of the normal operations and will basically "pull the plug" of your system, thus allowing you to understand if the problem is in "pulling the plug / bios" or "doing the normal operations / shutdown scripts").

From the output of your version of poweroff (which must be clearly different than mine, as the command works on my system the way I posted originally), I would guess you might achieve the same behaviour with:

```
sudo poweroff -f
```

> My sense of this problem is that it is hardware or BIOS; but I don't know where to go from here. Is there somewhere I can look to see the shut down sequence?


If you are right, then the forced poweroff won't work (this is the reason of this "test" indeed!). To be more exact: if the forced poweroff will work, you can exclude a bios problem on the poweroff.

If it is a bios problem (i.e. a problem in making your bios and linux kernel to cooperate) you might still try to boot the system with various options such "-noacpi" or even "irqpoll".

If it is a shutdown sequence, than you might try to alter the booting scripts, which are into /etc/rc0.d. For a complete explanation of booting scripts, I recommend [this page]("http://www.linuxfromscratch.org/lfs/view/6.2/chapter07/usage.html") from LFS.

---

### Post by ArtMan on 2007-04-14
Could this be a kernel issue?

I've been noticing the same issue for a week or so now. 

Please don't flame me: I'm a noobie who has to be in WindowsXP for most of the time due to some specialized software.

Like I said, I'm a noob; I don't even know how to get the processes scrolled on my screen during shutoff; I just get a graphic with a progress bar that almost goes to the end, then stops. I then have to power down my machine manually.

The machine is a 2-year-old HP with good specs, and the auto-shutdown worked fine before.

The problem may have started coincident with new kernel that I somehow upgraded to, which is 2.6.15-26-386. Could the problem be at that level? And, again, is there a workaround?

-ArtMan-

---

### Post by mac.ryan on 2007-04-15
> **ArtMan said:**
> Could this be a kernel issue?

I don't know, however yesterday I was compiling the kernel (v.2.6.16.27), and in the configuration options I noticed an an entry called "*Enable x86 board specific fixups for reboot*". Here below the explanation for the help feature.

```
This enables chipset and/or board specific fixups to be done
in order to get reboot to work correctly. This is only needed on
some combinations of hardware and BIOS. The symptom, for which
this config is intended, is when reboot ends with a stalled/hung
system.

Currently, the only fixup is for the Geode GX1/CS5530A/TROM2.1.
combination.

Say Y if you want to enable the fixup. Currently, it's safe to
enable this option even if you don't need it.

```

I am totally unaware if this can be put in relation with your problem and if ubuntu kernel image has this feature enabled or not, yet I found this interesting...

---

### Post by wmichaelb on 2007-04-16
Actually, the reboot process seems to work fine. It's only the shutdown that hangs. In addition, if I hold down the power switch after I get to the "System will not halt" line, it not only shuts off, but boots up fine the next time I turn it on. So ??????. Does Edgy have this problem?:confused:

---

### Post by mac.ryan on 2007-04-18
Have a look to [this other thread]("http://ubuntuforums.org/showthread.php?t=410732"). When I pointed the OP here he told me that it was the same problem, and 20 minutes ago he found a solution, maybe it will work for you too?

---

### Post by Kuoi on 2007-04-30
Maybe the following could help too ?

[Poweroff solution ?]("http://ubuntuforums.org/showthread.php?t=428363")

Greetings , Kuoi

---

### Post by wmichaelb on 2007-04-30
??????!?!?!?!?!?!!!!!?!?!? Just as suddenly as this behavior appeared, it has disappeared; the computer now shuts down correctly from the icon. Go fig. 

I have installed some additional applications since the last time. Phase of the moon? Wolfbane pollen concentration? Infection by a Windows file? 

To those who expressed concern, I assure you that no red chickens have died as a result of this investigation.

---

### Post by rillip on 2007-04-30
Whenever I see a flukey reaction like this, I point to hardware.  This is partially my prejudice, being a program developer rather than a hardware guru.  However, even bugged programs almost always have the same behvior.  Getting a non-deterministic issue like this is difficult with software on accident.

The fact that when you hold the power button, it then boots back up, indicates bios or hadware to me as well.  The effect of the powerbutton is run by the bios.  One of the above posts mentioned this as well, but typically there's an option stating what a hard poweroff should do, restart, shutdown, etc.  

Glad it worked itself out htough.  I blame sunspots!

---

### Post by wmichaelb on 2007-05-09
For all: the problem has come and gone a couple of times since, in each case after I've added software. I'm beginning to suspect:
  
- the behavior only occurs when I have an odd (or even) number of applications packages installed;
- there is a BIOS issue, in which case the problem will return without any additional software adds
- phase of the moon
- wolfbane pollen concentration
- something else unknown to thsi august group.

In any case, I'm happy at the moment. Thanks to all; you put in a lot of time on this issue!

---

