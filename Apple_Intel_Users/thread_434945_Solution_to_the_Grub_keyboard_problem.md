---
title: "Solution to the Grub keyboard problem"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-06
It is more like an alternative to GRUB and LILO really.. even though I still use grub

Sorry for all the threads but I guess the others will just go down as time passes.. and at least people will know what this one is about.


BACKGROUND for how I discovered this:
-------------------------------------------------------------------------------------------------------------
I thought I had messed everything up while removing grub to install LILO but I later was able to get grub back via Live CD.. however before realizing this I tried to install windows again because I thought I was doomed... I did the "recovery" thing and it messed up all my drivers to the extent that the bootcamp cd wouldnt work either.. Upset.. I just decided to reinstall windows by reformatting that partition with the installation cd...
-----------------------------------------------------------------------------------------------------------------


So by installing linux first, with grub or w/e.. and then reformatting your old windows partition... rEFIT works
It turns out rEFIT figured out everything again somehow (I had two copies of the same Linux Partition and the Windows icon pointed to grub too)... and now the Windows icon goes to windows and the Linux icon goes to grub... which I am going to set to have no timeout now..


Yes it requires you to format your windows partition after you install linux but hey.. if you dont have much in there anyways it will save you some unnecessary cold reboots  which was my main concern.. and on top of that.. the little icons all work!

This leads me to believe that rEFIT could potentially just point to windows in the first place.. maybe there is away to mess with rEFIT but I found no documentation on their website for this.


Hope some of you can resolve some of your issues with this... note that I only have done this once of course.. but I am sure it would work for others if they are using the same version of rEFIT and Linux



Of course installing LILO is probably better but if it didnt work out for you like it happen to me.. and if you really want those little icons all to correspond to the right OS.. this is the solution.

---

