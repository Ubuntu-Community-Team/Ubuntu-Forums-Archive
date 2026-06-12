---
title: "Windows/Linux question"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-24
Without telling me "Windows sucks" or because "Linux is better" Can someone tell me why Linux runs my vms' so much faster. I had ubuntu running windows in a virtualbox this worked great,  but it was not practical. My all in one is not compatable with Linux plus I have a hub rather than a router and Linux can't force an ip address like Windows can. So I switched now xp is running Ubuntu in a virtualbox, only it's doing it so much slower. Is there a specific reason for this. Is there a way to optimize Windows for this kind of application? I know my cpu is cappable of running a vm at normal speeds 'cause Linux was doing it just fine. If anyone has a soloution to this let me know please. Thanks.

---

### Post by Marsolin on 2007-07-24
I have noticed this too and my personal belief is that it is due to Windows being a memory hog and having to do a lot of background tasks that are unnecessary in Ubuntu. I notice a lot more disk churn on my work laptop that runs Kubuntu in a VM, and those disk accesses lock the rest of the system out.

---

### Post by Paulmd on 2007-07-24
> **swoll1980 said:**
> Without telling me "Windows sucks" or because "Linux is better" Can someone tell me why Linux runs my vms' so much faster. I had ubuntu running windows in a virtualbox this worked great,  but it was not practical. My all in one is not compatable with Linux plus I have a hub rather than a router and Linux can't force an ip address like Windows can. So I switched now xp is running Ubuntu in a virtualbox, only it's doing it so much slower. Is there a specific reason for this. Is there a way to optimize Windows for this kind of application? I know my cpu is cappable of running a vm at normal speeds 'cause Linux was doing it just fine. If anyone has a soloution to this let me know please. Thanks.

Any time you run a VM, you have overhead from the underlying OS.

You can mitigate some of this by adding more ram, but the issue cannot be entirely eliminated. It's the nature of the beast.


The one explanation I can provide is that you had less overhead with your linux VM.

Neither one is as efficient as running in a standalone environment.

---

