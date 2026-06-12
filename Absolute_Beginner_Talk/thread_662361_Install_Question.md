---
title: "Install Question"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by mjheagle8 on 2008-01-08
I want to install WINE on a ubuntu 7.10 desktop that cannot access the internet.  I downloaded the binary to my flash drive.  Can I install it from that?  How?  Thanks for your help!

---

### Post by RomeReactor on 2008-01-08
Hi. You would need to install many [dependencies prior to installing Wine]("http://packages.ubuntu.com/gutsy/otherosfs/wine") (note packages marked in red), and many of those packages have dependencies of their own, and so forth. Instead, try opening Synaptic and search for Wine; if it shows up, mark it for installation, then go to 'File->Generate package download script'. This will create a script that will download all the necessary packages, including dependencies. You can then use this script in another machine with internet connection running Linux, or download the packages manually in a windows machine by opening the script in a text editor and pasting each URL in a browser.

Once you have all the packages, copy them to your Ubuntu system, open Synaptic again and go to 'File->Add downloaded packages'; from there, you can install Wine through Synaptic.

I'm not certain this method will work because Synaptic won't be able to check the repositories for the packages, but you can try it. Otherwise, your best option is to take your system to a friend's house and use his/her internet connection.

---

