---
title: "Setting up a Kubuntu network for filesharing..."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Contrast on 2006-11-12
I've searched through several forums, this one included, trying to find a solution to this and haven't come up with anything related to my situation. I've also gone through the Kubuntu handbook and haven't found anything useful.

I have a laptop and a desktop which are running on Kubuntu 6.06, as well as another desktop on which I'll be installing Kubuntu 6.06 or Xubuntu 6.06 in the near future. My laptop and desktop are connected to a Netgear router (both hardwired), and can access the internet without any problems.
My problem is I can't figure out how to set up the network so that I can access the desktop's files from the laptop and the laptop's files from the desktop.
When I click Network folders from the Konqueror start page and then click Network Services, I'm told that the zeroconf daemon isn't running. I installed the package for zeroconf, opened a terminal and typed zeroconf, and couldn't figure out what to do with the given list of options, so I removed the package.
I tried typing "home" into the Domain name field Network Settings under System settings, and this doesn't appear to have changed anything.
I'm under the impression that Samba is only for connecting to a desktop that's on Linux, but I figured I'd try it since I've exhausted all other known possibilities at this point. When I click Samba Shares from Network Folders, it says "Unable to find any workgroups in your local network. This might be caused by an enabled firewall." Before I switched my desktop to Kubuntu from Windows XP, I could view the files on the desktop from the laptop with this method.
I'm not sure if this is possible, but I'm also wondering if I'll be able to share the files from my desktop on a P2P network if the program for that P2P network is running on my laptop.
If this has already been covered in another thread, please point me to it. Any help with this is greatly appreciated. I feel like an idiot for needing help with this, as I'm sure it's something that's painfully obvious.

---

### Post by punx45 on 2006-11-12
if you dont plan on ever sharing with any windows computers, look up guides on NFS.  if you plan to share with windows in the future, look up SAMBA.

in response to the second part of the question - can you P2P a drive on the desktop using the laptop - yes, but you have to have the network drive mounted locally (which will be the case when you solve your network sharing issues)

---

### Post by Contrast on 2006-11-13
Just now got it up and running after looking through the Kubuntu server guide's section on NFS. Thanks a lot.

---

