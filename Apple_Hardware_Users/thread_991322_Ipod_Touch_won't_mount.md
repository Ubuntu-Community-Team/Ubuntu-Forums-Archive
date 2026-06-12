---
title: "Ipod Touch won't mount"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by Shiloh Hawkesworth on 2008-11-23
I am trying to get my Ipod Touch to mound and this is what I get:

shiloh@chondro:~$ sudo ipod-touch-mount
[sudo] password for shiloh: 
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.
shiloh@chondro:~$ 


What am I missing?

---

### Post by Shiloh Hawkesworth on 2008-11-30
Bump

---

### Post by rakan21 on 2008-11-30
Are you using the 2.0 software? 
Remember 2.0 won't work. 

check out this tutorial [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by Shiloh Hawkesworth on 2008-12-01
Yes, I am using 2.2 

How can I go back? And how can I prevent it from updating?

---

### Post by damis648 on 2008-12-01
2.X will work, but you cannot sync music. It seems that you did not enter the right ip address, but just 'iPod'. Follow each step in the guide linked above.

---

### Post by Shiloh Hawkesworth on 2008-12-01
2.X will work, but you cannot sync music.

Does that mean it won't grab the music automatically? So I have to do it manually? Or does that mean I can't put music on it at all?

---

### Post by damis648 on 2008-12-01
> **Shiloh Hawkesworth said:**
> 2.X will work, but you cannot sync music.

Does that mean it won't grab the music automatically? So I have to do it manually? Or does that mean I can't put music on it at all?

Not at all. I am afraid Apple has locked it down to iTunes only by having the iPod checksum it each time iTunes syncs, so without iTunes, the music will not show up on the iPod.

---

### Post by Shiloh Hawkesworth on 2008-12-01
Even if I go back to a version pre 2.x? OR has apple totally locked us out now, regardless of the version?

---

### Post by damis648 on 2008-12-01
> **Shiloh Hawkesworth said:**
> Even if I go back to a version pre 2.x? OR has apple totally locked us out now, regardless of the version?

No, if you go back to 1.1.4 it will work.

---

### Post by Shiloh Hawkesworth on 2008-12-01
The steps to revert back seem to be removed. Anyone know how to revert back to 1.1.4?

---

### Post by damis648 on 2008-12-01
Yes. To do so, you will need the original firmware file. If you have it, plug in your iPod and hold down the sleep and home buttons on your iPod until the screen goes dark. Then, let go of the sleep button but keep holding the home button until iTunes recognizes the iPod. From here, hold down the shift key and click on the restore button on iTunes for your iPod, and select the 1.1.4 firmware file when prompted.

---

