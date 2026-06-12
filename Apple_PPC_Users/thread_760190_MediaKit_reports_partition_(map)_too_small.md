---
title: "MediaKit reports partition (map) too small"
date: 2008-04-19
forum: Apple PPC Users
---

### Post by Condip on 2008-04-19
Okay, i have successfully installed Ubuntu! Unfortunately it erased all of my information from mac os x (luckily i have recently backed up!). So know i am running feisty fawn. I can boot up okay on that, and all is well. I poped in my leopard install disk and choose my language. It says install leopard on the fallowing drive (and should have a list of available drives, but instead shows nothing!) I opened up disk utility and selected my drive. It shows 2 partitions... One is 18.63 gigs and one is 1.86. I think one is swap and one is just for ubuntu to use for normal stuff. That still leaves me with 91.29 gigs of free disk space. I clicked the add partition button and it prompted me with the dialog to confirm adding one, and also telling me that nothing would be erased, so i said yes. Then i get this error&#8212;
Partition Failed

Partition failed with the error:

MediaKit reports partition (map) too small.

I clicked okay, and tried again. This time i changed the 1.86 partition to 5, 10, and 15 gigs thinking that might be the problem (that that partition was too small) and nothing! How do i fix this? I want to be able to dual boot Mac OS X 10.5 and Ubuntu, and help would be greatly appreciated. :)

---

### Post by SWedd on 2008-06-24
I had a similar problem to this after I uninstalled Ubuntu from my powerbook G4.

In my case, it was caused by the Apple_Bootstrap partition (created during Ubuntu install), of format unknown to OSX. This partition was positioned right after my Macintosh_HD partition.

To enlarge my Macintosh_HD I needed to use diskutil to erase the Apple_Bootstrap partition to a blank "MS-DOS" partition. Then I could use Disk Utility to Delete the MS-DOS partition. After that I could resize my Macintosh_HD freely.

Thought this was worth posting as I couldn't find a solution that didn't involve a complete wipe elsewhere.

---

