---
title: "BitTorrent"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by dylondadank on 2008-03-19
can i get help installing bittorrent please?

---

### Post by jken146 on 2008-03-19
Bittorrent is a method of sharing files over the internet.  A bittorrent client is a program that allows you to use .torrent files to do filesharing.  There is already a bittorrent client installed in Ubuntu (I forget what it's called) but it isn't very sophisticated.

I recommend you try deluge.  You'll find it in Synaptic.  Alternatively, type ```
sudo aptitude install deluge
```

---

### Post by dylondadank on 2008-03-19
it has been installed, but where do i find it now??? i see it nowhere

---

### Post by kpkeerthi on 2008-03-19
I think it should be in applications -> internet

or Press ALT+F2 and type **deluge** <press-enter>

or open a terminal and type **deluge** <press-enter>

---

### Post by dylondadank on 2008-03-19
i guess when i ran it in terminal it did not install properly, so now i am installing from synaptic see if that turns out a little better =]

thanks

---

### Post by kpkeerthi on 2008-03-19
A latest version of deluge is available [here]("http://www.getdeb.net/app/Deluge")
1. Download the two deb files to /home/<user>/downloads folder. 
2. Open a terminal 
3. Type ```
cd /home/<user>/downloads
```
3. Then type ```
sudo dpkg -i *.deb
```

You may also download it from [http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by Xiong Chiamiov on 2008-03-19
> **kpkeerthi said:**
> A latest version of deluge is available [here]("http://www.getdeb.net/app/Deluge")
1. Download the two deb files to /home/<user>/downloads folder. 
2. Open a terminal 
3. Type ```
cd /home/<user>/downloads
```
3. Then type ```
sudo dpkg -i *.deb
```

You may also download it from [http://deluge-torrent.org/](http://deluge-torrent.org/)

Of course, he could also just navigate to the directory in Nautilus and open the .debs...

---

### Post by kpkeerthi on 2008-03-19
> Of course, he could also just navigate to the directory in Nautilus and open the .debs...

Yes.. but being new to ubuntu, he may not be sure as to which deb he should install first so the dependecies are properly taken care.

---

### Post by dstin1 on 2008-03-19
I used utorrent with windows but now I am using azureus, since there is now utorrent for linux.  This was an easy transition for me and I installed it through synaptic.  I also use the same ports on my router that I used with utorrent.

---

### Post by hyper_ch on 2008-03-19
bittorrent is also a client for the bittorrent protocol ;)

azureus is a memory hog...

---

