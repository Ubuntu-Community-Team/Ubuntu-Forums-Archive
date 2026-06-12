---
title: "[SOLVED] Upgrading to Gutsy"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Mike54 on 2007-10-12
I've looked around for similar threads, but I want to make sure I have my head wrapped all the way around this upcoming upgrade.  And since the only stupid question is the one not asked...

Yes, I'm green as a gourd with only 3-4 weeks of Ubuntu experience, but after a couple weeks of playing around with an Ubuntu Live CD, I wiped the 'other' operating system off and did a full Feisty install.  I set up my 120 gig drive in the following manner -

10 gig - /dev/sda1  ext 3  mount point  /
1 gig - /dev/sda2  swap
everything else - /dev/sda3 ext 3 mount point /home

OK, if I want to do a network upgrade to Gutsy, after the official release, I open the Update Manager and click Upgrade, which should walk me through the upgrade procedure.

My question (yes, I finally got to it) is this - are the images and documents that have been saved to the /home folders safe during the upgrade procedure, or will they be over-written?  My understanding is the upgrade will only over-write the / partition, yes?

I think /home will be safe and sound throughout the upgrade procedure, but I am just wanting to make sure that is correct.

If I were to upgrade via the alternate CD method, would the /home partition still be untouched?

I also want to say thanks for all the help this community has provided me.

---

### Post by OldTimeTech on 2007-10-12
As you say your home partition should be safe and sound during either upgrade.  But as I've been told each and every time I've done an upgrade, it's always much safer to backup your home directory on a flash drive, another hard disk, a cd-r.  Because even though we may say your safe....something unusual could happen and then you would have the complaint that we lead you astray and we wouldn't want that to happen.

After saying all of that.  I will also tell you that if you save your home folder, you could just as easily to a total new install.  And more of the knowledgable on these forums say every time you upgrade you should actually do a new install, that way if some program or update has gotten screwed during the time you've used Ubuntu, it won't affect the new install.

Enjoy Gutsy, I know I'm going to and yes, I'm doing a totally new install and then copy my home folder over to the new one.

---

### Post by Malta paul on 2007-10-12
Hi,
I would back up your /home directory before upgrading. You can use APTonCD, down load using Applications>system tools>APTonCD.
There is a rather good Sreencast video "Installing Ubuntu part1" that you may be of interested to you.
[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
Hope this is of help :wink:

---

### Post by Hospadar on 2007-10-12
The likelyhood of actually loosing data on the home partition is very tiny, but what is more likely is that the upgrade might cause some other system problems (like let's say your gui gets misconfigured) and you can't easily get at the stuff on your home directory.  for this reason I would really suggest backing your stuff up.

---

### Post by rookshop on 2007-10-12
If I backup my applications with APTonCD,  will all of them works after the upgrade or will they have compatability issues? Should I just download all the packages again??

---

### Post by dptxp on 2007-10-12
> **OldTimeTech said:**
> And more of the knowledgable on these forums say every time you upgrade you should actually do a new install, that way if some program or update has gotten screwed during the time you've used Ubuntu, it won't affect the new install.

Enjoy Gutsy, I know I'm going to and yes, I'm doing a totally new install and then copy my home folder over to the new one.

> **rookshop said:**
> If I backup my applications with APTonCD,  will all of them works after the upgrade or will they have compatibility issues? Should I just download all the packages again??

It is always advisable to have everything fresh when you upgrade.

This is the reason why the more serious users go for the LTS versions.

---

### Post by OldTimeTech on 2007-10-12
Only thing I would back up is the home directory/folder.

But I would have a list of all the applications you have loaded since install on the package you are running.  Because many times with a new upgrade/new package, will have better or newer versions of the packages you have.

I have to say, I've never used APTonCD so don't know if it will give compatability issues.

---

