---
title: "5GB hard drive enough for Feisty to be &quot;happy&quot;? (and what about RPMs?)"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by strider_mt2k on 2007-08-22
I have a little Ubuntu Feisty system that I've built from spare parts.

My current HD is a 40GB 4200RPM 2.5-inch laptop drive and the system runs pretty well with it. 

I was just given a 5GB 7200RPM 3.5-inch desktop drive, however that I think might be a bit better performer PROVIDING that it is big enough for Ubuntu Feisty and it's swap file.

My plan is to use the 5GB drive for the OS and core applications and set the 40GB drive up for use as a secondary drive internally if I can, although the system's ultimate mission will be as an internet and office app. appliance with maybe some DVD playing when I sit down to set THAT up.
(Awesome tutorials here on that subject, BTW)

My question:
Will Ubuntu Feisty and it's core apps.  run "happily" on as little as a 5GB HD, and will the faster RPMs make enough of a difference to make it a worthwhile "upgrade" from the laptop drive??

I tried a few searches here to this effect using different criteria and I know Ubuntu needs at least 3GB and possibly as much as 8GB to be "happy", but I think ultimately some advice from you fine folks will help me decide this one out.

Thanks!

---

### Post by Clay_Banger on 2007-08-22
as far as RPM's is concerned, 7200 is plenty fast enough.

and i think that 5 gb should be enough, as long as you dont install to many large applications, (games etc.), i'm only using 4gb of my 15 root partition.

---

### Post by Arthur Archnix on 2007-08-22
I currently have Feisty installed on a 4.7GB partition, with every program I could want, many I don't use, and all updates. I'm currently using about half the space. That partition is holding everything, root, home, you name it.

I keep all my files on a separate partition. Music, files, etc. 

You'll have no problems using your 5 GIG to run your swap, and Feisty with both / and /home set to the 5gig.

Edit: Just read the whole desktop/laptop thing, you know you won't be able to plug a desktop drive into your laptop right? I think you may have somehow setup a laptop drive to run in your desktop computer, if that's the case please excuse me.

Best,

---

### Post by Hobo Joe on 2007-08-22
Yes it will run fine. 4200 is a bit slow, but it'll still run without issues.

As far as it being 'worthwhile' to upgrade, that all depends on your budget and how much you are willing to spend.

5GB will house Fiesty without problems, however, if you were planning on installing lots of apps or putting data on it, you'll want to be careful that you don't overfill it.

---

### Post by Jimmyfj on 2007-08-22
according to this system spec it should be enough:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

But I'm not sure.

---

### Post by strider_mt2k on 2007-08-22
Thanks again folks!

Looks like moving to the other drive will be well worth it!

---

### Post by HermanAB on 2007-08-22
5GB is tons of space for Puppy Linux, but somewhat tight for Ubuntu.  Dedicate your second drive to /home and when the smaller and faster drive gets full, repartition it and move /var over.

---

### Post by strider_mt2k on 2007-08-27
Not surprisingly, I've obtained a 10GB drive that will surely do the trick.

I thought 5 was a little tight myself.

---

