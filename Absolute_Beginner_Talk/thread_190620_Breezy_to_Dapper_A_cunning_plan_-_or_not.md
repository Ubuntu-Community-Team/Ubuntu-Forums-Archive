---
title: "Breezy to Dapper: A cunning plan - or not?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Black Dog on 2006-06-06
I've checked out all I can on the forums but most questions / answers don't cover a scenario - here's mine:
(This is my first post - be gentle)

**Background**

In thinking career-wise I'd better find out what all the fuss about Linux is about, I stumbled across Ubuntu Breezy almost by accident earlier this year. It installed really easily (but I did it messily) and now my XP system is almost redundant. A true eye-opener, not merely the user interface but also the huge range of fabulous free applications. Now I don't have to beg my corporate masters for software - I just install it's free equivalent at home to explore the Latest Big Thing.

But this is a two-edged sword: I've loaded and removed all sorts of applications into Breezy and traces of them linger even after removal - so Breezy's no longer pure. (Strangely, I always come back to the standard apps delivered with Ubuntu. Somebody's made some good choices.) Also, Breezy's now mission critical at home - The Boss will be very unhappy if she loses her email or system time. (Perhaps Linux isn't totally free...)

I'm not truly an absolute beginner, having worked in what used to be called computing for so many years - but large corporate systems are my game, not PC's. And having experienced many system upgrades, I'm very nervous of upgrading my little Breezy system to Dapper. The only certainty is surprise, unless one mitigates risk.

So, I'm going to practise at home what I do at work - create a test system, evaluate it, and cautiously migrate to it. The first risk to eliminate is the chance of the web connection going down during an upgrade, or a hiccup in the ISO download, so I'll wait for the Shipit CD's. (A nice touch, Mr Shuttleworth. Thankyou.)

**Relevant technical landscape**
1. 386 PC 512mb memory, 2x 40Gb disk drives
2. Nvidia TNT2 graphics card
3. Windows XP
4. Ubuntu Breezy Badger
5. Disk 1 - all 40Gb allocated to XP in an NTFS partition
6. Disk 2 - essentially all 40Gb allocated to Breezy. No seperate home partition.

My plan is as follows, I'd appreciate any answers from this excellent forum to the questions at the end.

**a) Objectives**

i) What I don't want to do:
1. Put my current Breezy system in danger or have any significant downtime
2. Upgrade Breezy to Dapper and carry forward any rubbish or bad configuration that I've created
3. Spend lots of time fixing problems

ii) What I do want to do:
1. Install Dapper in a new partition, with a separate /home partition.
2. Clone the Breezy /home to the new Dapper /home
3. Keep XP to cover what for me are Linux's deficiencies - slide scanning and Tiger Woods Golf (in my view the only essential game).
4. Later, remove Breezy and create another Dapper system in its place for testing future upgrades & evaluating new applications

**b) Plan**
1. Resize XP to 22Gb (currently occupies 18 Mb - flabby, no?)
2. Create a new partition in disk 1 for Dapper
3. Create another partition in disk 1 for Dapper /home
4. Copy Breezy /home to Dapper /home (as described in [www.psychocats.net/ubuntu/separatehome/html](www.psychocats.net/ubuntu/separatehome/html))
5. Install Dapper as a new system
6. Edit Grub to ensure Breezy's still the default (so no choices need to be made by my user)
7. Test & set up Dapper, if OK:
8. Re-copy Breezy /home to Dapper /home (as Breezy's /home will have changed since the first copy)
9. Edit Grub to ensure Dapper's the default
10. Delete Breezy
11. Resize and relocate partitions (easily said !)
12. Install another instance of Dapper as a test system
13. Edit Grub to ensure Dapper 1 is the default

Therefore, the only productive downtime is steps 8 & 9.

**c) Questions**
1. Is the above plan viable? Are there any dumb errors or omissions? (Please don't advise me to upgrade Breezy, it's not going to happen)
2. What is a 'good' size for the Dapper partition, excluding /home - in Gb please, not a generic statement? (I'm aware that /home should be as big as one's needs)
3. I've read some traffic about GParted misbehaving - is it safe to use it for all the resizing and partition work?
4. Assuming that I don't add anything worth keeping to the new Dapper /home, are there any issues with re-copying /home once Dappers installed? Would any new Dapper files or configuration, and so on, get overwritten?
5. Where is Grub located after Dapper is installed? Is it still in the Breezy partition? If so, how do I move it to the Dapper partion? Or better still, somewhere system independent?
6. Forum traffic indicates that Nvidia drivers seem problematic for future upgrades - is there any need to install Nvidia legacy drivers when games are not an issue? (Wine's too obscure for me, XP will limp on)
7. How do I delete my first Ubuntu install, Breezy? Simply re-format the partitions? 
8. Are there any consequences in deleting a first Ubuntu install - e.g. I've read that this stops Grub from working. If so, what do I need to take care of?

Due to other commitments I can't visit this forum frequently, so please don't be offended if you don't get an immediate response, should you be kind enough to post anything. The World Cup's going to take out a lot of time too!

Thanks and regards,
David

---

### Post by Kimm on 2006-06-06
I cant help you with all of this, but I'll try to give you a hand.

You plan sounds fairly good, although very carefull.
Copying your home folder is entirely possible, this would also ensure that anything you configured remains the same.
This means however that anything Dapper places in your home directory by default will be deleted (no system critical configuration files are there however)

I believe about 2 Gb would be enough to get a pretty small System running, I belive the standard install takes about 300 Mb, add some additinal software and 2 Gb would probably last a while.

Unless you downloaded and installed the Nvidia drivers from the Nvidia website manually, you shouldnt have any problems with them.
The standard Ubuntu install uses the "nv" driver. This is an Open Source driver that support Nvidia cards (but not 3D) and will be upgraded along with the system.
You may also have installed the nvidia-glx package, this is the standard proprietary driver from NVIDIA and it will also be upgraded along with the system.

---

### Post by uteck on 2006-06-06
1. Your steps a very cautious and should work fine.
2. going with only 3 partitions; for the / partition I would recommend be about 10GB that way you leave room to grow, but no less then 5GB otherwise you may have space problems in the future.  2GB should be fine for testing.  /swap is recommended to be twice the size of your RAM, then the rest is for /home.
3. I have not had any problems with parted for the half dozen times I have used it.  Even the expensive pay for partition tools give warnings about data loss.
4. Copying things should work fine.  I reused the /home partition many times with many different installations and had no problem until the drive started acting up.  I think I went from Mandrake to RedHat to Debian with the same /home partition.
5. By default I think Grub is installed in the boot sector of the first primary disk (hda) unless you specified a different location.  You can tell Dapper not to install grub, then boot into Breezy and modify your grub menu to include Dapper.
6. By default the generic nv driver will be installed which should work fine for most things.
7. Yes, you can just reformat it.
8. Grub is most likely on hda, but since you will be leaving XP there and not formating the whole disk, it should still work.

---

### Post by jdong on 2006-06-06
Very conservative approach, and what you mentioned will work well. Do upgrade that XP partition before resizing, as that is always a shaky process in my mind (never failed on me the 10 times I've done it, but don't depend on that being true!)


I might make the futile recommendation to just upgrade Breezy to Dapper, or back up the Breezy partition and then attempt the upgrade. I have done too many dist-upgrades for my sanity, even on somewhat customized (custom package) setups, and never ran into a snag.

---

### Post by Black Dog on 2006-06-13
Thanks to all responders.
David

---

### Post by The Cosmic Hobo on 2006-06-13
Well... this is a very, very thorough plan - and it has a lot more steps (and details) than the four pages of scribbled notes I've got scattered on my desk. Reading all that makes me wonder if I need to take a step back and redo it all again - I've literally just signed up to find out if there are any known technical issues with Ubuntu live CDs on the laptop model I'm using, with a view to a transition from XP fairly shortly, and eventually building my own desktop specifically as an Ubuntu system.
Hope it goes well - I'm just glad there's such a good, knowledgeable, friendly community here, because I'm about to take my first proper steps with Linux, and after a couple of disasters in the past (mostly due to taking the half-arsed approach), this kind of conservative thinking is just what I need.

Sorry I can't offer any help, but your post has made me think about making a better plan for what I'm doing - have a karma point! (Or a jelly baby...) ;)

---

### Post by Black Dog on 2006-06-19
Thankyou, Cosmic Hobo.
For those who may be interested, here's what happened when I executed this plan, as I got tired of thinking and planning and waiting for the CD's. So I downloaded the ISO image and successfully copied it to CD (the first time ever that has worked for me!), and just got on with it:

1. Loaded XP and removed the reference to the NTFS partition in disk 2
2. Loaded Breezy and removed the reference to the same NTFS partition in disk 2
3. Using the CD as a Live CD, booted Dapper and executed gParted. 
4. Squeezed XP down to 20 meg (previously defragged)
5. Created a new 20 meg ext3 partition in disk 1. 
6. Copied Breezy /home across to this.
7. Resized the  FAT32 partition (used for XP & Ubuntu data exchange) in disk 2
8. Reloaded XP & Breezy to ensure all was well, and it was, with one scary moment: XP executed a disk check on its own partition & the resized FAT32 partition
9. Reloaded Dapper Live CD and re-execute Gparted
10. Created a 10 meg ext3 partion in disk 2 for Dapper
11. Paused for a tea break to steady the nerves and catch up with the World Cup
12. Installed Dapper into the new partition in disk 2, being careful to mount the correct partitions (new /home, old /swap, old data sharing)
13. Loaded the new Dapper and checked it out

**Bad outcomes**
1. Copying the /home partition has done something strange to the permissions in the new /home: my kids can no longer logon - an error occurs with 'no permissions for /home' (or similar). Fortunately, my wife's logon still works - I suppose because I'd altered the permissions in Breezy so I could read her data. For those who created the (mostly excellent) instructions for moving /home - were these instructions specific to a single user system? I'll raise this issue as a seperate question in the forum.

2. Redundant /home data needed to be manually deleted for those applications I'm not going to reinstall: Opera cache, Galeon cache etc. These applications had previously been removed in Breezy. So, when one completely removes an application via Synaptic, it does not completely remove it. Synaptic could be improved to optionally remove such data.

3. Evolution complained 'Sumnmary and folder mismatch, even after sync'. Googling this error revealed that manually deleting Evolution's Inbox.ev-summary, Inbox.ibex.index and Inbox.ibex.index.data solves the problem. They're all rebuilt when Evolution is re-executed (also needs to be repeated for all other Evolution folders).

4. Grub was re-installed into the MBR and into the /root of the new Dapper as part of the install process. No choices were offered - it just did it. Fortunately it recognised XP, Dapper & Breezy and set them up as boot choices. I just have to edit the new menu.lst to re-instate my pretty Grub colours. I'll have to do this again when installing a testing version of Dapper. This also means that should any new install be subsequently deleted, Grub will not be able to find stage 2, and the system will be inoperable. Not good - Grub should be system independent.

**Good outcomes**
1. Printer set up was very easy - I've got an HP 1205 PSC and this time I don't think I need the complexity of installing the HP toolbox etc.

2. All user settings (application configuration, desktop wallpaper, themes etc) came across unscathed.

3. Apart from the bad outcomes, everything works, so much so that I've left Dapper as the default system. I asked my wife and daughter if they liked the new system, and they both said 'what new system?' Victory! (so far...)

All-in-all, I'm very pleased.

Cheers,
David

PS have a clear plan for the partitions before installing any system - it's a real time-consuming pain to change them afterwards.

PPS can't wait for the howls of pain when the old world upgrades to Vista.... How many PC's will not be big enough to run it? How many hardware devices will be rendered obsolete as no Vista drivers will be built for them? Etc.

---

### Post by Black Dog on 2006-06-19
Oops. Read gig for meg in my previous post. A thousand apologies - or should that be 1024 apologies? (Help, I'm turning into a geek).

---

