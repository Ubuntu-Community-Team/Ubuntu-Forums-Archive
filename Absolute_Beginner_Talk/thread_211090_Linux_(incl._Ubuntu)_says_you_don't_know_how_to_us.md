---
title: "Linux (incl. Ubuntu) says you don't know how to use me, you are f&amp;*%$#"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by leo_m on 2006-07-07
...or actually, it does not say anything.  Do not believe? Try this...

Use the Administration|Networking to set hostname to a value containing an apostrophe (') - Ubuntu won't bat an eyelid and let you do that.

And after that, you won't be able to use this tool again...until...

a) you ```
sudo vi /etc/hosts
``` and remove the offending apostrophe (') then save the file.
b) and you ```
sudo vi /etc/hostname
``` and remove the offending apostrophe (') there too and save that file.

The modified name should be the same in both the files.

Then reboot and you will be back to normal.

The quirks of Linux are cute features - experienced persons will say, oh you do not know the features of shell, including handling of hyphens, single quotes et al? ...and then you are suddenly an outcast n00b (thankfully, not in Ubuntu though - here you can expect help, this post is an example).

In summary, use the apostrophe, hyphens and a few others carefully while you are in Linux...it won't warn you (darn...) but it will obligingly do the damage because it thinks it is being used by knowledgeable persons...would be helpful if safeguards were provided in applets like networking tool.

Be warned, you are likely to become wiser when you use Linux - it will force you to be...sooner or later ;) (not that it's a bad thing to be wiser...)

---

### Post by Bloch on 2006-07-07
I became wiser by using Linux. At least, I know a lot more about computers.
How did you attain wisdom without Linux?

---

