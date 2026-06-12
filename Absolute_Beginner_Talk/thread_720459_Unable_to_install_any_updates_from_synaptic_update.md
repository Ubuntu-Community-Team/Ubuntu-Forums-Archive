---
title: "Unable to install any updates from synaptic update manager"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by sethu_iiit on 2008-03-10
Hi,
I am a newbie to Linux and I have Ubuntu Gutsy 7.10 installed on my laptop here. 
Mistakenly, I deleted my /var/lib/dpkg folder today and after several hours of googling, I followed the below steps to recover the same.

[B]sudo dpkg --clear-avail
sudo dpkg --auto-deconfigure[/B]


After this, **sudo apt-get update** seems to work perfectly. But when I try to install the newly downloaded packages using the Update Manager, I am getting this error "**E: Internal Error, Could not perform immediate configuration (2) on libpam-runtime**"...

Please help me in resolving this problem. Any help much appreciated

Cheers,
Sethu S

---

### Post by red_Marvin on 2008-03-10
After looking at the man page for dpkg I think you might want to run *sudo dselect update* but I should say that I'm no expert.

---

