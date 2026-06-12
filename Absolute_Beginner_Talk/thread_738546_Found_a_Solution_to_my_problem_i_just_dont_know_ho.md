---
title: "Found a Solution to my problem i just dont know how to actually fix it."
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by jcgoodni on 2008-03-28
I just switched over to ubuntu and I have a sound problem on my Toshiba Satlelite notebook.  I found a solution that worked for everyone with the same notebook but since im so new with the opporating system i have no idea how to fix my problem.  

here is what it says to do..........

> Solved(?) this problem on another Toshiba Staellite A100-SK4 (PSAA8C-SK400E)
> by following most of the directions here:
>
> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
>
> However, contrary to that document, this is the entry that I appended to
> /etc/modprobe.d/alsa-base to get the sound to work properly:
>
> options snd-hda-intel model=auto
>
> The sound now seems to be working. At least it has over the past
> two reboots.

It works on Toshiba Satellite A105-S4074. There is no even need to
perform steps described in howto. This option (options snd-hda-intel
model=auto) works really fine.



So this is the portion that i need some assistance on .....

> However, contrary to that document, this is the entry that I appended to
/etc/modprobe.d/alsa-base 
to get the sound to work properly:
options snd-hda-intel model=auto

How do i do tha?:confused:

---

### Post by Inxsible on 2008-03-28
i don't know if it will work, but what the user is saying there is 

open that file and add the line and save the file. This is how you do it
in a terminal type in ```
gksudo gedit /etc/modprobe.d/alsa-base
```Then add the following line at the end of the file and save and close the file```
options snd-hda-intel model=auto
```Restart and see if sound works.

Good Luck

---

### Post by jcgoodni on 2008-03-28
thank you
this worked!

the sound is great now

---

