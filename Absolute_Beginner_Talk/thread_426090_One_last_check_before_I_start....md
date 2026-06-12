---
title: "One last check before I start..."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Game_boy on 2007-04-28
OK. I am a Windows Vista user wishing to try out Ubuntu while keeping Vista intact for the moment.

1. Am I correct in that just burning the CD image and then using the graphical install will **add partitions itself** and therefore leave me with my Vista setup intact?

2. Will I be OK with a Radeon X1950 Pro graphics card? People seem to have had issues.

3. Will a wireless adapter be "plug and play"? It's a Belkin, nothing special.

4. For just trying out Ubuntu, am I right in using Ubuntu over Kubuntu, etc. ?

---

### Post by Sef on 2007-04-28
> 1. Am I correct in that just burning the CD image and then using the graphical install will add partitions itself and therefore leave me with my Vista setup intact?


You will have to manually do the partitioning yourself.  Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing").

> 4. For just trying out Ubuntu, am I right in using Ubuntu over Kubuntu, etc. ?

Yes, because most users on here use Ubuntu, so questions tend to be answered faster and more people can help you.

---

### Post by freebird54 on 2007-04-28
OK - here we go.

1.  Ubuntu live CD's can make partitions, and do the install etc no problem. **HOWEVER - if all disk space is currently used by Vista, use Vista to resize partitions to make empty space!!!!**  Apparently Vista made incompatible changes to NTFS partitions that the LIve CD does not yet handle.

2. People have had issues.  I haven't heard of a proper 'fix' yet, but installing the fglrx driver should work for now.  (ATI makes fglrx for Linux).  This is easy to do, there is a 'sticky'  (permanently present thread) at the top of this forum about  the steps.

3.  Probable, but not certain.  Try it in the Live CD before installing.  If it works on its own, you can surf while installing!

4. I think so - but opinions differ. Kubuntu LOOKS a bit more like Windows, I am told (not sure myself) - and if you are a Windows 'power user' you will appreciate the configurability.  If you stay with the Gnome (standard Ubuntu) setup at first, it will be easier to get help here, and I think it is easier to comprehend at first.  You can switch desktops any time after you get going without loss.

 Hope this answers your questions...

---

### Post by mikewhatever on 2007-04-28
With the previous version of Ubuntu (6.10) it was usually advised not to use GParted tool to resize the Vista partition, but to use the built in Vista utility, whatever that is. The problem seems to be that Vista does not like it when its partition is resized by another program and would not boot afterwards. I am in no way an expert in Vista (never used it), so you might want to wait a minute for another opinion.

To check whether the graphics card and the wireless adapter work, run Ubuntu from the CD. This way it works from RAM only without being installed to the HDD.

---

