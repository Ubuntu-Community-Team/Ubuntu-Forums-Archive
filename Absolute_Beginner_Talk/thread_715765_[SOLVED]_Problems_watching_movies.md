---
title: "[SOLVED] Problems watching movies"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by computermesh on 2008-03-05
First off this is my first install of any Linux system so any help would be greatly appreciated. I either download a video or watch it through the browser and it tells me I do not have the appropriate codec. So I do a search and it finds gstreamer0.10-plugins-ugly. I try to install it and it wont let me and I need to go to the synaptic package manager. Go into the package manager and find it and mark it to install. It still wont install because it says other programs are required so I also mark them for installation and those wont install because it says they are not available. I'm just wondering if simple things like this are always this difficult or if I'm just doing something wrong. Also if anyone has any links to Intro to Linux guides it would be greatly appreciated. Thanks.

---

### Post by mikeyphi on 2008-03-05
> **computermesh said:**
> First off this is my first install of any Linux system so any help would be greatly appreciated. I either download a video or watch it through the browser and it tells me I do not have the appropriate codec. So I do a search and it finds gstreamer0.10-plugins-ugly. I try to install it and it wont let me and I need to go to the synaptic package manager. Go into the package manager and find it and mark it to install. It still wont install because it says other programs are required so I also mark them for installation and those wont install because it says they are not available. I'm just wondering if simple things like this are always this difficult or if I'm just doing something wrong. Also if anyone has any links to Intro to Linux guides it would be greatly appreciated. Thanks.

 Open Systems/Administration/software Sources
make sure that all four repos are enabled
Then
Open Add/Remove
search for and install 'Ubuntu Restricted extras'

---

### Post by billgoldberg on 2008-03-05
Yes ubuntu restriced extra's are ok.

But I suggest adding the medibuntu repo and then downloading vlc media player.

You also need to download libdvdcss2, the win32 codecs and the non-free codecs from the medibuntu repo.

[how-to]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

---

### Post by kpkeerthi on 2008-03-05
vlc is part of universe: [http://packages.ubuntu.com/gutsy/vlc](http://packages.ubuntu.com/gutsy/vlc)
medibuntu packages: [http://www.medibuntu.org/packages.php](http://www.medibuntu.org/packages.php)

---

### Post by billgoldberg on 2008-03-05
> **kpkeerthi said:**
> vlc is part of universe: [http://packages.ubuntu.com/gutsy/vlc](http://packages.ubuntu.com/gutsy/vlc)
medibuntu packages: [http://www.medibuntu.org/packages.php](http://www.medibuntu.org/packages.php)

Yes but the vlc in the universe repo is not the full version of vlc (it won't play dvd's for instance), you need the vlc from the medibuntu repo.

---

