---
title: "Questions about &quot;/home&quot; partition"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-07-30
It has been said that it is convenient to make a separate "/home" partition so that when one reinstalls ubuntu, settings will not be lost. I have a few questions about this.

When programs are downloaded, where are they actually installed, in the "/" directory or in the "/home" directory? I seem to notice that programs I download manually, outside of the "add/remove" and "Synaptic" seem to have folders "hidden" in my home directory.  Even programs installed through the "add/remove" or synaptic appear to have hidden folders in my "/home" directory.    If this is the case, what percentage of the hard drive should be partitioned for the "/" directory, and what percentage should be partitioned for the "/home" directory?

Also, the "/home" directory seems to be the only directory I can create new folders in. I can't do this in the "/" directory.

I am also questioning having a separate "/home" directory because when I did a reinstall of ubuntu, I did not reformat the "/home" directory and I got a white screen when the OS loaded. Then I needed to reinstall. 

Also, In Gparted, is it necessary to reselect "/home" for the home partition when reinstalling ubuntu even if you will not be reformatting that partition.

Thanks for any answers you can provide.

---

### Post by vexorian on 2007-07-30
The "hidden" folders are all for configuration.

Programs tend to go somewhere in /usr/ although you can customize a source distribution to install in /home/ but that's a manual thing.

I wouldn't really keep a separate /home, I do but it is not all that convenient, and upgrading the distro is actually overrated.

Before reinstalling you can simply move your documents somewhere.

You'll lose configuration, but let's face it, the only meaningful things are configuration for networking, etc and those go to /etc/ not /home ...

---

### Post by Inxsible on 2007-07-30
I have a separate /home. 

When I re-install, I select the same /home for my new install and make sure I DON'T format it. Keeps all my settings intact :)

Of course I do not know what effect it will have if you change your Linux distro, for eg. Debian based to RPM based

---

### Post by bodhi.zazen on 2007-07-30
> **tepidarium said:**
> It has been said that it is convenient to make a separate "/home" partition so that when one reinstalls ubuntu, settings will not be lost. I have a few questions about this.

When programs are downloaded, where are they actually installed, in the "/" directory or in the "/home" directory.  I seem to notice that programs I download manually, outside of the "add/remove" and "Synaptic" seem to have folders "hidden" in my home directory.  Even programs installed through the "add/remove" or synaptic appear to have hidden folders in my "/home" directory.    If this is the case, what percentage of the hard drive should be partitioned for the "/" directory, and what percentage should be partitioned for the "/" directory.  

No, programs are installed on the root or / partition.

See this link for an overview of how Ubuntu is organized : [http://doc.gwos.org/index.php/FileLocations](http://doc.gwos.org/index.php/FileLocations)

The dot files in you home directory are your personnel configuration settings, or in the case of firefox and mail programs (thunderbird) personnel information (ie maiil) for applications and not the program itself.

These are the settings people are talking about preserving with a separate home (as well as personnel data).

> Also, the "/home" directory seems to be the only directory I can create new folders in. I can't do this in the "/" directory.

Yes, this is how Linux works. It is for security, ie users can not change or alter system files. There are a number of reasons for this ...

> I am also questioning having a separate "/home" directory because when I did a reinstall of ubuntu, I did not reformat the "/home" directory and I got a white screen when the OS loaded. Then I needed to reinstall. 

Yes, this is what will happen if you have conflicting configuration options in some of those dot files ...

This is rare, but it is a pain if it happens. Are you running beryl or compiz ?

I usually just make a /data partition for my personal data and mount is in say /mnt/data. You can then link to your home ... 

In a terminal:

ln -s /mnt/data/music ~/music

and on ...

This puts a music directory (folder) in your home directory (~ is short hand for /home/<user_name>)

I do not bother to back up configuration files. I do back up email files ...

> Also, In Gparted, is it necessary to reselect "/home" for the home partition when reinstalling ubuntu even if you will not be reformatting that partition.

Thanks for any answers you can provide.

err... no

You select the home partition and mount it at /home during the install (which is not gparted).

Do not re-format it or you will loose all your data ....

HTH ...

---

### Post by tepidarium on 2007-07-30
Thank you all for your responses.

Do you have any advice on what percentage of the HD should be allocated to "/" and what percentage to "home" (assuming that "/home"  contains all user files (photos, music, word files, etc.)

Right now I am leaning towards just making one Ubuntu partition and no separate "/home" partition.

---

### Post by aysiu on 2007-07-30
If you have a hard drive 30 GB or more and are not dual booting, I'd recommend an 8 GB / partition and leave the rest for /home

If you have less than 30 GB, I wouldn't create a separate /home partition.

---

### Post by bodhi.zazen on 2007-07-30
> **tepidarium said:**
> Thank you all for your responses.

Do you have any advice on what percentage of the HD should be allocated to "/" and what percentage to "home" (assuming that "/home"  contains all user files (photos, music, word files, etc.)

Right now I am leaning towards just making one Ubuntu partition and no separate "/home" partition.

You do not allocate partitions on a percentage basis.

The root partition needs 3-5 Gb as a minimum. 8-10 Gb is likely more then sufficient.

The rest can be /home or /data or /home and /data or another installation of Linux or BSD or what you want.

It all depends on how much data you have and where you want to put it.

I do not understand the distinction aysiu is making on HD size (> or < 30 Gb :confused:)

---

### Post by tepidarium on 2007-07-30
I've got a 120 Gb Hard Drive -(that for some reason indicates 112 GB can be used.)  I've got 1GB of Ram that will be upgraded to 3GB RAM soon.

I've got a Partition for Windows XP and a 5Gb recovery partition. I'd like to keep the recovery partition and limit the windows xp partition to about 40GB.

How would you allocate space between "/" and "/home" and "/swap" for the remaining 57 GB that would be free on my HD?

Thanks.

---

### Post by bodhi.zazen on 2007-07-30
> **tepidarium said:**
> I've got a 120 Gb Hard Drive -(that for some reason indicates 112 GB can be used.)  I've got 1GB of Ram that will be upgraded to 3GB RAM soon.

I've got a Partition for Windows XP and a 5Gb recovery partition. I'd like to keep the recovery partition and limit the windows xp partition to about 40GB.

How would you allocate space between "/" and "/home" and "/swap" for the remaining 57 GB that would be free on my HD?

Thanks.

/swap = 1 Gb # if you use  hibernation on a loptop you will need 3 Gb
/ = 10 Gb
/ home= 2 Gb
/data = rest

You can combine /home and /data into one large /home if you like.

Up to you ... It is not critical, you can always resize your partitions later if you like ...

---

### Post by aysiu on 2007-07-30
> **bodhi.zazen said:**
> 
I do not understand the distinction aysiu is making on HD size (> or < 30 Gb :confused:) Well, if you have less than 30 GB it's more likely that you'll allocate too much space for one partition or another, depending on how much data you have or how many programs you install eventually.

---

### Post by bodhi.zazen on 2007-07-30
Thanks, I knew you had a good reason, I could not fathom it ...

---

### Post by aysiu on 2007-07-30
> **bodhi.zazen said:**
> Thanks, I knew you had a good reason, I could not fathom it ...
It's just a recommendation anyway. It's entirely possible and maybe even advisable in certain situations to have a separate /home partition for a small hard drive.

---

### Post by bodhi.zazen on 2007-07-30
he he he ... Well, there are more then one way to skin the cat, that is the beauty of Linux. I am not sure any one way is "better" or "best" in most cases, although it can be confusing to some that there is no single right answer ...

For the benefit of others, you can always resize your partitions if you need to, although moving them can be messy.

To tepidarium : Sorry to hijack your thread ...

---

### Post by tepidarium on 2007-07-30
> **bodhi.zazen said:**
> /swap = 1 Gb # if you use  hibernation on a loptop you will need 3 Gb
/ = 10 Gb
/ home= 2 Gb
/data = rest

You can combine /home and /data into one large /home if you like.

Up to you ... It is not critical, you can always resize your partitions later if you like ...

Thanks for the answers, just one more question - 

do you really suggest allotting only 10GB for the "/" partition?  If that's where the main OS files are and where all the programs are installed, couldn't that run out of space fast?

Thank again.

---

### Post by aysiu on 2007-07-30
Yes. In fact, 10 GB would be the max for the / partition. I have never gone over 4.5 GB, even with a *lot* of programs installed.

Most of the room will be taken up by your personal files (music, videos, pictures, documents, etc.), and those live on the /home partition.

Or, if you follow bodhi.zazen's advice you quoted, they'd live on the /data partition.

---

### Post by luckyd on 2007-07-30
Hi, sorry to ask another question, but I have heard many good things about having a separate home partition, especially if you muck up you system and need to reinstall. What I wanted to know, is if there was a way for me, who already has a one partition (not including swap :)) system too set a separate partition now?

---

### Post by bodhi.zazen on 2007-07-30
> **luckyd said:**
> Hi, sorry to ask another question, but I have heard many good things about having a separate home partition, especially if you muck up you system and need to reinstall. What I wanted to know, is if there was a way for me, who already has a one partition (not including swap :)) system too set a separate partition now?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[color=blue]Thanks aysiu[/color]

---

