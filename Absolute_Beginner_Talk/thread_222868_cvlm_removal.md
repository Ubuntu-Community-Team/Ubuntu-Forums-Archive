---
title: "cvlm removal?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by levigruber on 2006-07-25
I installed cluster manager (and redhat cluster suite and cvlm) - thinking that it was for managing the clusters on my hard drive. Install failed ( clvm: subprocess post-installation script returned error exit status 3-redhat-cluster-suite: dependency problems - leaving unconfigured - system-config-cluster: dependency problems - leaving unconfigured ) - At any rate, I removed completely all but clvm - now when I try to install Synaptic returns "clvm: subprocess pre-removal script returned error exit status 1". I went online and found a blog which suggested "sudo dpkg --purge ltmodem", and  tried this. If I install any more packagesw I still have the clvm error. Thanks in advance.

Levi](*,) ](*,)

---

### Post by kisiyel on 2006-08-18
I had a similar problem and

sudo rm /etc/init.d/clvm
sudo apt-get remove clvm -f --purge

solved my problem. Now no problem at installing.

---

