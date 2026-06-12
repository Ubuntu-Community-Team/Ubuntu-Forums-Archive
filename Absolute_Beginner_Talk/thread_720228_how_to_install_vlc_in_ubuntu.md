---
title: "how to install vlc in ubuntu???"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by arko_saha_cse on 2008-03-10
hi............
i m a Beginner in ubuntu.....
if you help me how 2 install VLC in ubuntu???
i have following version of vlc--(vlc-0.8.6e.tar.bz2)...
can u say me is it a right version????
pls help me......:)

---

### Post by -random on 2008-03-10
go to System > Administration > Synaptic Package Manager.

click on settings > repositories, and enable universe repository.

then click reload, search: 'vlc'

click on []vlc and 'mark for installation'

then click Apply.

- - -

(they reccomend also to install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2). But i didn't and my vlc works fine. Source: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html))

---

### Post by NightwishFan on 2008-03-10
open a terminal and type:
sudo apt-get update
type password (its invisible)

let it finish then type:
sudo apt-get install vlc

When its done you are good to go.

---

### Post by jan quark on 2008-03-10
the posters above said everything 
 you can check also this guide for tips how to install applications in ubuntu:
[LIST]
[*][http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[/LIST]

---

