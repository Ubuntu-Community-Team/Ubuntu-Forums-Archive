---
title: "Troubling with updates"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by bkeithly on 2007-01-15
Computer:
laptop hp 6040dv
Ubuntu Edgy 6.10
Linux keef-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux


I keep getting failures when attempting to do a distribution upgrade.

here is what happens:

system indicates that there are some upgrades/updates.

I click on the synaptic package manager and start the upgrade process.

There are two grades, 2 download and appear to be applied. But then the system tells me I have to do a distribution upgrade.

I click on the button to apply the distribution upgrade but it fails. the system tells me to look at this file:

/var/log/dist-upgrade/

and here is what the file says:


<b>Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9746
Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvid
ia-glx 2
Removing nvidia-glx rather than change nvidia-kernel-1.0.9746
Done
Installing ekiga as dep of ubuntu-desktop
Installing yelp as dep of ekiga
Installing firefox-gnome-support as dep of ubuntu-desktop
Installing gnome-app-install as dep of ubuntu-desktop
ERROR:rootist-upgrade failed: 'A essential package would have to be removed'
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9746
Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvid
ia-glx 2
Removing nvidia-glx rather than change nvidia-kernel-1.0.9746
Done
</b>


Do I need to remove the nvidia packages? Is there any way to upgrade and keep the nvidia stuff installed?

uname -a on my machine:

Linux keef-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux


The biggest problem I am having with updates/upgrades is they nock out my nvidia drivers and my ndiswrapper stuff. Then I have no network and my video goes to crap.

Does anyone know how to update/upgrade and prevent these things from gettiner overwritten (nvidia, ndis)


Sorry for all the questions, but I am really digging ubuntu and if I can get around these few issues I will be in great shape!!!!!

---

### Post by Seine on 2007-01-20
The following worked for me. (You may not get the same kilometreage). 

[http://www.ubuntuforums.org/showthread.php?p=2041710#post2041710](http://www.ubuntuforums.org/showthread.php?p=2041710#post2041710)

---

### Post by bkeithly on 2007-01-20
Envy worked

---

