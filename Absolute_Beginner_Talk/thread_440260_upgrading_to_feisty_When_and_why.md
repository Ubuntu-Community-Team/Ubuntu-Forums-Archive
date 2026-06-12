---
title: "upgrading to feisty? When and why?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-05-11
so I have been using dpper drake since Christmas.

Jut had a major problem with it.. some corrupted file, caused havoc..

the sys op at work who helped rectify says I should just update to Feisty Fawn since it is better..

so, is it? and what is in volvled in the upgrade? what risk do I run of loosing stuff?

Yes, I wil lback up the important data before the upgrade... but what will it do to my opera? and to my firefox for instance..?

Sorry to ask but I am jsut a noob getting more intersted in this whole linux thingy.

robi

---

### Post by Cypher on 2007-05-11
All of your personal settings should be untouched by the upgrade to Feisty. Howeve, since there is Edgy Eft (6.10) in between you and Feisty, not sure how many things might break if you jump directly.

I did an upgrade of Edgy Eft to Feisty Fawn without any issues, I think others have done Dapper to Feisty will minimal errors.

So save everything you care about and give it a shot..

---

### Post by hyper_ch on 2007-05-11
do you have /home on a seperate partition? If so, then I would re-install the system from ground.... if not, then I would make a backup of /home, and re-setup the whole system (and also making a /home partition this time) :)

---

### Post by beanco on 2007-05-11
no partition... at least i think not...

how to check it?

and how to make one?



robi

---

### Post by ramjet_1953 on 2007-05-12
Are you happy with Dapper?

Are you using the system for your liveliehood?

Are there any features in Feisty that you want / need?

If things are going fine for you in Dapper, you know what they say about fixing something that isn't broken?

Also if you have a look at these forums, there are some issues still outstanding with Feisty.

[LIST][*]Scanners[*]VCD support (System Hard Locks when you insert a VCD)[*]There seems to be a problem emerging with HP printer installs (Could be that python-qt3 is not installed by default)[*]Many people are getting random hard locks[/LIST]

There may be more, but enough for me to only have Feisty on a seperate HDD, well away from my Edgy install, which has been stable for me. I know others have had problems with Edgy, though.

For me, I'll stick with Edgy for my primary OS, until the next LTS version is released.

Regards,
Roger. :cool:

---

### Post by beanco on 2007-05-12
I currently only have one hard drive.

Dapper is on that.

I need a computer for work .... that is one rason I will not upgrade in the next few days... i mean I have to a job or two done, cannot afford computer problems...


roib

---

### Post by alienexplorers on 2007-05-12
I can't see upgrading to feisty Fawn if everything is working fine. I use my computer to do jobs for others and Dapper suits my needs perfectly.  I figure as ramjet_1953said if it is not broken don't fix it.  Unless you want all the new bells in whistles then go for the upgrade.  Just remember to back up everything important.  You never know if some small thing could make you loose everything.

---

### Post by beanco on 2007-05-12
well, i am not sure what new bells and whistles there are.. i will have tolook into.

i agree in principle that  *if it ain't broken, don't fix it*

but I have had small issues with dapper.

I cannot get my printer installed...I have tried everything on it I can find on these forums..

I have problems with opera,, mainly flash related... 

I would think of switching to firefox but i want a save sessions option, like in opera...

Epiphany died a while ago and I cannot get it back up... but this is probably not related to dapper, rather to my silly skills, or lack there of... and to be honest I have not tried much...


robi

---

### Post by ramjet_1953 on 2007-05-13
For me everything except my webcam works fine in Edgy.

My Logitech QuickCam for Notebooks Pro refuses to co-operate. Funnily enough, it works fine in Dapper and Feisty. 

However, it is not really essential for me and as I said in my previous post, I'll stick with the stability that Edgy gives me until the next LTS release.

Of course, others who have different hardware may have issues.

 

Regards,
Roger 8)

---

### Post by beanco on 2007-05-13
so maybe I should start upgrading by goingto edgy for a bit, and when the next fiesty is out go there???

robi

---

### Post by lakersforce on 2007-05-13
Like mentioned above, it would be a great idea to set up a seperate /home partition. I have it set up this way:

/dev/hda1 ntfs 60gb windows
/dev/hda2 ext3 5gb / (root)
/dev/hda3 ext3 250gb /home
/dev/hda4 swap 1gb


That way I can install and reinstall all versions of Ubuntu (and other linux distros for that matter) over and ver again without ever loosing my personal data, as long as I remember to set everything up correctly under install.

Dont be afraid to play around with setting your partitions up under install. Under Ubuntu, nothing is actually writen to the disk before you give the very final go-ahead.

---

### Post by wpshooter on 2007-05-13
> **beanco said:**
> so maybe I should start upgrading by goingto edgy for a bit, and when the next fiesty is out go there???

robi

beanco:

I just moved one of my machines from Dapper to Edgy and all seems pretty good/stable.

However, before that I attempted to move that same machine directly to Feisty and I also attempt to moved that machine to Feisty by installing Edgy and then upgrading to Feisty and each time when I got to Feisty I had PROBLEMS.

IMO, Feisty is NOT ready for prime time.

I can not really see them starting on another project when the previous one (Feisty) is so far from finished !!!

My advice is to stay with Dapper or possible move to Edgy.

Good luck.

---

### Post by beanco on 2007-05-13
lakersforce.

when i first started to play with ubuntu i ws trying to install it, per instructions on the site, partitioning and stuff... I wanted XP on one partition and Ubuntu on the other.

I could not get it to work!!!

I eneded up just killing XP and then I got ubuntu running...

so it seems I am not good at partitioning. I will look into it.

wpshooter,

ok seems like dapper to edgy is the way to go... then whenthere is a version of feisty  running well, go there.

robi

---

### Post by beanco on 2007-06-05
OK I want to try feisty.

But how to make partitions?

I want this old dapper on one partition and feisty on the othe so they do not interfere with eachother.

Once I am sufficiently happy with Feisty I will get rid of dapper.

so how do I do this?

robi

---

### Post by beanco on 2007-09-08
it's been a while shince I last posted in this thread,

I am still on Dapper and having more and more problems.

I either have to reinstall it or try feisty....

I still do not know how to make partitions...

somebody point me in the right direction for that.

My son needs a good movie/video editor for school work. my daughters needs a stable envorinment for school projects, mostly word processing..

my wife and I need stable word processing and spread sheet stuff...

I would gladly keep dapper on one parition and feisty on a different one, playing roudn with it... and with reinstalls, etc. is a great way to learn but I need to figure out how to make partitions first....

robi

---

