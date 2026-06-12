---
title: "After Windows Update, I can't boot windows"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Avinash4 on 2007-11-07
I am dual booting windows xp and ubuntu 7.10. I just installed the latest windows update patches from MS, and when I restarted, I can no longer boot xp. It appears in the GRUB list, but when I select it, the screen just turns black, and no HD activity is there. Any ideas?

---

### Post by oilchangeguy on 2007-11-07
> **Avinash4 said:**
> I am dual booting windows xp and ubuntu 7.10. I just installed the latest windows update patches from MS, and when I restarted, I can no longer boot xp. It appears in the GRUB list, but when I select it, the screen just turns black, and no HD activity is there. Any ideas?

you had to do something else. because if an update did cause a problem, you'd be getting the blue screen of death.

---

### Post by Avinash4 on 2007-11-07
That is strange, I can boot ubuntu fine, but I cant even get to the options to get xp into safe mode.

---

### Post by oilchangeguy on 2007-11-07
> **Avinash4 said:**
> That is strange, I can boot ubuntu fine, but I cant even get to the options to get xp into safe mode.

like i said you had to do something else besides just run an update. and when you select windows from the boot list, you can't press F8 to get into safe mode?

---

### Post by DutyDuty on 2007-11-07
Is this really a problem for the Ubuntu forums?

What you do is do a clean install of XP. Or take it to a shop for support.

---

### Post by oilchangeguy on 2007-11-07
> **DutyDuty said:**
> Is this really a problem for the Ubuntu forums?

What you do is do a clean install of XP. Or take it to a shop for support.

be nice. the user can also try [http://support.microsoft.com](http://support.microsoft.com)
but most likely the problem is operator error. not operating system error. how many threads are there where somebody did something to ubuntu, they should'nt have. and wanted to blame it for their screw up?

---

### Post by jaybombalous on 2007-11-07
definitely a windows problem, but you might try **supergrub** cd image and boot to that and rewrite grub to the master boot partition. That may or may not get you back in to windows. If it doesn't then u may wanna go ask microsoft for some help.

the only operator error here is messing up the MBR, u can easily repair that. U could also see if the problem is grub or windows related by using** gparted** and booting to the partition that u know is loaded with windows and see if it boots. **Gparted** can boot partitions like grub boots partitions.

---

### Post by oilchangeguy on 2007-11-07
> **jaybombalous said:**
> definitely a windows problem, but you might try **supergrub** cd image and boot to that and rewrite grub to the master boot partition. That may or may not get you back in to windows. If it doesn't then u may wanna go ask microsoft for some help.

the only operator error here is messing up the MBR, u can easily repair that. U could also see if the problem is grub or windows related by using** gparted** and booting to the partition that u know is loaded with windows and see if it boots. **Gparted** can boot partitions like grub boots partitions.

how about spelling the word you. u is not a word. and not everybody in here uses english as their first language. so they might not be able to clearly understand your posts.

---

### Post by jaybombalous on 2007-11-07
No, I should not have to type a specific way to help someone else out. If they want help then they should be able to find a way where they can understand the help they receive.

Gparted is the program u need, then u just boot the windows partition using gparted and see if it works, only then can u formulate a plan.  

A: If the windows partition doesn't boot then u should go ask microsoft for help, but be warned microsoft is not gonna let u do a dual boot with ubuntu.

B: if it does boot, u could then try and repair the MBR with Supergrub.

Be warned Microsoft has its own boot loader program and they will insist u use this boot loader instead of grub if u call for help. There is no doubt in my mind about that point, thats why I threw my microsoft cd in the trash. Its worthless to me these days.

---

### Post by Fearghal on 2007-11-07
I have the same problem as Avinash4, everything was well with my XP partition.  Last night I had a job to do that required my XP partition. When I booted into XP, the splash screen came up then BSD.  I tried F8 and went to safe mode, same again.
Now I am not complaining, I can open the partition via Ubuntu and recover all my files, but what I want is to delete the XP partition and resize Ubuntu to use all 100GB.  What I do not want to do is reformat the whole drive just to claw back my 50gb windoz space.
Whats the safest way?????

---

### Post by FXEF on 2007-11-07
> **Fearghal said:**
> I have the same problem as Avinash4, everything was well with my XP partition.  Last night I had a job to do that required my XP partition. When I booted into XP, the splash screen came up then BSD.  I tried F8 and went to safe mode, same again.
Now I am not complaining, I can open the partition via Ubuntu and recover all my files, but what I want is to delete the XP partition and resize Ubuntu to use all 100GB.  What I do not want to do is reformat the whole drive just to claw back my 50gb windoz space.
Whats the safest way?????

The GParted-LiveCD should do the job.
[URL="http://gparted-livecd.tuxfamily.org/"]
http://gparted-livecd.tuxfamily.org/[/URL]

---

