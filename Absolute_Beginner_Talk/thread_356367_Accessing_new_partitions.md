---
title: "Accessing new partitions"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by thompa on 2007-02-08
HI,

Well, after the mess I made by typing in a long entry into the terminal which resulted in me having to reinstall and lose everything (lesson there!), I researched about partitions and decided to go with putting the system onto its own partition '/' so that future system upgrades wouldn't affect my settings.....

I used GParted which worked fine except that it showed an unallocated partition of several mB that I couldn't eradicate or combine with another partition. I believe that I may have to edit fstab... can anyone advise how I get rid of the unallocated space ie make it usable in one of the other partitions?

Which brings me nicely to another issue.... I have updated the files using synaptic... but am not sure that I am doing this correctly now that I have a separate partition for the system files.

Should i be doing something special? When I had everything together on one partition, I could access 'root' but now I can't.

I am just getting some uneasy feelings... since one of the updates I wanted was to Samba and this refused to install

I am looking for reassurance here... and treading very carefully and making a log of everything I do - just in case.... after making such a mess last time

---

### Post by thompa on 2007-02-08
OK.... sort of confirmed my suspicions, I think....

Tried to install gdesklets using automatix2 and the log reads:-

E: samba : subprocess post-installation script returned error exit starter 102
E: swat:dependency problems - leaving unconfigured..

I did some reading and it did seem as though the '/' partition wasn't mounted and I have now done this following the advice here:- [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) 

But still I fee lost in the Ubuntu jungle....

Can anyone help?

---

