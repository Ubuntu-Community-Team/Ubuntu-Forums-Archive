---
title: "lost two ext3 partitions, need to fix partition table"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-10-29
Hello,

yesterday my Ubuntu file server froze suddenly and never came back up. I diagnosed the hard drives and everything seems to be fine. Then I punched in Knoppix and looked at the partitions with QTParted and something is not quite right there. On my first drive no partition was active and the used space of the partition with the OS cannot be displayed (N/A). The parition can't be mounted either:

mount: wrong fs type, bad option, bad superblock on /dev/hda1,

The other paritions on this drive work fine. 

Then there is a second drive in the machine which was configured with one big ext3 partition. This partition shows the same symptoms, the used space can't be determined and it can't be mounted. 

I'm quite sure that the last thing this server was doing was running azureus from the OS partition and downloading a game to the other partition which is broken now. There is a slight chance that there was not enough space for the game anymore. Azureus allocates the space before the download starts and I have a feeling in my gut that that's when the disaster happened.

So my questions are: 

What do I do now to save the data? Is there a magic tool to fix the partition table and have it the same way back as it was before? Or do you know of a method to access the data somehow, so that I can copy it to another drive?

How did this happen? Is it really possible that azureus did this to me by trying to allocate more space than available? (I'm not even sure if that was the case btw, I believe there was enough space yet, but you can always make a mistake).

Thanks,
Cruz

---

### Post by bilal_esz on 2006-10-29
try test disk 6.4 foe windows
if it doesnt work then use partition  magic

hope u still hav ur windows installed

---

### Post by STREETURCHINE on 2006-10-29
i had a simalar problem just fixed it with my computer,try

    sudo fsck /dev/hda1

---

