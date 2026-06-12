---
title: "How i destroyed my Unbuntu..."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-10
Hi guys...

i destroyed my Ubuntu while having an error in synaptic i had corrupted some font lib... i clicked reinstall and ...it uninstalled everything that has font in it i think... 

anyway i was thinking of upgrading to latest Ubuntu 'gusty' i think... anyway do i just reinstall over the top of everything? is there a repair option...does it delete the partitions and reinstall clean?

thanks...i always learn the hard way !!! :) :popcorn:

---

### Post by Jimmyfj on 2007-08-10
Yes - Just plug in the Live Cd and boot up on it.

As for Gutsy. Gutsy is still in beta and WILL crash at some point. I know mine did - For the third time - But never mind - I enjoy the competition with it.

---

### Post by SOULRiDER on 2007-08-10
You can boot into safe mode and do
```
sudo aptitude install ubuntu-desktop
```
If that doesnt work try reth reinstall instead of install. Mind you, its gonna be a big download, but it may fix it.

---

### Post by Hopeless on 2007-08-10
hi,

ok i'll give it a shot...
 where is the re-install option?

---

### Post by ravenwere on 2007-08-11
```
sudo aptitude reinstall ubuntu-desktop
```

---

