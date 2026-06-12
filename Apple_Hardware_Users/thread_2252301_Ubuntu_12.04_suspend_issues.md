---
title: "Ubuntu 12.04 suspend issues"
date: 2014-11-10
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-11-10
When Ubuntu god into suspend esp when I close the lid. I get a blank screen then the color fades. Sometime I get the option to login, but when I do the touchpad freezes. Other times I need to reboot my PowerBook. I followed the instructions in this thread but it has not helped [http://ubuntuforums.org/showthread.php?t=2112830](http://ubuntuforums.org/showthread.php?t=2112830)

Anyone else run into this issue?

---

### Post by este.el.paz on 2014-11-11
> **reinhard-boris said:**
> Thx guys!

On the suspend issues, I understand there are various longer standing  bug reports on it, I haven't really looked into it yet but it's bound to  come up some time. My understanding was suspend/ sleep won't work at  the moment as it's relying on older framebuffers and the functions are  not implemented in KMS (yet or potentially ever?). 

To me personally it's not much of an issue, as shutting down and when  needed booting up is not that time consuming, so if you disable sleep  and suspend as a workaround and get used to shutting down and booting up  normally it's really not that much of a hassle and you won't run into  issues for now.

@RB:

I'm moving this answer over to this thread, even though it says "12.04" . . . wherein I didn't have problems with "suspend" . . . but, do in 14.04 . . . .  So, from what you are saying, "there is no suspend" . . . but, seems like there was not that long ago.  But, here again is the old adage, one man's food is another's poison . . . because for me having to hard boot each time I'd want to check emails or something . . . or just leave the computer running all day . . . is not something that I consider as "OK" . . . whereas, I don't listen to music or much video on the computer . . . not having sound is something I can "work around" . . . .  : - )

e.e.p.

---

### Post by rican-linux on 2014-11-11
so basically there is no suspend or sleep?

---

### Post by este.el.paz on 2014-11-11
> **rican-linux said:**
> so basically there is no suspend or sleep?

That may be the sage wisdom . . . path of least resistance and effort . . . .  But, like I said, I did have working suspend in my iBook in 12.04, so perhaps recent updates to the kernel have changed that . . . and that would render the idea of rolling back to 12.04 for suspend somewhat moot . . . .  

But BR has some skilz and doesn't seem like the kind of guy who would say something like "there is no suspend" for humorous effect . . . .  I used to think it had something to do with needing a certain amount of RAM for the system to "suspend" into . . . and perhaps that requirement has grown larger than my 640ish MB of RAM?  Sometimes there are things to do to overcome a problem . . . but sometimes the amount of time and effort required don't pan out in cost/benefit review . . . .  We'll see if anyone else stops by and offers some tips on reviving and/or entering the mystical state of "suspend."

e.e.p.

---

### Post by rican-linux on 2014-11-11
I have 2GB of RAM on my PowerBook so I cannot believe it is a RAM problem.

---

### Post by este.el.paz on 2014-11-11
> **rican-linux said:**
> I have 2GB of RAM on my PowerBook so I cannot believe it is a RAM problem.

@rican:

Hence my use of the word "I used to think" . . . so, agreed 2 GB of RAM should be plenty.  But, over on the "sound" thread I just posted that I was/am booted up in a Xubuntu 12.04 CD . . . and, even in the "live" system I was able to go into and then 20 mins later "wake from suspend" in it . . . .  So, one possiblity for you might be to try Xubuntu 12.04 and see if suspend works for you with it; as I mentioned "suspend" is one of those "mission critical" features for me . . . sound, less so.  

So this iso was from around 3/6/13 I believe, so the question is whether update/upgrades in kernels would eliminate the working "suspend" feature . . . possibly it would . . . .  There are a few less bells and whistles in 12.04 compared to 14.04 . . . a little less eye flash, but if the suspend thing languishes in "non-critical" bug report land . . . I may try an re-install of this Xubuntu 12.04 for ppc.  XFCE is "lighter" on the system, but has enough power to get the basic tasks handled . . . .  Of course there are always "issues" with any system . . . always an element of compromise . . . but might work for you?

e.e.p.

[Edit:  PS, after I posted this I think that at the time rsavage said he had "tweaked his iso so that suspend works" . . . so, today I don't know enough to understand how he did that, if he even did or said that so many months ago; but possibility is that my advice about xubuntu 12.04 having working suspend function may be . . . "bogus" . . . or "incorrect" . . . or "wrong" . . . or, remote possibility it might be "right" . . . "correct" . . . "not bogus" . . . .  

Probably the best that we can do is to try to find a similar bug on launchpad and add our tale of suspend woe there and hope that somebody listens and makes some adjustment so that suspend will be brought back for PPC users . . . .]

---

### Post by rican-linux on 2014-11-11
I am thinking about going back to Xubuntu. Suspend not working is pretty much a show stopper for me as well.

---

### Post by este.el.paz on 2014-11-12
> **rican-linux said:**
> I am thinking about going back to Xubuntu. Suspend not working is pretty much a show stopper for me as well.

@r-l:

So you had suspend in xubuntu before? Hopefully you read my caveat/edit about not sure if xubuntu as available now would offer suspend.

But, I did a google search on "suspend 14.04 ppc" . . . and interestingly the bug report I filed on it came up (forgot about it due to inactivity) . . . it might not be exactly your issue, but, if it relates to suspend you might add your issue there as well . . . so far it's just been me . . . doesn't get too high up on the radar with the devs with just one sufferer . . . . 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366624)


e.e.p.

Edit:  You can always reboot back into OSX for the "sleep" function . . . it's a bit of a pain, but sometimes linux offers some features that OSX doesn't, so even if rolling to xubuntu doesn't get you back into suspend, having the system installed might offer variety . . . .

---

### Post by rican-linux on 2014-11-12
Xubuntu had suspend working. there were other issues with that distro but all of those were fix able.  i am probable going to save some scripts I have and change back.

---

### Post by este.el.paz on 2014-11-12
> **rican-linux said:**
> Xubuntu had suspend working. there were other issues with that distro but all of those were fix able.  i am probable going to save some scripts I have and change back.

@r-l:

Well, whatever you decide, it's still 'buntu/debian at heart . . . .  If you have time check into that bug report, that's what actually gets things done . . . posting here does not work its way to the devs.

However, I'm thinking about trying to add XFCE DE to my 14.04 system and see if **maybe** that might bring suspend back.  Xubuntu 14 is no longer supporting PPC, but, in 12.04 I had XFCE & LXDE desktop environments loaded and switched back and forth through the lightdm log in window.  ****Possibly*** that might work for you, since you are in 12.04 already, it might be easier to just add "xfce4" (something like that) in the terminal, or use synaptic to install it . . . and test it out . . . .  That way you wouldn't have to "save scripts" from Ubuntu, you could log in and out of it . . . ????  

I'm going to give it a try for 14.04 Lu and see what happens with suspend . . . probably not today . . . but, couple days.

e.e.p.

---

### Post by rican-linux on 2014-11-12
I started the process. Since this is not my main laptop I have no issue with blowing it away and rebuild. In the end I can always just load debian wheezy. There are a lot of PPC blogs that all report great results with Debian.

---

### Post by irv on 2014-11-12
I have a Asus Q500A laptop and I had this same problem so I just quit using Suspend. A short time after that my laptop would shut off but would not turn back on. It took me 20 to 30 times trying before it would come back on. I ended up sending it into Asus and they replaced the motherboard. Now that I got it back everything works again. Suspend works also. When it was not working right, I would use the [fn] + [F1] keys and it would go into suspend mode. Then I would close the lid and when I would open it it would come out of suspend. But if I just closed the lid it would go into suspend and never come out. All this is working now. I thought I would just throw my two cents worth into this discussion.

---

### Post by este.el.paz on 2014-11-12
> **rican-linux said:**
> I started the process. Since this is not my main laptop I have no issue with blowing it away and rebuild. In the end I can always just load debian wheezy. There are a lot of PPC blogs that all report great results with Debian.

@r-l:

Wheezy is fine, but if you have a G5 you should have enough on the hardware side to run more than Wheezy.  You have to understand that in linux there are "purists" . . . people who are looking for the "slimmest" OS that will run . . . and mostly it's for CLI or server type stuff . . . it's all in "context" to the particular viewpoint.  If you want a nice GUI . . . then I would think something a little newer than Wheezy should be around.  Possibly you could easily run one of the 14.04 flavors . . . it's LTS . . . the base would have to be Lubuntu . . . but, right now "suspend" is a problem with it . . . .  : - )

@irv:

Thanks for stopping by, good to know you got suspend fixed . . . but, have to say that at this point Apple is likely not going to replace a G4/G5 motherboard . . . might even be difficult to find the part.  Recently a Mac repair shop told me that "there is no motherboard available for a G4 iMac" . . . circa '02 . . . .  Could someone find it on ebay? perhaps, but no guarantee of condition . . . .

e.e.p.

[Edit:  Thanks to rsavage I checked "hibernate" and that does work . . . with a little persistence; when waking from "hibernation" the screen goes back to the various options . . . reboot, suspend, hibernate, etc . . . this time hit "cancel" . . . and back in business . . . .]
[Edit2:  Upon further use of hibernate, it also seems to be intermittent . . . and/or to not work . . . essentially logging out, which then means the upper right hand button is the only option . . . and back into suspend not working and needing to reboot or shut down . . . .]

---

