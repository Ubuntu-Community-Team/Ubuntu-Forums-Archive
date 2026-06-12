---
title: "Recommendations on Remote Access"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by jdecker403 on 2006-12-27
I am an Ubuntu newbie trying to get away from the MS world. I need a recommendation on what kind of remote desktop app I should use to access my latest version of LTS Ubuntu box. I heard of FreeNX, x11vnc and others and would like to know which one you all have a preference too. 

What I am looking for is this:
Ease of installation and use
Reliable, meaning the host will be available even after I disconnect from host.

For the last two days I’ve been doing searches on Google and Ubuntu forums and tried setting up X11vnc, and regular vnc using some of the threads I read in the forums. So far from my windows box, I can connect to my Ubuntu box but it only gives me a grey screen with a large X in the middle. Before I underwent any of this I installed Ubuntu with Gnome as default, but I then added KDE since it’s seems to run much quicker on my old laptop that has 256 of memory with 800mz PIII. So I have a mixture of the two, Gnome and KDE. Since then I’ve trying to get x11vnc and vnc to work on the KDE side of things with no avail. I’m planning to do a clean install of Ubuntu and trying my luck again. Any advice on how to get remote desktop going on a Gnome or KDE will be greatly appreciated.

---

### Post by jonathan.lees on 2006-12-27
I use the Remote Desktop that comes with Gnome, it works flawlessly for me and it's very simple to get working:

Click on system > Preferences > Remote Desktop this will allow you to turn on Remote desktop, Click in the allow other users to view your desktop button, click off the require your permission if you like and click on the require user to enter a password. Enter a password and click on close.

You can now use a vnc client on a remote machine to connect to it.

---

### Post by jdecker403 on 2006-12-27
Thanks, I didn't realized that gnome came with a remoted desktop feature only after I tried installing x11vnc. I tried to enable it but it does not work. Another vnc seems to be starting up  that seem to take presedence. When I get home I will try to do a fresh install of ubuntu and try running the remote desktop that gnome comes with.
Do you know if this remote desktop is availave in the KDE side of things? I tried looking for it but I could not find it there.

Thanks again...

---

### Post by jonathan.lees on 2006-12-27
The remote desktop feature is part of Gnome called Vino so I guess it's not a feature of KDE. I don't use KDE so I don't know if there is an alternative for it.

Here's a link for using [Vino]("http://gnomejournal.org/article/29/remote-desktop-administration-using-vino")

---

### Post by Ozitraveller on 2006-12-27
You might find this useful:

Search for "Remote Access" in this guide.

Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)


There is a lot of other good stuff here too.


Also these might help:
[http://www.tightvnc.com/](http://www.tightvnc.com/)
[http://www.tightvnc.com/related.html](http://www.tightvnc.com/related.html)
[http://www.realvnc.com/](http://www.realvnc.com/)

---

### Post by jdecker403 on 2006-12-27
Thanks Ozitraveller, Ill be sure to look at the links. If you all happen to run accross on how to get remote desktop going on Kubuntu please let me know. Jonathan, thanks for the tip. I heard of vino mentioned before in some of the forums, I just didn't know that was Gnome's remote desktop app was called that. Thanks...

---

