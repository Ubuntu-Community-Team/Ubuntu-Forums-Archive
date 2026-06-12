---
title: "partition"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-02-08
Hi I just partitioned my hard drive to add a second distro in the gparted info it says I need to create a swap file but I think suse can use the swap for ubuntu. the info on gparted is for a window linux dual boot exactly what kind of files do I need to create for a second linux install? Thanks Dan

---

### Post by hyper_ch on 2008-02-08
you can use the existing swap partition for the suse swap.

Can you elaborte the other issue?

---

### Post by perlluver on 2008-02-08
I would reccomend using a seperate swap partiton.  In all my reading that seems to be the way to go.  Nothing will get mixed up, and either system can't screw up the other.

---

### Post by Paqman on 2008-02-08
Different distros can share a swap partition quite happily. Same goes for a /home partition, although it might be best to have seperate users for the different distros.

Generally, you only need to create a new / partition to install a second distro.

---

### Post by hyper_ch on 2008-02-08
> **perlluver said:**
> I would reccomend using a seperate swap partiton.

Why? Swap is nothing more then temporary ram. You can use the same swap partition for hundred different distro installs.

---

### Post by perlluver on 2008-02-08
> **hyper_ch said:**
> Why? Swap is nothing more then temporary ram. You can use the same swap partition for hundred different distro installs.

I thought I read that swap partitons had to be seperate, however it looks like it is just home.  You can use the same space but they reccomend another partiton for home.

---

### Post by hyper_ch on 2008-02-08
it's an own partition - hence it's seperate.

A different partition for home might be recommended. Different distros ahve different default settings so when booting into another distro while using the same home you could get some unexpected results.

---

### Post by Paqman on 2008-02-08
> **perlluver said:**
> I thought I read that swap partitons had to be seperate, however it looks like it is just home.  You can use the same space but they reccomend another partiton for home.

Separate user accounts maybe, but as long as your /home is in a file system that all distros can use I don't see any need to create a seperate partition

---

### Post by maineman2 on 2008-02-08
Well Im new to this and I need to know How many and what kind of partitions do I need in my 20 gib partition? Can I just leave it on big partition? How do I name this Hda7/ Thanks Dan

---

### Post by perlluver on 2008-02-08
> **Paqman said:**
> Separate user accounts maybe, but as long as your /home is in a file system that all distros can use I don't see any need to create a seperate partition

Thank you, you learn something new everyday, right?

---

### Post by hyper_ch on 2008-02-08
> **maineman2 said:**
> Well Im new to this and I need to know How many and what kind of partitions do I need in my 20 gib partition? Can I just leave it on big partition? How do I name this Hda7/ Thanks Dan
You really only need 1 partition. That's the root ("/") partition and it is recommended to make it Ext3 as type. The root partition should be at least 4-5 GB, 10 GB would be better...

However swap is recommended, especially when you're on a notebook and want to hibernate or sleep. In that case the swap must be at least equally large as your ram (so that all data from your ram can be written to the swap).

If you have enough ram (1GB or more) then it depends on what you want to do. Mostly you probably wouldn't need a swap partition either. However if you like to have many programs open, it is better to have it. General rule of thumb I'd say with 1 GB ram you should probably have 1.5 - 2 GB swap partition. The type is "swap"


A home partition is mostly also recommended. That would be the one where you store your documents, music, videos, configuration settings that affect single users... the mountpoint for it is "/home" and also Ext3 is recommended.

---

### Post by kenvac on 2008-02-08
cool....i got tonnes of info from u guys.....

---

### Post by hyper_ch on 2008-02-08
in the end it will be your preferences how you want to partition it. In the beginning I also had a seperate home... I don't see the need for it any longer, as  do regular backups on a different computer and because I have written myself an (almost) automatic reinstall script...

In windows you can't choose... here you can... different people, different needs and hence different approaches and solutions.

---

### Post by maineman2 on 2008-02-08
I have a 15 gb partition for open suse but open suse tries to install over ubuntu when I direct it to load in hda7 it says its already in use I have it labeled as ext 3  what do I have to label this as to get suse to load on that partition? Dan

---

### Post by maineman2 on 2008-02-08
> **maineman2 said:**
> Hi I just partitioned my hard drive to add a second distro in the gparted info it says I need to create a swap file but I think suse can use the swap for ubuntu. the info on gparted is for a window linux dual boot exactly what kind of files do I need to create for a second linux install? Thanks Dan

new problem at bottom

---

