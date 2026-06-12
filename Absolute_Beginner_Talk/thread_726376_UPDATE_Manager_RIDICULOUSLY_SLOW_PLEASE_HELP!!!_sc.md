---
title: "UPDATE Manager RIDICULOUSLY SLOW PLEASE HELP!!! screenshot included..."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by systemOAD on 2008-03-16
Hi everyone,

I already had ubuntu gutsy installed before for a few months, and due to a problem i had to format my linux partition. so after fomatting it, i reinstalled ubuntu gutsy from the same installation cd that i had, but for some reason this time, the update manager is taking a while to download the necessary updates. this same thing is happening with the add/remove package manager, and synaptic package manager. i am currently downloading another ubuntu7.10.iso and the highest download speed that i reached with that was over 800kbps! but with update manager, add/remove, or synaptic, the max speed i reach is 20kbps. can anyone please please please help me with this, i would highly appreciate it. thanks.

---

### Post by durand on 2008-03-16
I've been having similar problems.. Try changing the mirror that apt-get uses.

System > Administration> Software Sources
Then click on Download from: Other > Select Best Server. Then try again with the updates.

---

### Post by Lord Illidan on 2008-03-16
Why not put your /etc/apt/sources.list here?

I believe it's a mirror problem.

---

### Post by systemOAD on 2008-03-17
yeah it was a mirror problem...changed it and not everything is fine. thanks guys.

---

