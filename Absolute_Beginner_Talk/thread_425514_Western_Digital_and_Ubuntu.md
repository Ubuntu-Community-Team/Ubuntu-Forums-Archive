---
title: "Western Digital and Ubuntu???"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-04-27
I'm thinking of buying a new External Hard Drive which will replace my current one (which will be used for System Backups). I am looking at a Western Digital MyBook 320gb ([Link]("http://www.amazon.co.uk/Western-Digital-320GB-Essential-External/dp/B000EXZB02/ref=sr_1_4/202-7894164-3156603?ie=UTF8&s=electronics&qid=1177706616&sr=1-4")) but it is not clear on any websites whether this has any Linux Drivers/Will format with FAT32 (Need to use it for both Windows ( :( ) and Ubuntu ( :) )).

Anyone know whether this would work or anyone using one of these with Ubuntu at the moment?

---

### Post by Bachstelze on 2007-04-27
No need for drivers. At worst, it will come preformatted but ou can still reformat it in any other filesystem you wish.

---

### Post by starcraft.man on 2007-04-27
> **bobbocanfly said:**
> I'm thinking of buying a new External Hard Drive which will replace my current one (which will be used for System Backups). I am looking at a Western Digital MyBook 320gb ([Link]("http://www.amazon.co.uk/Western-Digital-320GB-Essential-External/dp/B000EXZB02/ref=sr_1_4/202-7894164-3156603?ie=UTF8&s=electronics&qid=1177706616&sr=1-4")) but it is not clear on any websites whether this has any Linux Drivers/Will format with FAT32 (Need to use it for both Windows ( :( ) and Ubuntu ( :) )).

Anyone know whether this would work or anyone using one of these with Ubuntu at the moment?

I have a friend who I think runs his Ubuntu off of a western digital, I don't really see why ya'd need specific drivers. As for sharing it with windows, you might wanna just look at ntfs-3g, from everything I've heard its very stable.

Network attached storage is always the other solution, ethernet is the great equalizer caring not what filesystem you use :)

---

### Post by chalex on 2007-04-27
It will work fine, as will any other brand.

---

### Post by Happy_Man on 2007-04-27
Most any external drive will work with Ubuntu, but you don't need to format it as FAT32 for access from Windows and Ubuntu. There are ext3 drivers available for Windows at [http://fs-driver.org](http://fs-driver.org), so you can just format your drive as ext3, and still enjoy full access.

---

