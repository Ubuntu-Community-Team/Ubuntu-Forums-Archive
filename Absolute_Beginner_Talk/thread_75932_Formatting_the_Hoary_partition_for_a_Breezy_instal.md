---
title: "Formatting the Hoary partition for a Breezy install?"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by Pathfinder73 on 2005-10-14
Hi

As this will be the first time I'm trying this, perhaps someone can help?

I managed to get Hoary installed and running on my second partition.  This was the first time I had ever played with Ubuntu/linux.  Now I want to upgrade to Breezy by doing a fresh install, so my question is:
When installing a new Ubuntu version (e.g. from 5.04 to 5.10) from CD, is it best to format the linux partition before doing the install, and how do you do that? i.e. can you install directly over a previous installation?

Thanks to those that help me on this.

---

### Post by cbudden on 2005-10-14
Why not do a apt-get dist-upgrade after changing your /etc/apt/sources.list file?  Im not entirely sure but you would probably just set the mount point to / in partition setup and tell it to format, at least that it what i would try.

---

### Post by ChrisTheGeek on 2005-10-14
Hi,

If you would like to do a fresh install then you will need to format the partition.  The installer for breezy can take care of this for you so just run the installer and setup the options you want in the "partition setup" section.

However, there is no real need to do a fresh install to get 5.10 goodness, just update your repositories and update.  More info here:

[https://wiki.ubuntu.com/HoaryUpgradeNotes](https://wiki.ubuntu.com/HoaryUpgradeNotes)

Enjoy :)

---

### Post by John.Michael.Kane on 2005-10-14
Pathfinder73 also the install will give  you the option to resize your space and allow for dual booting of 5.04 and 5.10.

---

### Post by Pathfinder73 on 2005-10-14
Hi

Thanks to all for the replies.  The reason why I thought of doing a fresh install was because of all my fooling around.  It might just be better to have everything fresh and clean, before I start interferring with it as I learn.

However, having never done an apt-get upgrade before, I thought I would try that first as suggested and if things really do go wrong then I have the new shiny Breezy CD disk waiting next to the PC.

Thanks once again to all for their comments

---

