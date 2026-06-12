---
title: "Which entry in /dev?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by MrHorus on 2006-08-05
I'm not a newbie but this is something glaringly obvious that I *should* know but don't... :P

I have a USB GPS reciever which DOES have a driver and DOES work out of the box but I want to write a custoemr Java application to parse and handle the raw signals from the sattelite and I need to know where to get the data from.

Now I know the unit will map as a serial device somewhere in /dev but for the life of me I can't figure out how to identify which entry.

Is there simple commend or something that I can use that will show me these mappings?

As I say, I am sure this is some glaringly obvious one-liner... :)

---

### Post by neilp85 on 2006-08-05
What I usually do is plug in the device and run dmesg. There should be some messages about where the device was mounted. Try this a couple times and see if it always gets mounted at the same place. If it gets mounted at different places you could probably write a small script that runs the output of dmesg through sed or something similar to see where it is currently mounted and give that result to your java app.

---

### Post by MrHorus on 2006-08-05
> **neilp85 said:**
> What I usually do is plug in the device and run dmesg. There should be some messages about where the device was mounted. Try this a couple times and see if it always gets mounted at the same place. If it gets mounted at different places you could probably write a small script that runs the output of dmesg through sed or something similar to see where it is currently mounted and give that result to your java app.

It's a GPS reciever, not a hard drive so since it has no file system it won't actually be mounted anywhere.

---

