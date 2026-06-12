---
title: "Exaile 2.14 for ppc"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by avtolle on 2009-01-22
For those using exaile for their music player on PPC, I'm sure you have been seeing the popup that appears when starting it to the effect that version 2.14 is out, grab it from [www.exaile.org](www.exaile.org). As anyone who has taken the bait knows, the new version is nicely packaged for Ubuntu i386 and AMD 64, but no ppc. So, just for grins, I decided to download the tarball and compile it to see if it would build.

If on 8.10, the dependencies are installed already if exaile is installed, save one. What I found I needed was python-gtk2-dev, on the first attempt to "make". Once that was installed, it compiled and installed successfully. The major benefit I have found with it so far is that the Shoutcast plugin now works (I had upgraded the plugin previously when the new update to it was released, and it didn't work for me) to scan Shoutcast for different genres of music.

Generally, download the tarball from the site, and extract it (I did it on the Desktop). Once extracted, the INSTALL file gives the instructions to install it, which I followed. Once completed, exaile 2.14 is installed to /usr/local, and launches from the applet in the panel without problem.

So, if you are feeling adventurous, give it a whirl.

---

