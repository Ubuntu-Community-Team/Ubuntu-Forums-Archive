---
title: "How do I revert back to a fresh 7.10 install?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-14
I have completely screwed stuff over and I have worn out the patience of the helpers on this forum. Anyway I created a back-up DVD of whatever crap I wanted to keep and now I would like to reset the entire system back to its default, just installed status. Is the only way to go back to "factory" defaults a reinstall?

---

### Post by FuturePilot on 2007-12-14
Yes, as of now, a reinstall is really the only way. Just make sure you get all of your important stuff backed up first.

---

### Post by boriquajake on 2007-12-14
> **FuturePilot said:**
> Yes, as of now, a reinstall is really the only way. Just make sure you get all of your important stuff backed up first.

That blows because I don't have my disc and without thinking I used my last one to back up my personal files which on this machine amounted to 700 megs of crap I didn't really care about.

---

### Post by Henry Rayker on 2007-12-14
cds are pretty cheap...

---

### Post by boriquajake on 2007-12-14
> **Henry Rayker said:**
> cds are pretty cheap...

No, you are right, it is just that I am all about instant gratification and having to go to a store and then come back and download and then create the disk is more work than I hoped to have to do. I am way lazy.

---

### Post by CatKiller on 2007-12-14
> **boriquajake said:**
> Is the only way to go back to "factory" defaults a reinstall?

It depends what you've broken. Does a new user have the same problems you're experiencing? If not, then removing the relevant config files from your Home folder will be sufficient. If they do, then you might as well fix whatever it is you broke. Since you're resigned to re-installing anyway, the extra knowledge will be a bonus.

---

### Post by boriquajake on 2007-12-14
> **CatKiller said:**
> It depends what you've broken. Does a new user have the same problems you're experiencing? If not, then removing the relevant config files from your Home folder will be sufficient. If they do, then you might as well fix whatever it is you broke. Since you're resigned to re-installing anyway, the extra knowledge will be a bonus.

Dude, you are right, I would much prefer to fix the problem but after posting my issues two or three times with no results it appears that I have over-taxed the generous souls on this forum. (seriously, I mean that with no sarcasm, people have been really great)  It seems like at this point my best bet is to go back to square one. I know that I am not the typical Linux user in that I have no previous experience and I am totally dependent on this forum to get stuff to work. Throw in the fact that my computer is a little tough for Ubuntu (HP, ATI, you know the usual suspects) and I am getting embarassed at how much help I need. I would gladly pay some expert for support but I don' t have many options here in Puerto Rico. Whaa whaa, booo hooo. I am irritating even myself now.

---

### Post by dondad on 2007-12-14
> **boriquajake said:**
> No, you are right, it is just that I am all about instant gratification and having to go to a store and then come back and download and then create the disk is more work than I hoped to have to do. I am way lazy.


If you haven't done so, when you redo the install, use gparted to set up several partitions and make one of them your /home. That way, if you need to do any more reinstalls, you won't lose your data. (still good to back up thogh) It only took me twice having to reload all of my data to figure this out ;-)

---

### Post by CatKiller on 2007-12-14
> **boriquajake said:**
> Dude, you are right, I would much prefer to fix the problem but after posting my issues two or three times with no results it appears that I have over-taxed the generous souls on this forum. 

Most people aren't going to have read your other posts, so you won't run out of support here. The largest problems with people not getting answers are either that you've worded the question in such a way that the people that could help you don't know that they can, or that your problem is rare and fiddly enough that no one really knows the answer.

Have you managed to create a new user yet? Did they have the same problems? From a quick skim of the titles of your posts, you seem to be having some kind of graphics problem - is that correct?

---

### Post by shae on 2007-12-14
From what I can tell your problems involve Desktop Effects.  Try disabling desktop effects and see if any of them go away.  Desktop effects are still in development and ATI support is crappy at the moment.  If Desktop effects refuse to turn on, it is for good reason.  By default Compiz blacklists certain chipsets because of their problems.  You should not try to circumvent this if you do not know what you are doing.

You should try disabling desktop effects, rebooting, and seeing if any of the problems persist.  If they do then we have bigger problems, if they do not then we have found the culprit and begin considering options.

---

### Post by siciliancasanova on 2007-12-14
Start your download of Ubuntu 7.10 and gParted live.

Go to the store and grab some cd's.

Come back and burn both .iso's

Partition with gParted at least one extra one for your /home directory.  Make sure you create a swap partition also.  I do not think gParted live notifies you about swap unlike during the partitioning during an Ubuntu install, so you don't have to worry about file loss in the future.

Install Ubuntu on your / partition.

---

### Post by LostMagix on 2007-12-14
i dont know why you say your tiedof the help on the forums, this is some of the best help forums i have ever been on

but back to the topic, if it was me i would just nuke the drive and pop the install disk back in, that way you know its a 100% clean

---

### Post by boriquajake on 2007-12-15
> **LostMagix said:**
> i dont know why you say your tiedof the help on the forums, this is some of the best help forums i have ever been on

but back to the topic, if it was me i would just nuke the drive and pop the install disk back in, that way you know its a 100% clean

You are completely right, these are easily the best help forums I have ever even heard of. My problem is that I thought that I had made other people tired of me.

---

