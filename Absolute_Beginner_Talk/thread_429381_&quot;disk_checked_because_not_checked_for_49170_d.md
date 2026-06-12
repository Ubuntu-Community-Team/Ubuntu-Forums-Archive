---
title: "&quot;disk checked because not checked for 49170 days!&quot;"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-05-01
Hi all,

Just curious here...

I did a Feisty fresh install and you all know how it needs to reboot after a while. So it did and I was told it needed to run chdisk because it had not been ckecked for nearly 15 years!!

Any thought on that? Is it some kind of devs' joke? Sure had me laughing.
Thnx.

---

### Post by Malta paul on 2007-05-01
When 4.04 is first installed it dose a system fill check (the first one) showing 49170 days. After that it will carry out a FSCK's after about every 37 boot ups and will give the correct number of boots before the forced check .:)

---

### Post by ubnewbie2 on 2007-05-01
Yep, I have installed it 3 times, and it always does this.  Just another little bug they need to clean up I guess.

---

### Post by locke.dragon on 2007-05-01
lol! :D i've never had this problem, but it sure if funny!  ;)

---

### Post by ubnewbie2 on 2007-05-01
I think it's related to the first error it gives, which is that the Superblock says it was last mounted in the future.  When it fixes this, the result seems to be that it thinks it hasn't been checked in a long time.

---

### Post by xyz on 2007-05-02
Thanks folks!:lolflag:

---

### Post by Steve H on 2007-05-02
I saw that when i upgraded to Feisty, I presumed it was just a way of "Forcing" the disk check. I mean if you ain't checked it in 15 yrs , it will sure need it!! :)

---

### Post by BipolarChucker on 2007-05-02
You may find this is because you told Ubuntu when you were installing that your BIOS clock was set to UTC, when infact it is probably not. I had a problem with SUDO when this happened.

I'm guessing on the remedy here but I think that once Ubuntu attempts to update the time from an atomic time server (ntpdate?), it sets the superblock in (as far as the system is concerned) the future.

You may be able to rectify it with tzconfig, alternatively, you should actually set your BIOS clock to UTC.

---

### Post by ubnewbie2 on 2007-05-02
> **BipolarChucker said:**
> You may find this is because you told Ubuntu when you were installing that your BIOS clock was set to UTC, when infact it is probably not.

Actually I don't remember ever dealing with that question.  I just clicked on my country/city on the map, and the clock then showed the right time.  I never actually told it what my BIOS was set to.

---

### Post by xyz on 2007-05-03
> **BipolarChucker said:**
> You may find this is because you told Ubuntu when you were installing that your BIOS clock was set to UTC, when infact it is probably not. I had a problem with SUDO when this happened.

I'm guessing on the remedy here but I think that once Ubuntu attempts to update the time from an atomic time server (ntpdate?), it sets the superblock in (as far as the system is concerned) the future.

You may be able to rectify it with tzconfig, alternatively, you should actually set your BIOS clock to UTC.

I'll check it out. Thnx.

---

### Post by jkblacker on 2007-05-03
Yeah again, I had this when installing - and then when I first booted back into xp, that forced a disk check as well, possibly something to do with the partitioning having changed and windows not knowing about it yet?

The 15 years thing seems to have had no adverse effect, though.

---

### Post by Lucifiel on 2007-05-03
Hmm, I remember someone telling me that disk checks are normal because it's just Feisty checking if the partition has any problems.

---

### Post by xyz on 2007-05-03
> **Lucifiel said:**
> Hmm, I remember someone telling me that disk checks are normal because it's just Feisty checking if the partition has any problems.

Yes it is "normal" but not 'that' necessary.
If your Ubuntu is on ext2 or ext3 partitions, you can also set it to check disk at so and so boot.

---

### Post by ubnewbie2 on 2007-05-03
Yes, checks are normal, but finding large errors isn't. :)

---

