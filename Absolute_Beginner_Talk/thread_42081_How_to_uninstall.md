---
title: "How to uninstall?"
date: 2005-06-15
forum: Absolute Beginner Talk
---

### Post by silent-red on 2005-06-15
I have recently installed RealPlayer10GOLD. How could I uninstall this I have installed this using a .bin file not .rpm file.

What are the pros and cons of a .bin and .rpm files?

Thanks

---

### Post by Kyral on 2005-06-16
First off. Ubuntu uses .deb (or Apt-Get, which is really just a *long talk about how Apt works with .deb* ) and not rpms.

Now, what I would tell you is to find the main file where it resides (don't delete /usr/bin if its there) and delete it. If it was a .deb all you would have to do is sudo dpkg -r <packagename>

---

### Post by silent-red on 2005-06-16
Where does usually a main file resides? Is it the .bin file the main file? 

Where can I find .deb packages?

---

### Post by Kyral on 2005-06-16
there is a "RealPlayer 10 based on the open source Helix Player" (as taken from the results of apt-cache search realplayer) package in the Ubuntu Repos (I don't know which, I'd just enable Backports, Extras, Universe, Multiverse, and Restricted repos for Hoary, check the UbuntuGuide for how to )

As for the bin, unless you are strapped for space, I'd just leave it. I doubt it would do any harm. 

Most software installs will be done through Apt-Get/Synaptic. Only in a few cases (Point2Play comes to mind) will you need to manually download and install a .deb, and then it will usually be offered from the website.

---

### Post by silent-red on 2005-06-17
Thanks for your response.

---

