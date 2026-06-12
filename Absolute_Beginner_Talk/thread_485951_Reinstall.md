---
title: "Reinstall?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-06-27
Okay, I've had to replace the motherboard in a computer that has Ubuntu 7.04 on it.

Now of course Ubuntu won't boot, since the hardware has changed.


Is there some way to make it work with the new hardware without a complete reinstall?  I'd like to retain the user settings, installed software, and so on.  How do I go about bringing this thing back to life without spending a bunch of extra time personalizing it all over again?

---

### Post by steve.horsley on 2007-06-27
I always thought that Linux didn't mind having the hardware changed under it, for the ;arge part. How far does it get - what error messages do you get?

---

### Post by orange2k on 2007-06-27
> **steve.horsley said:**
> I always thought that Linux didn't mind having the hardware changed under it, for the ;arge part. How far does it get - what error messages do you get?

Yes it does mind...
Once I had to plug in a ethernet-network card to get my adsl modem working (since it wouldnt work in feisty over my USB cable like it did in Dapper), but it wasnt recognised...
So I had to reinstall everything - but I didnt mind - it was a fresh install so I didnt have to worry about anything getting lost...

Still, it was a little frustrating...
It should take care of new hardware being installed...:(

---

### Post by Spektyr on 2007-06-27
What do you mean you "didn't have to worry about anything getting lost"?  Do you mean that if I reinstall Ubuntu over a previous installation it will retain all my earlier settings and installed software?

---

### Post by orange2k on 2007-06-27
> **Spektyr said:**
> What do you mean you "didn't have to worry about anything getting lost"?  Do you mean that if I reinstall Ubuntu over a previous installation it will retain all my earlier settings and installed software?

No, it was a fresh clean install, and I didn`t install anything additionally, so there was nothing to lose...
But if I had to do it today, it would probably take some time to get everything I want to work...
But not much, because I keep everything I download in my home directory, and I move it if needed to another drive, when I reinstall Ubuntu...
I dont know how complex your setup is, but hey there is always the forum to help you out...:)

---

### Post by Spektyr on 2007-06-27
My main concern is that it took a lot of work to get Samba working the way I wanted it, and my wife tinkered with pretty much every appearance setting there is... her frustration results in me having a bad day.

---

### Post by orange2k on 2007-06-27
I think your concern is justified, there is no way to get all the settings somehow picked up by a fresh install...You can try the migration tool in the Feisty install, but that will only cover your browser settings and maybe some other trivial stuff...
Setting up samba will take some time, so will the settings that your wife did...
On the other hand I would love to reinstall today if I head enough reasons - my compiz-fusion doesn`t work and I bet I would get it working if I reinstalled - but Beryl works just fine so I`ll just wait some time till I feel like it...;)

---

### Post by Outrunner on 2007-06-27
Wait a sec there! Are you sure you didn't make a separate /home partition during installation? If you did, then when you reinstall you should be able to retain all your previous settings/programs that installed in your /home partition.

---

### Post by Spektyr on 2007-06-27
I haven't reinstalled.  That's why I'm asking how to make the computer work either without a reinstall, or in spite of one.

---

### Post by Outrunner on 2007-06-27
I know you haven't reinstalled, that's why I was asking if you made a separate /home partition when you first installed. Did you? Because if you did, you might be able to retain most of your settings/programs(when/if you reinstall, that is).

---

### Post by GMachine_24 on 2007-06-27
I don't know if this would work but it did for me:

I recently had to replace the main hard drive and some memory on a computer running Edgy Eft 6.0X.

I used the Edgy install disk to install the basic Ubuntu OS and then - here is where the benefits of backing up come in - I just reinstalled everything from my latest back up file on top of the new installation and so far - it's been weeks - everything has worked perfectly. I do back up my computers every day so I had the most recent settings, documents, etc. and they all came back as if by magic.

Hope this helps.

gm

---

### Post by Spektyr on 2007-06-27
I just installed.  Used the whole drive.  I don't know what a "separate /home partition" means precisely, but I didn't do anything fancy.

---

### Post by Spektyr on 2007-06-27
> **GMachine_24 said:**
> I don't know if this would work but it did for me:

I recently had to replace the main hard drive and some memory on a computer running Edgy Eft 6.0X.

I used the Edgy install disk to install the basic Ubuntu OS and then - here is where the benefits of backing up come in - I just reinstalled everything from my latest back up file on top of the new installation and so far - it's been weeks - everything has worked perfectly. I do back up my computers every day so I had the most recent settings, documents, etc. and they all came back as if by magic.

Hope this helps.

gm

Ah, so if I were to rebuild the computer in its previous state, keep the motherboard patched together long enough to do a backup, I could return to the good hardware, reinstall, then go back to the backup?

What utility should I use for the backup process?

---

### Post by Outrunner on 2007-06-27
Well, as you probably know, the /home partition is where you keep your user/personal data(pics, documents, settings etc.). Basically it's the same thing you did for your / and swap partitions, but instead you set the mount point to /home and that way, when you reinstall, you can simply use the same setup as the previous install, except that you don't tick the "Format?" checkbox besides your /home partition(this is refering to the LiveCD graphical installer). This way you retain all your personal data and settings you previously had(so you don't have to reinstall any apps, etc.)

OK, as you can see, I'm not very good with explanations, sorry... Anyway, you said that you "just installed". What do you mean, did you reinstall, or are you referring to your current installation? I don't understand

---

### Post by Spektyr on 2007-06-27
> **Outrunner said:**
> Well, as you probably know, the /home partition is where you keep your user/personal data(pics, documents, settings etc.). Basically it's the same thing you did for your / and swap partitions, but instead you set the mount point to /home and that way, when you reinstall, you can simply use the same setup as the previous install, except that you don't tick the "Format?" checkbox besides your /home partition(this is refering to the LiveCD graphical installer). This way you retain all your personal data and settings you previously had(so you don't have to reinstall any apps, etc.)

I have no idea what you're talking about.  I used the 7.04 Live disc to install.  The only partition question it asked I answered with "use the entire drive".  To my knowledge there is one partition, it's the entire hard drive, and everything is contained within it.

I don't understand what you're trying to say.

> **Outrunner said:**
> OK, as you can see, I'm not very good with explanations, sorry... Anyway, you said that you "just installed". What do you mean, did you reinstall, or are you referring to your current installation? I don't understand

I used the word "just" in the capacity of meaning "simply" or "only".  I *merely* installed Ubuntu.  I didn't do anything fancy.  I did it simply.

---

### Post by Outrunner on 2007-06-27
OK, ok, I get it now... So you used the first partitioning option(use whole HD). So to answer my own question, you don't have a separate /home partition. I assumed you use the "Manual Partitioning" option - then you might have known what I was talking about. Well, not sure what else to suggest, sorry I couldn't be more helpful than that...

EDIT: And by the way, I just realized, thought I might clarify. You don't have a single partition, you have / (read: root) and swap (like page file in Windows, additional RAM, in a certain way)

---

### Post by jrev on 2007-06-27
It should be interesting to see whether we can backup only the /home partition and have the PC working again after the mother card interchange.
I don't believe at all that it will work any more ;)

But just now I cannot say why.

---

### Post by Outrunner on 2007-06-27
OK, I have another suggestion if you're interested. You can use this guide to make a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then you can reinstall and select MANUAL Partitioning when it asks you. Simply set the new partition's mount point to that of "/home" and don't tick the "Format?" checkbox. 

About your fstab file, you won't need to modify it as it says in the guide,since you will reinstall anyway so it will create a fresh /etc/fstab for you. Good luck, I'm off to bed now...

---

### Post by Phixion on 2007-06-27
This is where backup drives are priceless, granted you will lose the appearance settings, but important data will be safe.

Invest in either a backup internal or external.

---

### Post by GMachine_24 on 2007-06-27
> **Spektyr said:**
> Ah, so if I were to rebuild the computer in its previous state, keep the motherboard patched together long enough to do a backup, I could return to the good hardware, reinstall, then go back to the backup?

What utility should I use for the backup process?


I use the basic 'tar' utility - the complete command depends on where you're sending the back up information, which folders you want to include/exclude, etc. but you will end up with a standard *.tgz file. Mine are about 800 MB - which still amazes me.

Anyway, there are numerous articles/howtos about backing up using tar. You will end up with one file - or you should - and as long as it's not >2GB you're pretty much set - presuming you saved it to a secure location. I back up my comps every day to an external hard drive and every four or five days burn a DVD with the most recent back up files on it... in case of fire, flood, pestilence, etc. If it's >2GB you should consider splitting the file as Linux isn't certified ... ok here I get a little fuzzy on the details but it has to do with ISO certification and what not but the bottom line is don't keep files >2GB. You can split them and then recombine them if you need to restore your comp.

gm

---

### Post by Spektyr on 2007-06-27
> **Outrunner said:**
> OK, I have another suggestion if you're interested. You can use this guide to make a separate /home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then you can reinstall and select MANUAL Partitioning when it asks you. Simply set the new partition's mount point to that of "/home" and don't tick the "Format?" checkbox. 

About your fstab file, you won't need to modify it as it says in the guide,since you will reinstall anyway so it will create a fresh /etc/fstab for you. Good luck, I'm off to bed now...

Thanks, that looks like a workable solution.

> **Phixion said:**
> This is where backup drives are priceless, granted you will lose the appearance settings, but important data will be safe.

Invest in either a backup internal or external.

Yeah, this computer was slated for some pretty serious expansion, it just didn't last long enough to see any upgrades before this memory problem showed up (motherboard's memory control chip has gone batty).  The hardware order that was going to supply this machine with a massive second hard drive for backing up every other computer on the network now is going to also contain the various hardware repair items it needs as well.

The computers on the network have had the misfortune of a series of unrelated hardware failures that taken together have crippled my backup capacities and let me without a reliable machine from which to build a stable foundation.  This is a big part of the reason that this particular computer, when it failed, got slated to be rebuilt with Ubuntu rather than Winblows XP.

> **GMachine_24 said:**
> I use the basic 'tar' utility - the complete command depends on where you're sending the back up information, which folders you want to include/exclude, etc. but you will end up with a standard *.tgz file. Mine are about 800 MB - which still amazes me.

Anyway, there are numerous articles/howtos about backing up using tar. You will end up with one file - or you should - and as long as it's not >2GB you're pretty much set - presuming you saved it to a secure location. I back up my comps every day to an external hard drive and every four or five days burn a DVD with the most recent back up files on it... in case of fire, flood, pestilence, etc. If it's >2GB you should consider splitting the file as Linux isn't certified ... ok here I get a little fuzzy on the details but it has to do with ISO certification and what not but the bottom line is don't keep files >2GB. You can split them and then recombine them if you need to restore your comp.

gm

This also looks like a good workable solution.  I think I'll end up combining this with the separate /home partition idea, just for extra paranoia.

After all, this computer is going to be the basis for backing up the entire network.

---

