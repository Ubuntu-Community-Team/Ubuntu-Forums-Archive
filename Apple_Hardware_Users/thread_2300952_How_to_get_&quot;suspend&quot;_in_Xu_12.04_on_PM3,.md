---
title: "How to get &quot;suspend&quot; in Xu 12.04 on PM3,1 w/radeon card??"
date: 2015-10-29
forum: Apple Hardware Users
---

### Post by este.el.paz on 2015-10-29
[https://lists.ozlabs.org/pipermail/linuxppc-dev/2012-April/097669.html](https://lists.ozlabs.org/pipermail/linuxppc-dev/2012-April/097669.html)

PPC denizens:

I read through this link and numbers of others from the FAQ looking for data on getting "suspend" to work in a 12.04 install on a Powermac3,1 Sawtooth that has the radeon ati 128 rage video card.  From the FAQ it looks like "suspend" is possible with the radeon card, but the precise instructions for how to get that going are not **obvious*** . . . .  This link shows a rambling thread among some of the devs entitled "PowerPC radeon KMS -- is it possible?"  and basically arrives at no conclusion on the topic, it's just a brainiac shop-talk chat session . . . .

I tried looking at a number of things, I now have a little better idea of what "KMS" stands for, but not the relevance of it for getting "suspend" to work.  I tried "sudo pm-hibernate" and that did shut the computer down, but revival was via power button and that brought a "frozen" GUI, had to drop into TTY and reboot the system to get the cursor working.  I searched synaptic with "powerprefs" and "radeondrmfb" and that brought nothing.  I ran "fbset" and it said, "not installed" . . . .

So, as far as the general utility of 12.04 on this machine, it is fine . . . and the **only** thing that keeps it from being frontline is the lack of OSX-like "sleep" feature.  I think I went through a bunch of stuff on my now defunct iMac w/Nvidia card and found that wasn't going to be working; but, now I'm running this PM ST as the main squeeze, it's got the radeon card, but, "lsmod" doesn't show "radeon" module, as I believe I would see, perhaps in my iBook???  

Is there a simple set of quality, yet basic instructions on how to get "suspend" set up somewhere in the Ubuntu archive/wikis???

Many thanks,

e.e.p.

---

### Post by rsavage on 2015-11-01
You don't have a radon card...

---

### Post by este.el.paz on 2015-11-01
> **este.el.paz said:**
> [https://lists.ozlabs.org/pipermail/linuxppc-dev/2012-April/097669.html](https://lists.ozlabs.org/pipermail/linuxppc-dev/2012-April/097669.html)

PPC denizens:

I read through this link and numbers of others from the FAQ looking for data on getting "suspend" to work in a 12.04 install on a Powermac3,1 Sawtooth that has the radeon ati 128 rage video card.  From the FAQ it looks like "suspend" is possible with the radeon card, but the precise instructions for how to get that going are not **obvious*** . . . .
Is there a simple set of quality, yet basic instructions on how to get "suspend" set up somewhere in the Ubuntu archive/wikis???

Many thanks,

e.e.p.

> **rsavage said:**
> You don't have a radon card...

@rsavage:

Thanks for stopping by, I ***always*** appreciate your very dry and concise sense of humor . . . .  BTW, right now I'm booted up in live session of your 12.04 spin of Xu 12.04 on my iBook . . . very nice system--and as you had originally said, "suspend works" . . . .  I put it into "suspend" last night and this AM opened the clamshell . . . and up she spun, so I am thinking about retro-installing it, and adding Tori OS as the DE and see if it runs more quietly than 14.04, which seems to run the fan hard all the time . . . .

OK, back to the OPs thread, question is about Powermac Sawtooth, which does have the radeon card, but, which so far has not provided "suspend" . . . or, the prevalent directions don't seem clear as to how to achieve . . . .  Or, are you saying that "ati Rage" is not radeon???  I think it is . . . .

e.e.p.

PS:  I PM'd you over on U MATE forum, didja get that inquiry there?

---

### Post by rsavage on 2015-11-01
> **este.el.paz said:**
>  Or, are you saying that "ati Rage" is not radeon???  
Correct

> 

PS:  I PM'd you over on U MATE forum, didja get that inquiry there?
Don't have a U mate account..... so no.  U mate is nothing to do with me.

---

### Post by este.el.paz on 2015-11-01
> **rsavage said:**
> Correct


Don't have a U mate account..... so no.  U mate is nothing to do with me.

Ah, strange, "drm" is listed as one of the modules in "lsmod" . . . I'm not booted in that machine right now so I can't check it . . . but seems like I saw somewhere that is radeon . . . but, anyway . . . so close, yet so far with that machine . . . more or less almost gets me around on the net, but, easily overwhelmed . . . .

OK, on the U MATE, thought I'd seen some posts from you here about MATE DE . . . I tried to PM you here but it was "blocked" . . . I was asking if you could lend your skills with PPC iso spin to the ToriOS team . . . Israel could use a little direction on the how-to of that, as he is an x86 guy . . . .  It is a nice DE that does get the ST around on heavy sites . . . since I'm running yr 12.04 spin I know you know . . . I'm typing in "xbuntu" right now . . . .  : - )

---

### Post by rsavage on 2015-11-02
I don't understand why you are using a computer that belongs in the tip (recycling centre).  Particularly when you have a more modern ibook, and a MacBook I think.  How many computers do you need?  It's madness to purchase old Powerpc hardware unless it is a cube, or an imac g5, or something that looks good when you don't use it (because why would you use a computer that old?)

---

### Post by este.el.paz on 2015-11-02
@rsavage:

"madness" . . . is a phrase that has special appeal to me . . . but, it's all about "games" . . . why is anyone still using PPC computers???  Because they are there, and they still run just fine.  This one I "inherited" from the better half when my iMac died . . . the second time . . . .  So, I didn't "buy it" . . . but, did buy the parts to get it up to spec . . . now, with 2 GB RAM it is "faster" than my iBook . . . .  It is the "home" unit, so I don't have to get the MBPro out each and every time . . . and with Tori running in it, it does "OK" . . . but, 450 MHz is easily overwhelmed . . . .  But, just for your edification, following your instructions on the FAQ awhile back I found: ```
I ran some Grep command I found there in the FAQ and               got:
              
              "$ grep RADEON /boot/config-$(uname -r)
              CONFIG_DRM_RADEON=m
              CONFIG_DRM_RADEON_KMS=y
              CONFIG_FB_RADEON=y
              CONFIG_FB_RADEON_I2C=y
              CONFIG_FB_RADEON_BACKLIGHT=y
              # CONFIG_FB_RADEON_DEBUG is not set"
              
            
             The line config_drm_radeon kms=y  is supposed to mean             something, but not sure where to go with that.
```

e.e.p.

---

### Post by rsavage on 2015-11-02
I'm sorry I can't help you.

---

### Post by este.el.paz on 2015-11-02
> **rsavage said:**
> I'm sorry I can't help you.

Thanks . . . you have made that clear . . . .  I was just hoping for some comment on the grep items that showed up with "radeon" in them???  As per the FAQ items . . . it seems like it indicates that "suspend" could be possible?

e.e.p.

---

### Post by rsavage on 2015-11-02
Have you ever considered that Linux is not for you?

---

### Post by este.el.paz on 2015-11-02
> **rsavage said:**
> Have you ever considered that Linux is not for you?

Homes, not really your finest hour . . . but, yes, often . . . as I don't have the kind of time it would take to learn everything needed to hand build my own linux system.  But in spite of that I have dual/triple boot systems running on three computers . . . more or less "OK" . . . some of it with help from others such as your self when you are in a good mood . . . much of it on my own . . . .  A "forum" is for getting some direction or help . . . this kind of post reminds me of 5 years back on the hard core linux user forum . . . ubuntu forum is generally more "generous" with assistance.  But, at least you replied . . . which I do appreciate.

e.e.p.

---

### Post by rsavage on 2015-11-03
Look I don't wish to be rude or upset you, but I've already told you twice now that the rage 128 card is not a radeon card.  You can run as many commands as you like until the cows come home, but you are never going to alter this fact.  I can't help you, because you never ever listen to or act on the reply you get.  It would be a waste of my time to do so, and yes it would put me in a bad mood.  The rage 128 has a section of its own in the FAQ, have you actually looked at that?  Yes it doesn't say anything about suspend, but it'll help you with what you need to google (but I've no idea if suspend is possible, particularly on a desktop machine).  You've been on this forum for what - 4 or 5 years? - yet you don't seem to have progressed at all in any understanding of linux.  Which is fine, people have different strengths and weaknesses, but I just think you'd be happier and more productive if you dropped Linux or concentrated on using it on a modern non-powerpc machine.  Instead of being mardy about the replies you get, perhaps you should take them for the well meaning helpful answers in which they were intended.

---

### Post by howefield on 2015-11-03
Doesn't appear to going anywhere productive, thread closed.

---

