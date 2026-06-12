---
title: "Upgrade from 10.04 to 12.04 PPC"
date: 2012-10-23
forum: Apple Hardware Users
---

### Post by banzaay on 2012-10-23
Hi all 

I have Ubuntu 10.04 installed on PowerBook  G4.
During the automatic Distribution Upgrade to 12.04  (I follow this tutorial [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer#From_10.04_to_12.04](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer#From_10.04_to_12.04)), while the process is downloading the data files, I have the following error:

W:Failed to fetch
[http://ports.ubuntu.com/ubuntu-ports/di ... se/Release]("http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release")  Unable to
find expected entry 'partner/binary-powerpc/Packages' in Release file
(Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old
ones used instead.

The upgrade process stops and a complete rollback is performed.

What is the problem ? Can you help me ?

Thanks
Ciao Mirko

---

### Post by powerpcliberation on 2012-10-25
Try this.

Fire up the terminal and type:

* sudo apt-get clean*

After you enter your password type:

[I]sudo apt-get update
[/I]
After this run the updates again.  If the issue persists then you would be better off just downloading the 12.04 iso and installing from scratch.

Hope that helps.

---

### Post by banzaay on 2012-10-31
This solution doesn't work.

I also tryed to download the file [http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release](http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release). Inside this file I can't find  'partner/binary-powerpc/Packages'.
:confused:

Is there someone that have performed this upgrade ?

Thanks Mirko

---

### Post by powerpcliberation on 2012-10-31
> **banzaay said:**
> This solution doesn't work.

I also tryed to download the file [http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release](http://ports.ubuntu.com/ubuntu-ports/dists/precise/Release). Inside this file I can't find  'partner/binary-powerpc/Packages'.
:confused:

Is there someone that have performed this upgrade ?

Thanks Mirko

As I wrote already, if the terminal fix didn't work it's much simpler just to download a full 12.04 iso which you can get [here]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-powerpc.iso").

I made a Lubuntu install guide on my blog for 12.04 which you can read [here]("http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html").  It's easy to install but there are a few default things that don't work as intended on PowerPC.  The guide is to help with those quirks and be sure everything is setup properly.

---

### Post by powerpcliberation on 2012-12-29
updated info not needed after all

---

