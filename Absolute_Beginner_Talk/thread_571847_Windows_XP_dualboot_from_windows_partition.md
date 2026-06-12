---
title: "Windows XP dualboot from windows partition"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by alphasurfari on 2007-10-09
I read some older threads on this, but didn't understand what was going on.. I want to understand how to fix GRUB, so I am posting this new thread. 

Originally I had my Dell Inspiron 600m dual booting XP and ubuntu. I used these instructions: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

I removed that drive and put it in an external. Did a clean install of Kubuntu with a new drive in the laptop. Now I am trying to get the windows partition back off the external, onto the laptop and booting. I have used GParted to resize and copy the XP partition back onto the laptop. But it isn't showing up in GRUB. How do I get it there?

Here are my partitions:

/dev/sda1 ext3 (the kubuntu install)
/dev/sda4 fat32 an area that both the kubuntu and XP boots should be able to read so I can exchange files
/dev/sda3 ntfs the windows partition
/dev/sda2 extended inside which is /dev/sda5 which is the linux swap

So how do I set up GRUB? Am I missing some other step perhaps?

Thanks

---

### Post by Joeb454 on 2007-10-09
I think Windows only boot's if it's the first on the Disk...although my 'buntu is first, I dual boot Ubuntu and Vista (was XP/Vista so think that's why). And I don't think copying straight from one drive to another would work, though I could be completely wrong.

---

