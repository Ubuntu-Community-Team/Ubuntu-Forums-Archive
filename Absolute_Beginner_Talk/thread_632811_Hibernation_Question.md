---
title: "Hibernation Question"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Derekrocks14 on 2007-12-05
Uh..this is my first post. This is something I've always wondered about hibernation. If I go to hibernation and save it to the hard disk (its the root partition i think) what happens to the information that was saved about the session for hibernation. Is it deleted when I resume k/ubuntu? I know if its saved to RAM..RAM regenerates over time.

---

### Post by Hospadar on 2007-12-05
Well I believe (I'm not totally sure, but pretty sure) that what happens when you hibernate is that certain parts of ram (perhaps all of it in some cases) get saved out to the hard drive, generally the parts pertaining to user processes I believe, and then when you resume from hibernation, the ram that was saved to disk gets deleted off the disk, so you don't have to worry about loosing a gig of disk space every time you hibernate.

The reason it gets saved to disk is because normal RAM requires power to hold it's data, so saving ram out to disk allows the machine to use a lot less power during hibernation.

---

### Post by Derekrocks14 on 2007-12-06
Thanks that's what I needed to know. I think I confused the save to RAM with Standby/Suspend option.

Thanks.

---

