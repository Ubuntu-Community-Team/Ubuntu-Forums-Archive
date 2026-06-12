---
title: "Gutsy Gibbon (7.10) stalls while reading cache"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by RichardIII on 2007-10-20
Hi to the community,

I attempted to upgrade my 7.04 installation to 7.10 from within 7.04, but it stalled when "Reading cache"; I now have this situation that I can't do any software updates since "A previous upgrade has not fully completed".

A retry of the upgrade results in the upgrade staying completely blank, any suggestions to roll back?

Thanks in advance, Richard

---

### Post by PartisanEntity on 2007-10-20
My upgrade process also seems to freeze at 'reading cache'. I tried letting it run all night, nothing changed.

I downloaded the alternate CD, tried upgrading from it, but it froze at 'checking package manager'.

---

### Post by RichardIII on 2007-10-20
> **PartisanEntity said:**
> My upgrade process also seems to freeze at 'reading cache'. I tried letting it run all night, nothing changed.

I downloaded the alternate CD, tried upgrading from it, but it froze at 'checking package manager'.

Thanks for the quick response, PartisanEntity; at least I didn't do anything wrong :).

Do you have any suggestions to roll back (I am now stuck in "Software Update" with 703 updates I can't run, and I would like to go back (roll back / downgrade) to the normal 7.04 Feisty Fawn until this problem is solved...

Richard

---

### Post by PartisanEntity on 2007-10-20
Technically you and I have not upgraded to 7.10 yet as nothing was installed. You can open a terminal and enter: sudo gedit /etc/apt/sources.list and change all instances of gutsy to feisty. Save and close then restart.

---

### Post by RichardIII on 2007-10-20
Done! It now seems that I am back to normal again. Thanks a bunch, or in your language: Vielen Herzlichen Dank! :)

Now that this is done: Is it a good thing to report this somewhere? Next question of course being: Where (Yes, I need to learn a lot about the way things are done in Linux/Ubuntu...)

---

### Post by PartisanEntity on 2007-10-20
Gern geschehen :)

Yes, please do report it [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153984"), it seems others are having this problem.

---

### Post by RichardIII on 2007-10-20
Done, thanks for showing thew way! ;)

Have a fine weekend!

Richard.

---

### Post by RichardIII on 2007-10-25
PE,

I see in your information that you are running 7.10... did you perform a clean install, or did you upgrade?

If the latter, how did you get past the freezing cache read?

BTW: I have a FF image now, just in case ;)

Thanks in advance,

Richard.

---

### Post by PartisanEntity on 2007-10-26
I did a clean install, I could not be bothered to wait :) In my case, I had previously upgraded from Edgy to Feisty, so I decided it was time to have a nice and clean install.

---

### Post by RichardIII on 2007-10-26
OK, PE, that clears the matter completely!

Later next week I'll try again upgrading from within FF.

There is little that I'd like to see lost in the transition from FF to GG on this system, it's my primary system... The Windows boxes here are all secondary systems

---

