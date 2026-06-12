---
title: "Where are the older versions of 14.n and 16.n for 32 bit PPC processors?"
date: 2018-12-24
forum: Apple Hardware Users
---

### Post by jharris1993 on 2018-12-24
Greetings!

Ref: [http://cdimage.ubuntu.com/lubuntu/releases/](http://cdimage.ubuntu.com/lubuntu/releases/) which is the list of Lbuntu releases for the various Mac flavors.

**_Issue_:**
When searching that list, it appears that the entries for versions less than the most current release version do not point to that earlier version - but instead point to a version that is not obvious (no secondary point release marking) or is the current release version - despite the title of that particular link. (*i.e.* The link for 14.4.1 - depending on which "desktop" or "alternate" link you choose - returns either a version named "14.4" or the current version "14.4.5".

**_Why this is a problem_: **
[LIST]
[*]It is entirely possible that there may be hardware compatibility issues with the most current release that can be solved by using a slightly older release - at least as an installation candidate. 
[*]The options are available on these download pages, they should be accurate. 
[*]The versions without a secondary point release do not indicate to the user exactly ***what*** release is actually being downloaded. (*i.e.* Is it 14.4.0?  14.4.1? 14.4.5?)  This is also true for the various 16.n installation CD's. 
[/LIST]

In my own case, I am trying to troubleshoot a display configuration issue on an iBook G3.  Apparently, installation via the alternate CD image doesn't configure the X display subsystem properly.  I would like to investigate the possibility that installing an earlier point release may configure it properly and then an update to the most recent version will keep the working display.  At the very least, they may provide valuable data-points to help solve the problem.

Thanks in advance for any help you can provide.

Jim "JR"

---

### Post by oldfred on 2018-12-24
I think you are into the enablement stack issue.
       [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Basically Ubuntu was releasing a version with a specific kernel version. The .1 was the same kernel but included other updates. Then the .2 thru .4 had to update to last or .5. So there should only be two versions .1 & .5, everything else was in between. Not sure then if you can find those versions or not.

---

### Post by jharris1993 on 2018-12-24
> **oldfred said:**
> I think you are into the enablement stack issue.
       <snip>
Basically Ubuntu was releasing a version with a specific kernel version. The .1 was the same kernel but included other updates. Then the .2 thru .4 had to update to last or .5. So there should only be two versions .1 & .5, everything else was in between. Not sure then if you can find those versions or not.

So, it looks like the .0/1 secondary point release is the one I need that (appears to) have the older X stack.  Do you, (does anyone else), know if the 16.4 (no secondary point indicator) is the 16.4.0/1 point release?

Jim "JR"

---

