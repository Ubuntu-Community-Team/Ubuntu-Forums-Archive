---
title: "I need help getting my USB adapter to work..."
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by imalumberjak on 2006-04-01
I have 5.10, which is, to my knowledge, the latest verison of Ubuntu. I'm trying to install my WG111T Wireless internet adapter, and I need help.

I did some research and came across a site that says ndisgtk is included in the Universe Repository. What exactly is a Universe Repository, and how do I enable it? Help would be appreciated. :D


[This]("http://spohlenz.blogspot.com/2005/08/ndisgtk-in-universe.html") is the site.

---

### Post by audax321 on 2006-04-01
Repositories are what you use to download and install software via apt-get or Synaptic.

The universe/multiverse repositories contain extra software that is not included with the main Ubuntu distribution. To add these you just edit /etc/apt/sources.list (there will be a line in there to uncomment by removing the # in front of it). It's a good idea to disable the repository by putting the # back in after you are done with it. You can edit the file using the following command: sudo gedit /etc/apt/sources.list

You could also try the how-to here to do it through a GUI:
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28Repositories%29)

To update the list of software you can install, either load up Synaptic and hit the Reload button or run the command: sudo apt-get update

Then just install the package you want via Synaptic or apt-get.

---

### Post by ORF1000 on 2006-07-27
I got my WG111T to work in Dapper by downloading and compiling a later version of ndiswrapper, version 1.21.  The 1.8 in the Ubuntu repositiories just doesn't work, at least not with my chipset.  [I followed the instructions in this wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  It wasn't hard to do.  It was worth it in the end because the WG111T a pretty good device.

Dave

---

### Post by ORF1000 on 2006-07-29
One more thing about the WG111T -- you need to install both Windows drivers -- athfmwdl.inf and netwg11t.inf.

---

