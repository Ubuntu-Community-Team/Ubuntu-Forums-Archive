---
title: "Virtualisation on a HP compaq 6710b"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by He|iX on 2007-11-28
I have a HP Compaq Laptop 6710b T7250 2.00 GHz with 4GB RAM.

At the moment I have vista ultimate installed and was wondering wanting to use virtual box with ubuntu 7.10.

Has anyone done this? or have any better suggestions? At this stage I was going to allocate 512 MB RAM to ubuntu via the VM, or should I go for1GB? The average physical memory I use at the moment without a VM running is 1.8GB RAM.

would virtual box be the way to go i this case? or would soetihng like VMware server etc be a better choice?

Thanks in advance! :)

---

### Post by jba6511 on 2007-11-28
virtualbox would work fine. 512 MB of RAM would work but a gig would be even better. If you need more you can always change it later.

---

### Post by Jonne on 2007-11-28
> **jba6511 said:**
> virtualbox would work fine. 512 MB of RAM would work but a gig would be even better. If you need more you can always change it later.

4GB is plenty of RAM. I've run vmware on a box that had 512MB. Ubuntu can live with 256MB or even 128MB, but since you've got ram to burn, go ahead and set it to 512MB. Unlike Windows, Ubuntu won't complain if you change the amount of ram afterwards, so you can experiment all you want.

As for virtualbox vs vmware: I think they're pretty much equal in functionality, so pick whichever one you want.

---

### Post by jba6511 on 2007-11-28
agreed. One side note, I find that overall virtualbox runs better for my system, but the bridged networking option in vmware is much easier to use than setting up bridged networking (host networking) in virtualbox.

---

### Post by He|iX on 2007-11-29
Thanks for that - a great help. :)

I was thinking of giving ubuntu 1GB RAM and keeping 3GB for vista - god knows you need it.

On the topic of networking - i noticed that there are a few options to get the virtual networking going. I work in an environment where I need firewall rules and reserved IP addresses, so what would be the best way to do this? I believe there is that NAT option in virtualbox - this wuold save me from having to get another IP address assigned, but would it work?:confused:

---

### Post by Jonne on 2007-11-29
> **He|iX said:**
> On the topic of networking - i noticed that there are a few options to get the virtual networking going. I work in an environment where I need firewall rules and reserved IP addresses, so what would be the best way to do this? I believe there is that NAT option in virtualbox - this wuold save me from having to get another IP address assigned, but would it work?:confused:
NAT would be best then, yes. The limitation you'll have is that if you run a server (apache, ssh, smb), only your host machine will be able to reach it (unless you forward ports), so offering services to other people on your network will be a challenge. Connecting to the internet using your ubuntu virtual machine should work without problems, unless the firewall(s) on your vista box blocks traffic.

---

