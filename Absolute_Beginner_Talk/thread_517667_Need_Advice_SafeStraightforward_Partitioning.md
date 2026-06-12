---
title: "Need Advice: Safe/Straightforward Partitioning"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by e123 on 2007-08-04
Hi All,

I am about to begin the recovery process. Thank you all again for pointing out the things I need to do to access my data.

Is there a 'best practice' for partitioning out my home directory? I have a 40gb hard drive and Ubuntu is the only OS I run.

Any advice is much appreciated. My goal is to be able to install/reinstall an OS without worry too much about my data.

Thanks!
Matt

---

### Post by VChief on 2007-08-04
40 GB is more than enough. That's what I have. Currently, I have it portioned as 20G for / and 19 for /home. I'm currently using 7.3G on my /. But that's because I've installed a lot of programs (some are stuff I use all the time, like programming and electronic stuff, and some because I'm still trying to find what programs I like...taken me a few years). I think a fresh install is only about 2 or 3G.  I know 7.3 is the highest I've ever taken up in /. Depending on what you want to do, you should be able to easily give your / partition about 10G and 30G to /home. Having /home on a separate partition is a really smart idea.

EDIT: If you rip music on your computer or download a lot of music or large files, give your /home as much as you can if you don't have another medium to put them on. Currently, I have a 160GB external that all my music is on, so 19GB is more than enough for my /home.

---

### Post by louieb on 2007-08-05
After about a year of playing with Linux this is what works well for me. [LIST]
[*]Root partition  7GB I have my main stable distro installed here in the case of this machine I run Dapper.
[*]Home partition  2GB  Only keep my user configuration file here. Could be smaller if i got my email on the data partition.
[*]Test distro partition 7GB  Currently have Feisty. Feisty soon to be replace by Gutsy. Linux distros are fast moving don't like doing Upgrades to the newest release Perfer to do a fresh install Having this partition allows me to install the latest release without  fear of messing up my main distro.
[*]Swap .5GB Kinda small but PC only has 384MB ram
[*]Data partition Rest of hard drive. This keep my data separated from the operating system.[/LIST]

---

### Post by Austin_KW on 2007-08-05
root "/" partition; 5-10 GB depending on how man apps you want to install. I have ubuntu + kde desktop + xubuntu desktop and a mix of applications in 5gb

swap; 1GB

/home ; the remainder, having a seperate /home partition will allow you to upgrade, reinstall or change distros without losing all your data.

---

