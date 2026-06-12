---
title: "[SOLVED] NFS Share and Printer over Network Died"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-07-23
Looking back, I think it happened when I turned off RPC Mapper in services for some reason unknown to me. Still, with that enabled, And attempting to start from scratch on the NFS and printing side, I am baffled by how easy it was the first time, and how difficult it is this time. I have removed NFS and reinstalled, using the official guide. No luck. Same with the various services that can be used for printer sharing. Before, it was a piece of cake. i clicked a few things and NFS sharing and printing over the network worked flawlessly. Where should I be starting to look for the source of the problem? Any info I can post to troubleshoot?

Thanks in advance.

EDIT: At one point, when trying to add the printer again, it said the server was busy. When I try to print from the laptop (not connected to printer) the printer icon pops into the notification area, and the job will just sit there. I have quintuple (at least) checked all settings listed in the official guide, on both computers. What on earth could be going on here? I don't even know which computer to be focusing on. I really want to stick with NFS, but I might try samba for troubleshooting purposes.

---

### Post by coldstatue on 2007-09-09
It was firestarter. *smack*. had to add the laptop's ip to the allow list. I didn't realize firestarter was running.

---

