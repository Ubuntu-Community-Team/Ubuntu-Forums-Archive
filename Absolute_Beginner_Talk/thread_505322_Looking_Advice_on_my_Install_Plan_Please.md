---
title: "Looking Advice on my Install Plan Please"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by RhubarbnCustard on 2007-07-20
Hi - I'm going to wipe my drives and do a standalone Feisty Dawn install. This is how I was thinking of setting up my partitions:

/boot  20MB  1st primary partition
/          10GB
/swap 564MB
/home all the rest

My system is:  IBM 300PL PII 400; 281.7MB RAM; Master Drive 30GB; Slave 20GB; Ethernet Pro 100
Currently dual boot with XP and Feisty Dawn.

I'm going to dban the disks first then set up the partitions using the Ubuntu install (GPart?). Will this be reasonably straightforward? I've read a few of the guides recommended on the forum, and I've used Partition Magic a bit, but I'm a bit unsure about the /boot partition and how I tell GPart what I want (eg, will I be asked for sizes in numbers of 1024K blocks?)

So any tips please? 
Cheers

---

### Post by Skrynesaver on 2007-07-20
Looks sane and sensible to me from a partitioning perspective.  The installer on Feisty walks you through the partitioning very smoothly. Just put in your boot partition first and all should go well.  As far as I remember it does ask you for sizes rather than cylinders and makes partitioning very handy indeed

---

### Post by Happy_Man on 2007-07-20
GParted asks for sizes in terms of megabytes, which makes it easy for partitioning idiots like me :p

Other than that, though, everything looks pretty good.

---

### Post by RhubarbnCustard on 2007-07-20
Thanks peoples.

I've got my clean drives, and I'm now trying to set up the partitions using the 7.04 install but I can't see how to get /home to include the slave drive as well as what's left over on the master after I've indicated my other preferences. Am I trying something daft? I have 20 gig left over on the master (and 20gig unused on the slave).

Also I notice the install partitioner won't let me set the /boot partition as 20MB and changes it to 16MB. Is this because that's all that's needed?

Any ideas please?

---

### Post by alienexplorers on 2007-07-20
Basically the same setup I am running on my slave 40GB drive and it works great.  My primary 30GB drive is for Windows XP.

---

### Post by RhubarbnCustard on 2007-07-20
Hey alienexplorers - I'm envious of your hardware :-))

---

### Post by trak87 on 2007-07-20
20mb for /boot is not enough. My /boot partition with Feisty currently contains 42mb of data. My partition is 100mb.

---

### Post by grishenko2000 on 2007-07-20
it just means that you have to clear out old kernel images after you have updated and no longer need them.
You would be able to keep only about 2 with 20g though

---

### Post by RhubarbnCustard on 2007-07-20
Ok Trak87, thanks - I haven't actioned anything yet so I'll change that - the install is sitting on the other workspace.

Any ideas on using the other drive?

Cheers

---

### Post by RhubarbnCustard on 2007-07-20
Thanks Grishenko too - getting out of synch here as everything's a bit chunky running off the cd

---

### Post by trak87 on 2007-07-20
> **RhubarbnCustard said:**
> Any ideas on using the other drive?

No need to worry about the other drive at this point. You can always partition it in any way you want later.

---

### Post by RhubarbnCustard on 2007-07-20
Thanks Trak87.

Well the install is done and I'm just going to copy over my backed up video settings (once I've worked out how to do that) and I can start playing with my setup.

In the end I realised I just had to mount the 2nd drive as "/whatever" and bob's my aunty.

Thanks for everyones help and support - it was a lot easier than I thought it would be. No doubt I'll be thinking aloud on the forums again in the near future (or just plain begging for help.....)

---

