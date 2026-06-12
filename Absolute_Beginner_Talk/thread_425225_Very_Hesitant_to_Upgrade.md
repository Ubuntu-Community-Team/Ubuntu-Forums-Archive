---
title: "Very Hesitant to Upgrade"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by dgifford on 2007-04-27
I am on 6.06 on an asus m3000np laptop.  I use this machine for all things, work and play.

I want to move to 6.10 to get firefox 2.0 and the new gnome.

I did go and get the beagle updates from a non-ubuntu source so it would search my Thunderbird email.

I am hesitant to upgrade because of all the reported issues. (cannot afford to lose the system for days)

thoughts?  encouragement? warnings?  I have put a lot of work into this laptop to get it where I want it.

---

### Post by earobinson on 2007-04-27
I would back up your home dir before you do anything. And if its not worth the risk then dont do it.

---

### Post by dgifford on 2007-04-27
The home dir is totally backed up.  Daily

not worried about the data, worried about the system functionality.

---

### Post by Tomosaur on 2007-04-27
I'd just jump straight to Feisty rather than Edgy, it's a massive improvement in my view.

---

### Post by AlexDe on 2007-04-27
Try installing _Simple Backup_ and backup all neccessary files.. then if worse comes to worse just revert :).

```

sudo aptitude install sbackup

```

---

### Post by whee on 2007-04-27
Do you have a spare disk to backup your system on?
There are tools with which you can backup entire drives(all partitions) and when something goes wrong when upgrading then you can just wipe your disk and fetch the backup to restore everything as it was before.(This can be done quite quickly, shouldn't take all day)
That being said, i had bad experiences with Edgy, had to revert back to Dapper which was reasonably ok in my experience.
Feisty is in my experience the best Ubuntu version yet.

I'll give my personal rating:

Dapper: reasonably ok, some glitches and problems here and there, but nothing serious
Edgy: I had nothing but problems with it.
Feisty: quite good so far, i do see some very minor glitches here and there, but compared to my experiences with Edgy and Dapper it seems better in my opinion.

---

### Post by Hendrixski on 2007-04-27
Unlike other operating systems we won't force you to upgrade.  Besides, 6.06 is supported for like another year or two right?

In the future... you can create a separate partition for your information so that if you botch an upgrade it doesn't touch that partition at all... you just reinstall everything from scratch and that partition is still there just like you left it.. and you mount it and TADA.  :-)

But yeah.  Upgrading is fun if you want all the latest stuff... if you don't need to you don't have to.  no pressure.

---

### Post by dgifford on 2007-04-27
can one go from dapper to feisty directly howver?

---

### Post by mrmonday on 2007-04-27
You can get Firefox 2 on dapper, search the forums for guides. You might be able to get the new gnome, but I am not sure. If your PC is valuable to you, I would not upgrade. If it is anything like the upgrade to feisty, its not worth it. 

If you want to upgrade, as earobinson said - backup first, then download the CD, and upgrade from that. I have heard that this is a lot more successful.

---

### Post by whee on 2007-04-27
> **dgifford said:**
> can one go from dapper to feisty directly howver?

You mean upgrading?
I'm not sure, but i don't think it's possible. But maybe there is some uber elite guru way to do it, but i haven't encountered such a way yet, but that doesn't mean it does not exist.
What i do know is that it will be possible to upgrade from LTS(long term support) release to LTS release. Dapper was an LTS release, so it is probably possible to upgrade from Dapper to the next LTS release of Ubuntu, which version of Ubuntu will be the next LTS and when that LTS will be released i do not know.

---

### Post by Patrick K on 2007-04-27
Most likely most apps will run fine. But some items like wireless, sound, and restricted video drivers might have problems. It could take days to sort them out. Automatic partition mounting has cause some, including me, to have to spend time sorting that out. EXT3 partitions mounted fine but Vfat's had (still have) some problems. I don't how well NTFS partitions have faired (I don't use NTFS). 

So, I would say, if you are using native apps, you shouldn't have any problems (wine came through the upgrade for me just fine). If you need access to Windows partition it's somewhat hit or miss. Most haven't had problems. If you need 3d video, the Restricted Driver Manager installed the right Nvidia driver for me. Others haven't faired as well. My wired Ethernet connection worked right out of the box as have most others. I don't use wireless but see a lot of post. Still, I suspect most are connecting without problems, but it does seem the most problematic issue of all. Sound worked right out of the box for me except with DAW apps like Ardour and Hydrogen. Playback of regular source material hasn't been a problem for me but has been for others.

---

### Post by compiledkernel on 2007-04-27
You might be dealing with some breakage for a dapper to feisty upgrade. 

The upstart init thing was the main issue that I ran into when upgrading from dapper to edgy, id assume it would be the same for a dapper to feisty upgrade.

---

### Post by dgifford on 2007-04-27
well after pondering for literal weeks.  I think I am gonna fill sandbags and wait for the next LTS.

Thanks everyone for their thoughs, encouragement and wisdom.

---

### Post by jpatton on 2007-04-27
Couldn't he just modify his sources.list file to point to the fiesty stuff?

---

### Post by mrmonday on 2007-04-27
> **jpatton said:**
> Couldn't he just modify his sources.list file to point to the fiesty stuff?

Dangerous Idea. Don't do this. It can make your system unusable.

---

### Post by mrmonday on 2007-04-27
> **dgifford said:**
> well after pondering for literal weeks.  I think I am gonna fill sandbags and wait for the next LTS.

Thanks everyone for their thoughs, encouragement and wisdom.

That will be a while. I think its Gutsy+1 or +2 that will be the next release.

---

