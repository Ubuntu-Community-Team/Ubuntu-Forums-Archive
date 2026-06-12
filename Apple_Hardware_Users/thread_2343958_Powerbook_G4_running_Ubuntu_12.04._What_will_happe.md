---
title: "Powerbook G4 running Ubuntu 12.04. What will happen?"
date: 2016-11-21
forum: Apple Hardware Users
---

### Post by smnbldwn on 2016-11-21
I recently installed Ubuntu 12.04 on my 1.67Ghz Powerbook. It runs really well but the update manager keeps recommending I upgrade to 14.04.5. I know that this version is not available for ppc architecture with the Unity desktop and when I tried to install Lubuntu or Mate ppc 16.04 the computer froze after a couple of minutes. What will happen if I accept the update? I know support runs out for 12.04 next year and I want to know if it will just go to Lubuntu or remove the desktop entirely or even break the installation. Does anyone know what will happen?

---

### Post by rican-linux on 2016-11-21
I have a PowerBook G4 and it is running Lubuntu 16.10 right now. I would recommend 16.04. It runs well.

---

### Post by smnbldwn on 2016-11-22
Did you have the issue with the live DVD freezing?

---

### Post by paul9731 on 2016-11-22
G4 MDD Dual 1Ghz Radeon 9000 AGP4x

When I tried the software update from Ubuntu 12.04 which was mostly functionable, just found myself stuck with Firefox 36 with no upgrade path other than a distro upgrade, I tried to upgrade to Ubuntu 14.04ppc via software update, which when it wnt through the motions of a full update, when it came to reboot into the new system, it just booted to a black screen no matter what I tried to add in the yaboot prompt second stage screen.  I tried twice through the whole procedure. Same result.

That's when I tried Lubuntu 14.04 which's iso boots fine, to install finely, however the video=radeonfb:1024x768-32 worked but the windows were elasticated slow like a bung jump in slow motion.  Shells, Terminal, Firefox. worked but sound was the issue which never came right.

You may be luckier than me with your laptop. 

I gave up with Ubuntu over and including 14.04 and above and use Debian Wheezy because Debian Jessie 8.xx all behave the same even after Alternative Installs and freeze shortly after login when an app is launched. It's like a race to open an app to see if it won't freeze but always did.  It's like 16.04, 16.10. 17 mate lubuntu16 all freeze on my G4MDD.  Live DVDs and Alternate Installs where possible.

Debian Wheezy is extremely stable.  It is labeled as obsolete on Debian downloads but is the most compatible from my point of view.

---

### Post by smnbldwn on 2016-11-23
Thank you, I can see Wheezy is still supported until 2018 so I will have a look. Has anyone tried Mint PPC?

---

### Post by rican-linux on 2016-11-23
try with this boot parmaeter

```

live radeon.agpmode=-1

```

---

