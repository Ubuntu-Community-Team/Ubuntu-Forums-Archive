---
title: "ati radeon 9200"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-03-26
how do i install ati radeon 9200 drivers, i have ubuntu 8.04 

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) , is where i can download them from, but it only support xcog 7.1, hardy runs on 7.3

Also do you think there will be a issue

---

### Post by mikeyphi on 2008-03-26
> **ibizatunes said:**
> how do i install ati radeon 9200 drivers, i have ubuntu 8.04 

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) , is where i can download them from, but it only support xcog 7.1, hardy runs on 7.3

Also do you think there will be a issue

Big discussion here: [http://ubuntuforums.org/showthread.php?t=722943&highlight=ati+radeon+9200](http://ubuntuforums.org/showthread.php?t=722943&highlight=ati+radeon+9200)

check this out also: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by forrestcupp on 2008-03-26
I was under the impression that the open source drivers that are installed by default work perfectly with the Radeon 9200.  I think you can just use what you have and even run Compiz without problems.  You shouldn't need to install anything else with the card you have.

---

### Post by ibizatunes on 2008-03-26
i found there is a bug with the 9200 open source driver, if you fast user switch then you can have compiz running, basically it runs for 1 user reboot and then another user can user the full features, i was wondering if i could installed "closed" driver and see if this fixes the issue
I have already filled a bug in about this issue

---

### Post by forrestcupp on 2008-03-26
Well, you can either install the drivers in the Restricted Drivers Manager and use Xgl to run Compiz, or you can use [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to install ATI's newest proprietary drivers that don't require Xgl anymore.

---

### Post by ibizatunes on 2008-03-27
Envy wont work as it doesnt support legacy drivers 9200 needs legacy :(

I think i will have to try and install restricted drivers, but they dont appear in the manager currently

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

hopefully that is the same in 8.04

If that doesn't work then i will install XGL, am i right in thinking that is in the repo?

---

### Post by Circus-Killer on 2008-03-27
afaik, the restricted drivers wont work with the lagacy radeon 9200. i have the same card on my desktop, and i use the open source drivers, which run perfectly.

---

### Post by ibizatunes on 2008-03-27
Yes they work fine, except if u fast user switch, basically if you fast user switch it doesn't use compiz correctly in the new user,
if you reboot login with a different person account detail it works fine, just not if you fast user switch

Any ideas?

---

### Post by ibizatunes on 2008-03-27
bump

---

### Post by ZamueL on 2008-04-22
Hi all,

I am also having huge problems installing the drivers on 8.04
Not sure if you have upgraded circus-killer but in your profile it says
you are using 7.10. Nearly every forum i have found has people saying it works when they are not using 8.04 (no offense in any way).

If anyone has any miracles let me know.

So frustrated i am shopping for a new card but i would like to get this to work so i can play wow and wc3 and keep windows out of my life..lol

---

