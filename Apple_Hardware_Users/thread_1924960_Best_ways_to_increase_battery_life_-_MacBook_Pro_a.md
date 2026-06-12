---
title: "Best ways to increase battery life - MacBook Pro and Ubuntu (dual boot)"
date: 2012-02-13
forum: Apple Hardware Users
---

### Post by dresde on 2012-02-13
Hello all!

I have been searching trough the for and Google but I couldn't find up to date replys to the battery life when running Ubuntu in a MacBook Pro through dual boot.

When I boot into Mac, let's say battery is at 89% and it says that's going to last 3 hours. If I boot right after into Ubuntu, it says battery is going to last just 1 hour. And its not just a matter of different ways to calculate, since I have really noticed that Ubuntu drains my battery.

Also, when using Ubuntu the laptop heats up way more and once in a while the vent starts working like crazy.

So.... what are the best ways to reduce battery use - heating up while in Ubuntu?

Thanks!

---

### Post by sauferkel on 2012-02-15
Hey

i tried to reach a battery life like in OSX for some weeks now. I could increase it, but i did not get to the OSX power consumption (3-5 watts in idle on a MBP 7.1 !) I ended up with around 6.5 to 7 on idle.

What i did:

Install powertop and look for their suggestions, laptop-mode-tools can handle most of them. ->

Install laptop-mode-tools, general configuration is in /etc/laptop-mode/laptop-mode.conf , but there are several more config files in /etc/laptop-mode/conf.d/

Install phc-kernel + patch to undervolt the cpu, helps really a lot! - lifetime increases and heat is reduced. [http://www.linux-phc.org/]("http://www.linux-phc.org/")

I mount /tmp /var/log and /var/tmp to ram to reduce disk activity when my system runs fine. I know it is NOT recommended , since you loose your log files on reboot, but i rarely use them.


Here you can find some more information about it : 
[http://www.lesswatts.org/index.php]("http://www.lesswatts.org/index.php")
[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption")

Besides all this, 12.04 will have a lower power consumption, but you can't use the phc-kernel atm.

Hope this helps a bit, if there are more questions, just ask.

good luck :)

cheers
henning

---

### Post by naggu on 2012-02-26
Yea, I have exact issue like OP too.

---

