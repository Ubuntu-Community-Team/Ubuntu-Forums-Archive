---
title: "Motherboard change/reinstall Issue."
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-07-24
Okay, so I replace the motherboard in my wife's Ubuntu Feisty machine.  I reboot and lo and behold, it doesn't seem to need a reinstall.

So I start poking around and several things aren't working.  "No problem," I think, "I followed the instructions on how to make a separate /home partition and I should be able to just reinstall without headaches."

Unfortunately, I guess I'm too inept to perform a reinstall that's apparently so simple that none of the "create a separate partition for /home" advice bothers to explain.


I popped in the Live CD, clicked install, set everything up the same way as usual except I go to Manual for the partition, designate the old /home partition as the /home mount point and the old filesystem partition as the / (root) mount point.  I click the format box for the root partition (because you have to) and don't format any others.

I set it up with "temp" as the user (since I'm not sure what would happen if I told it to use one of the existing usernames) and it does the whole install thing without a hitch.


However, when I reboot without the disk I can't log in as either of the previous user accounts, and when I try to login as "temp" I get some kind of error about how /home/temp doesn't exist and would I like to try to login as root even though that probably won't work.  Which it doesn't.

I need to get this fixed, quickly, and preferably without completely hosing or wiping out my wife's settings (since I find it infinitely more enjoyable to *not* annoy the crap out of her.)

Help?  I've rebooted with the Live CD and the /home partition appears intact - and has a "temp" folder in it.

Update: Without actually doing anything the computer now will reboot and login as "temp".  However, the original user accounts are still not working.  Also, I'm getting graphical artifacts and audio static.  The restricted drivers will not activate.

---

### Post by trent dillman on 2007-07-25
...

---

