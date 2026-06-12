---
title: "Automatically hibernate on power failure?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by apsk121 on 2008-01-05
Hi all,

I have an APC UPS and I've been using it with windows. It has a powerchute software that automatically hibernates the computer in case of a power failure. This feature is very important to me as I live where we have frequent power cuts etc.

Ubuntu seems to recognize the UPS and model number etc. It even provides options on what to do when battery power is on use. I've selected hibernate when battery power is low, but that doesn't seem to get the job done.
I switched off the power outlet to test this feature and it showed that battery is no longer recieving AC power and it showed the battery draining, but it did not hibernate the PC, the battery completely draiing out and the UPS switched itself off. :(

Any ideas on how I can get this to work?

---

### Post by dcstar on 2008-01-05
> **apsk121 said:**
> Hi all,

I have an APC UPS and I've been using it with windows. It has a powerchute software that automatically hibernates the computer in case of a power failure. This feature is very important to me as I live where we have frequent power cuts etc.

Ubuntu seems to recognize the UPS and model number etc. It even provides options on what to do when battery power is on use. I've selected hibernate when battery power is low, but that doesn't seem to get the job done.
I switched off the power outlet to test this feature and it showed that battery is no longer recieving AC power and it showed the battery draining, but it did not hibernate the PC, the battery completely draiing out and the UPS switched itself off. :(

Any ideas on how I can get this to work?

Go to the APC website and see if they have any Linux software available.

---

### Post by apsk121 on 2008-01-05
They don't.

---

### Post by OmegaBLK on 2008-01-22
^There is a version of PowerChute Business Edition for Linux.  Not sure about the quality, or if it will run in Ubuntu properly, or if it will cooperate with their low-end ups line of, but there is a binary available.  You do need to register to download it though.
[http://www.apc.com/resource/include/techspec_index.cfm?base_sku=SFPCBE705&tab=Software](http://www.apc.com/resource/include/techspec_index.cfm?base_sku=SFPCBE705&tab=Software)

---

### Post by Cato2 on 2008-02-09
To get the APC UPS working with Ubuntu, see my mini HOWTO at [http://ubuntuforums.org/showpost.php?p=4282701&postcount=35](http://ubuntuforums.org/showpost.php?p=4282701&postcount=35) - it's pretty easy to configure once you have the instructions, and it's supported by the excellent apcupsd software from the Ubuntu repositories

To get Hibernate on power failure working, see [http://ubuntuforums.org/showpost.php?p=4302102&postcount=37](http://ubuntuforums.org/showpost.php?p=4302102&postcount=37)

There's even a GUI tool that supplements apcupsd to make it easier to see what's going on with your UPS, the 2nd post has a pointer on this.

---

