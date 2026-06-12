---
title: "Open Office Base, Sun Report Builder, not possible to save margins settings"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by SorKar on 2007-12-27
Ubuntu 7.10, Open Office 2.3.0 database (Sun-Report-Builder_0.oxt version 1.0.1 downloaded from Synaptic Package Manager). 

The system is totally new, clean Ubuntu (no MS Windows etc), **64 bit** Intel (E6750 Core 2 Duo).

It seems impossible to save the margins in Format / Page. Default value is 2 cm in Left, Right, Top and Bottom boxes. It is possible to change values but new values do not save and have no impact on the page margins in the report.

I have also created reports in Win XP (open office 2.3.1). No problem opening/editing tables/queries etc but the report builder is the problem when copied to Ubuntu.

- Any clue where to start checking?

**Dec 28, 2007 More info added**

After some more testing it seems that the problem is relevant only to the **Left and Right check boxes**. It is possible to change and save new values for the **Top and Bottom check boxes** by selecting first the Bottom box and then the Top box + OK. Picture **Page Setup-2** added.

- **Can somebody please verify this problem** (should I make a bug report)?

**Dec 29, 2007 ... more info added**

After some more testing on 32bit system Ubuntu 7.10 + Windows XP system the conclusion is that the "Margin problem" is related to 64bit systems.

Bug report created:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/179220](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/179220)

---

