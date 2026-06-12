---
title: "Has 7.10 Ruined My HD?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Bezmotivnik on 2007-10-18
I've been trying all day to get an install done of 7.10.  All I have achieved is a tailspin of worsening symptoms.

I have burned two  7.10 i386 CDs from a good-MD5SUMS download.  I have tested them as good in four systems.  I have changed the CD-ROM drive in the problem box.

"Live" loads and appears to be pretty much fully functional.  When I first tried to install, I had a hang at about 60%.  After an hour, I bailed out.

Since then, 7.10 will not do the "partition format" of the HD.  The install hangs there at 5% as soon as it attempts to partition the drive.

I've tried two different tested CDs and swaped the CD-Rom.  No dice.

Is the HD cooked, or what?  It is detected during the install, it just won't partition.

Thanks for any help on this.

---

### Post by iver2435 on 2007-10-18
Have you tried loading into a Live CD session and then downloading and using Gparted to format the drive?  I very much doubt that the Ubuntu load hosed your drive, more likely it left it in an inconsistent state.  Try the format thing and see what happens.

---

### Post by irish_flu on 2007-10-18
No operating system installation is ever going to "ruin" your hard drive; it's a good rule of thumb that, except in very specific circumstances, software isn't going to ruin hardware.

Your troubleshooting methods are good (new CD-ROM drive, new CD).  I'd say there's either something up with the hard drive physically, or there's something so wonky about the partition currently on there that Ubuntu can't quite do the deed.

I'd either try to manually partition and format the drive from within the live CD (just make it one big partition if you want, you can always do it over when you install) or maybe partition and give it a good format from a DOS boot disk or something.

You could also give it a shot with the Gparted live CD (it's small, like 50MB or so).

---

### Post by Cappy on 2007-10-18
do a ```
sudo apt-get install gparted
``` on the live cd and then run ```
gparted
``` from the command line. Hopefully it will either give you an error in the command line or a pop up message somewhere letting you know what the problem is.

---

### Post by Bezmotivnik on 2007-10-19
OK, this pretty much follows my own thinking on this business (that a flaky install hopelessly garred-up the drive's partition)  -- I've just never formatted a Linux drive before and assumed that there was nothing in another partitioner/formatter that the install partitioner/formatter wouldn't do.

Will give these a try, thanks!

---

### Post by swoll1980 on 2007-10-19
it will do it just reinstall it when gets the partitioner do i manual partition

---

### Post by swoll1980 on 2007-10-19
> **Cappy said:**
> do a ```
sudo apt-get install gparted
``` on the live cd and then run ```
gparted
``` from the command line. Hopefully it will either give you an error in the command line or a pop up message somewhere letting you know what the problem is.

can you install software from the live cd?

---

### Post by Bezmotivnik on 2007-10-19
It's an installer bug.

It was choking on my having a second (slave) drive.  Even though it was in no way involved in the installation, I couldn't get the master HD to format until I disconnected the slave.  This was a perfectly working 7.04 system this morning.

I eventually got 7.10 installed, but it has a staggering amount of weirdness:  Firefox crashes, GNOME vanishes, stuff locks up, the system won't even close down reliably.

Why it should be so flaky compared to the 7.04 I installed on the same box a couple of weeks ago, I can't imagine.

Rollback time, I think. :(

---

### Post by exile on 2007-10-19
I've had this problem since one of the Tribe (5 I think) releases. It's a shame it's still there for the final.

I can confirm that my hard drive wasn't ruined due to it.. just my previous feisty install.

---

### Post by Bezmotivnik on 2007-10-19
> **exile said:**
> I've had this problem since one of the Tribe (5 I think) releases. It's a shame it's still there for the final.
I'm sorry to say that so far, 7.10 is a total abortion on this machine.  I've never seen anything to equal it.  Almost nothing works, everything crashes and 7.04 was really trouble-free in the short time I had it up on the identical machine.  I don't understand what changed! :(

---

### Post by zalo on 2007-10-19
Gutsy should be about as fast as Feisty.

The Desktop CD is often unreliable IMO. I recommend trying  the Alternate CD.

---

### Post by Soarer on 2007-10-19
I had similar problems. Gutsy was fine at first, after a clean install. Then I imported my profile (from Feisty) and, though not so bad as yours, started getting grey screens and program (mainly Firefox) crashes.

I wonder if something in a Feisty profile upsets Gutsy sometimes?

---

### Post by WorldTripping on 2007-10-19
I had a similar drive issue when trying to install Fawn.

If the external HDD was plugged in, the live CD would not load, once it was unplugged everything was OK.

---

### Post by Bezmotivnik on 2007-10-19
> **WorldTripping said:**
> I had a similar drive issue when trying to install Fawn.

If the external HDD was plugged in, the live CD would not load, once it was unplugged everything was OK.
Not being able to install in a box with two drives seems to be a bug worth fixing.  I can't see a lot of people going through the grief of busting open their boxes to disable slave drives, or having any idea that's what's crashing their installs.

---

### Post by dfreer on 2007-10-19
I actually had an eaiser time doing an upgrade from feisty -> gutsy, then using the Live CD to install. Granted, this was with the Beta and not the Final Release.

---

### Post by Frak on 2007-10-19
Try the alternate or network disc. Also, the Linux Kernel protects your hardware from being borked.

---

### Post by Bezmotivnik on 2007-10-19
> **Frak said:**
> Try the alternate or network disc. 
I'll probably just reinstall 7.06...but why do people routinely suggest the "Alternate" CD?

Its description on the downloads page give no indication of anything that should make the slightest difference. :confused:

Is there a real, meaningful page that addresses the differences in a way that most users would understand?

Thanks!

---

### Post by Perfect Storm on 2007-10-19
Becourse Alternate CD comes with text installer  (minimal things that would/can mess your system up).

---

### Post by Bezmotivnik on 2007-10-19
> **Artificial Intelligence said:**
> Becourse Alternate CD comes with text installer  (minimal things that would/can mess your system up).
REALLY!  That's all?  No kidding?  Just ANSI instead of GUI? 

Nuts, if I'd have known that, I never would have messed with release in the first place. :rolleyes:

---

### Post by Frak on 2007-10-19
> **Bezmotivnik said:**
> REALLY!  That's all?  No kidding?  Just ANSI instead of GUI? 

Nuts, if I'd have known that, I never would have messed with release in the first place. :rolleyes:
That's why we routinely suggest it. :)

---

### Post by Bezmotivnik on 2007-10-21
> **Frak said:**
> That's why we routinely suggest [Alternate]. :)

I couldn't get it to install the kernel.

It *appears* to need an active Internet connection to install. Is that correct?  If so, it won't work for me, as I only have wireless access.

---

### Post by Soarer on 2007-10-21
No, it does not need Internet access to install.

What error did you get?

---

### Post by Perfect Storm on 2007-10-21
> **Bezmotivnik said:**
> I couldn't get it to install the kernel.

It *appears* to need an active Internet connection to install. Is that correct?  If so, it won't work for me, as I only have wireless access.

Any chance you burned Ubuntu to a CD-rw?

---

### Post by Wiebelhaus on 2007-10-21
omg man , the title [HTML]Has 7.10 Ruined My HD?[/HTML] infuriates me , software cannot except in extremely rare situations mechanically damage hardware.


Download [UBCD]("http://www.ultimatebootcd.com/")

Run a debug script:

Boot to Win98SE startup disk

"debug" at command line

Enter in the following commands:



```

-F 220 L1000 0 (ENTER)

-A CS: 100 (ENTER)

xxxx:0100 MOV AX,301 (ENTER)

xxxx:0103 MOV BX,200 (ENTER)

xxxx:0106 MOV CX,1 (ENTER)

xxxx:0109 MOV DX,80 (ENTER) <---"80" for hd1, "81" for hd2 >

xxxx:010C INT 13 (ENTER)

xxxx:010E INT 20 (ENTER)

xxxx:0110 (ENTER) <-------BLANK LINE "VERY IMPORTANT" >

-G (ENTER)

Program terminated normally

- (CTRL)-(ALT)-(DEL) to reboot system
```

Then at the command type:

"fdisk"

follow all defaults.

Sounds like you killed your partitions some how and you now need to rebuild on e then install your OS.

---

### Post by snl2587 on 2007-10-21
> **swoll1980 said:**
> can you install software from the live cd?
Yes, you can download and use software while using the LiveCD, but it will not be available upon reloading the LiveCD (unless you copy it to the HD, but that's a different case).

---

### Post by Bezmotivnik on 2007-10-22
> **Artificial Intelligence said:**
> Any chance you burned Ubuntu to a CD-rw?
No.

---

### Post by dwhitney67 on 2007-10-22
> **Bezmotivnik said:**
> It's an installer bug.

It was choking on my having a second (slave) drive.  Even though it was in no way involved in the installation, I couldn't get the master HD to format until I disconnected the slave.  This was a perfectly working 7.04 system this morning.

I eventually got 7.10 installed, but it has a staggering amount of weirdness:  Firefox crashes, GNOME vanishes, stuff locks up, the system won't even close down reliably.

Why it should be so flaky compared to the 7.04 I installed on the same box a couple of weeks ago, I can't imagine.

Rollback time, I think. :(

:popcorn:  It's probably because the release was hurried before being properly tested.  And thanks to your efforts, it was tested a wee bit more today.  Rule of thumb is to never get an OS that just been released.  Wait for it to be patched.

---

### Post by Bezmotivnik on 2007-10-22
> **Soarer said:**
> No, it does not need Internet access to install.

What error did you get?
That it couldn't find the kernel to install.

Screw it, 7.10 is stone hopeless on this box -- or at least far, far, far more trouble than it could ever conceivably be worth. 

7.04 went in like it was on greased rails and was rock solid.  7.10 is a total trainwreck in just about every way I can think of.  7.04 will go back on the machine.

I may try 7.10 on a different machine, or not. [shrug]

---

### Post by Soarer on 2007-10-22
> **Bezmotivnik said:**
> That it couldn't find the kernel to install.


Sounds like a unique error.

Could you give the exact error, and when it happened?

Thanks.

---

