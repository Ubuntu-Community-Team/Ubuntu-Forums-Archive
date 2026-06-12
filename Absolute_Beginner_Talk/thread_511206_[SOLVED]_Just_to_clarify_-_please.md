---
title: "[SOLVED] Just to clarify - please"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-07-27
I am just about to delete my win partition and the ext3 partition which resides with it on a hdd - set as master

at present linux boots a slave drive which is setup with / , /home and a swap partition.

What i would like to clarify is once I have reinstalled linux to the master drive - how will it react to the old file system? Will it have a minor fit :)

I need to keep the /home partition - all my media have been copied to there but can I leave the old file system?

or would it be better to delete that / partition during the install - 

ie do I need to delete the old root partition - 

if I do would it best to do that with a live gparted which I've got and then do the install from the ubuntu live cd

---

### Post by mikewhatever on 2007-07-27
I do not think the new root partition would care much about the old one. You can use the old /home with the new root or create a new /home and then copy whatever you need from the old one. Gparted is a good program to delete partitions. You do not have to delete the old ones, but why would you keep them? Hope that helps.

---

### Post by forestpixie on 2007-07-27
thanks - just checking before I start - I really don't want to have trouble trying to reboot afterwards :) with too many root partitions and homes :)

I'm also hoping that I'll be able to copy my firefox and evolution folders from the old system to the new one to keep that info - guess I'll find out - I've exported firefox as an html but couldn't find a wayy to do same with evolution

---

