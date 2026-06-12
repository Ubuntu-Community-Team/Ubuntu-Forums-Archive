---
title: "rEFIt won't work on macbook pro 6,2 why?"
date: 2011-10-24
forum: Apple Hardware Users
---

### Post by ceratophyllum on 2011-10-24
I have tried rebooting after the install more than 4 times. No refit menu appears. When I hold down alt, I only see my Mac OS X Lion partition. 

(I have created a windows format partition using Disk Utility before installing refit.)

I tried running the "manual" install script located at /efi/refit/enable.sh but still no refit menu.

I tried booting from a CD made the rEFIt dmg file. The refit menu appears and works as expected. gptsync says there is nothing wrong with my GPT/MBR boot records. 

So what is stopping refit from working from my hard drive?

Has rEFIt been abandoned? I notice the updates stopped at the rEFIt site over a year ago.

How is grub2 coming along? Can it RELIABLY boot macbooks?

---

### Post by mactom on 2011-10-27
I also had a problem with rEFIt: I updated 11.10 then after rebooting I see a grey screen and a question mark.
I suppose that Ubuntu update made something....
Now my original OSX 10.6.3 is not booting so my MBP is dead:sad:

---

### Post by mactom on 2011-10-27
Is there someone that can give any suggestion??

---

### Post by ceratophyllum on 2011-11-20
Update: better off w/o rEFIt

1. I uninstalled rEFIt, following the instructions at the rEFIt site. I can deal with holding down ALT better than the added complication of rEFIt.

2. I booted from the Lion DVD and ran disk utility and had it repair everything it could. (The Lion DVD was created from the dmg file in the Lion installer app. Ars Technica explains how to do this.)

3. I deleted the extensions cache and zapped the PRAM after I applied the mid 2010 macbook pro Black Screen Of Death firmware fix. Something seems to have gotten ALT booting back to normal: Both the HFS+ and ext4 (mislabelled "Windows") partitions are now visible and boot as expected.

---

