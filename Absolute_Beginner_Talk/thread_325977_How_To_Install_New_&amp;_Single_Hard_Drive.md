---
title: "How To Install New &amp; Single Hard Drive?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Browzer on 2006-12-26
Hello,

Yes, it's another hard drive question, but I haven't seen my problem described here.

I have a Dell.  I took out the old hard drive when it stopped getting recognized.  I put in a new one.  There is nothing on the new & lone hard drive.  How do I get my machine to recognize the new, lone hard drive?  I can run the Ubuntu boot cd and get into the GUI, but I can't find any way to recognize the HD (there are no devices listed when I try to do an install).

My intent is to give the whole hard drive to Ubuntu.  The machine is basically a 20lb door stop right now, so I'd like to try out Ubuntu on it.

---

### Post by pay on 2006-12-26
Make sure the jumpers on the harddrive are correct for a single master harddrive.

---

### Post by merlyn on 2006-12-26
Hi,

What type of hard drive do you have, is it SATA or IDE? Also is it detected when you boot up your system?

Cheers.

---

### Post by Browzer on 2006-12-26
Hi,

It's an IDE Western Digital drive.  For a single drive, the jumper should be removed.  

My BIOS is not able to detect the hard drive, either.  Is the BIOS supposed to automatically detect a brand new drive?

---

### Post by Talon2 on 2006-12-26
> **Browzer said:**
> Hello,

I have a Dell.  I took out the old hard drive when it stopped getting recognized.  I put in a new one.  There is nothing on the new & lone hard drive.  How do I get my machine to recognize the new, lone hard drive?  I can run the Ubuntu boot cd and get into the GUI, but I can't find any way to recognize the HD (there are no devices listed when I try to do an install).

My intent is to give the whole hard drive to Ubuntu.  The machine is basically a 20lb door stop right now, so I'd like to try out Ubuntu on it.

PATA or SATA drive?

Have you got a spare cable (PATA or SATA) that you could try?

Are the connections good?

---

### Post by merlyn on 2006-12-27
Given that you are certain of the jumper settings, I would go with the previous post, and try swapping out the data cable.

If the drive, and cable are ok, and the drive is receiving power the BIOS will detect the presence of the drive.

Two other things to look for would be that the hard drive activity light comes on during boot and that you can hear the drive spinning up.

Also watch your screen when booting, if somethings up you should get an error message.

Cheers.

---

