---
title: "Bug = updates??"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-12-08
It appears to me to be the case. Last night I did a clean reinstall of Feisty, There were ~174  updates waiting, which I tried to run. Immediately an error message ppped up:

An Error Occured
the following details are provided:

E:dpkg was interrupted. You must manually run 'dpkg --configure -a' to correct the problem.
E: _cache ->open() failed. please report

That the error message popped up came as no surprise only because I was aware that it might have been a symptom of WHY I found it necessary to do a clean reinstall.

Note the message concludes with, "please report".

To whom, where and how?

Will this post serve the purpose?


EDIT: I should have added that among other symptoms that emerged, when I went to Synaptic, it opened with the very same error message overlaying it. When I closed the error window, so too did the Synaptic window close - so it seems I now have to limp along without it for the time being.

---

### Post by nikoPSK on 2007-12-08
run this:

```
dpkg --configure -a
```

---

### Post by mali2297 on 2007-12-08
Make it
```

**sudo** dpkg --configure -a

```

---

### Post by jimmj43 on 2007-12-08
Since I composed this thread's lead-off post I have D/L'd, burned to disk & installed Gutsy, so I HOPE I won't have to revisit the issue. That said, with this shiney new install, there ARE updates waiting to be installed. Decisions, decisions.... Do I wanna risk a few more hours evaporating outta my life?

---

### Post by jimmj43 on 2007-12-08
I should have known... :(

Shame on me. I tried to install the updates.

Tsk, tsk, tsk....


Another error message and another totally-crippled install crashed and burned.

This was the error message:

An Error Occured

The following details are provided:

E:/Var/cache/apt/archives/openoffice.org-java-common_1%3a2.0-1ubuntu 5.3_all.deb: unable to fsync updated status of 
'openoffice.org-java-common'

I opened the "review" window with the intention of C/Ping the contents to a text editor. Fail. The text editor refused to open. And the window that had been managing the udgrade list froze. I had to do a hard shutdown - which is why I'm now running on the live CD.

I have a few questions, none of which require immediate answers (for me). I'm rapidly reaching the point of no return and walking away from Linux. I've been running Feisty since its stable release (April?) and tried several distros in the interim, including DSL, TinyMe, Puppy,MINT,  Sabayon and now Gutsy. I'm seeing fewer and fewer differences between Linux and the dreaded Windows - both have their quirks (read: weaknesses) In my experience, every single Linux distro I tried sent me scurrying for help to get video (for instance) to work. In wading through the posts here I find the variety of "fixes" dizzying. Printers, {Can you say, "Lexmark"?) while not the open source community's fault in the least, still remains as a significant downside to the little guy noob with a skinny wallet. 

1. All those upgrades. Why so many, and, why with no manner of, say, color-coded priority flags? As a noob scans down a list of 100+ upgrades, his eyes will cross if he attempts due diligence to uncheck those he tries to identify as 'not needed'. Why bloat his machine with 'stuff' he's unlikely to have any use for? In the several months I ran Feisty I noticed a significant slowdown in performance as time and updates marched on. After a clean reinstall, sans ANY upgrades, it returned to its zippy self.

2. It isn't my intention to ruffle feathers here, but I wonder how thouroughly the updates are screened. My own experience recently, as well as a reading of the boards here strongly suggests a trend - tracable to upgrades, that have resulted in CREATING problems rather than solving. It's pretty exasperating and does nothing to improve the Linux image.

3. What might be the chances of asking that a common, simple-to-understand-by-noobs language and terminology be more vigourously encouraged on the Beginner's Board? For instance, if I see a poster offer a fix in the form of:

"cd sudo aptget,,yada, yada.."

What does "cd" mean? <-- If I don't know that, all the rest becomes meangless. I can ASSUME, but we all know where that leads.

On the other hand:

"Applications > Accessories > Terminal > *whatever command* "

Sorry for digressing ito too much trivial detail. I guess I'm just in a 'mood' to vent some...

Thanks for letting me bend your ear.

---

### Post by zvacet on 2007-12-09
**Upgrades**

Most of upgrades are security nature and you want to have them.others are upgrades of apps you allready have,meaning they are improved in some way and it is good to download and install them too.When update manager show you list of updates they ate divaded in sections so you can choose wich one you want or not.From my expirience best way is to download them all,because they are here for some reason.

**Commands**

If someone give you answer to your question and that answer involved some commands go to the terminal (applications>accessories>terminal) and just copy/paste that command and hit enter.For understending CLI read [this](http://linuxcommand.org/).It is good start.Good luck and I hope you will stay with Ubuntu.

---

