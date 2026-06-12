---
title: "Can't write to CD's."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-09-26
I was wanting to write 4 mp3's to a 700mb cd and I am getting,

"Insert a rewritable or blank disc

Please put a disc, with at least 83.8 MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW"

Which is i know i do have the right types.

---

### Post by Jimmyfj on 2007-09-26
Which Cd writing software are you using?

---

### Post by phizikal on 2007-09-26
CD/DVD Creator. Which app you prefer to write cd's?

---

### Post by Jimmyfj on 2007-09-26
I prefer Brasero Disc Burning Application it's easy to use and haven't failed me yet. Try Brasero and see if you get the same error from it.

---

### Post by sstusick on 2007-09-26
You could try NeroLinux or K3b.

---

### Post by phizikal on 2007-09-26
In repositores? Where can i get it... get deb?

---

### Post by sstusick on 2007-09-26
You can get k3b (a KDE program)  from add/remove.. not sure about NeroLinux.

---

### Post by Jimmyfj on 2007-09-26
Correct. You can get Brasero from 

there: [http://www.getdeb.net/download.php?release=1318&fpos=0](http://www.getdeb.net/download.php?release=1318&fpos=0)

It should be in the repo for 7.04 but I can't remember if it is - Haven't run 7.04 for a while now. It's in Programs>Add/Remove>Music and Videoes in Gutsy though. But just click the link and you should find it there.

---

### Post by phizikal on 2007-09-26
Brasero didn't work also... The reason why I was burning MP3's because... I Dont have no sound.. and I am getting a error on this also.

Does it require sound to burn?

---

### Post by phizikal on 2007-09-26
All the CD  burning apps say i need gstreamer plugins.

---

### Post by mcduck on 2007-09-26
> **phizikal said:**
> All the CD  burning apps say i need gstreamer plugins.

If you wan to burn MP3 files into Audio CD (playable in nomral CD players) you need the required plugins so the burning application can convert your MP3s into normal audio.

Just install all gstreamer0.10-plugins from Ubuntu's repositories and it should work fine.

If you are trying to make MP3 disk (playable with computers and MP3-players) you need to burn it as Data-CD, not as Audio-CD. In that case you don't need the gstreamer plugins, although you probably want to install them anyway to get your media files working..

---

### Post by phizikal on 2007-09-26
gstreamer0.10-plugins isn't in the repos or its broken.

---

### Post by mcduck on 2007-09-26
> **phizikal said:**
> gstreamer0.10-plugins isn't in the repos or its broken.

Yes, they are. You may need to enable Universe & Multiverse repositories to get all the plugins.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gstreamer0.10&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gstreamer0.10&searchon=names&subword=1&version=feisty&release=all")

---

### Post by phizikal on 2007-09-26
I know i have all my repos. 

"""""""
 sudo apt-get install gstreamer0.10-plugins
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package gstreamer0.10-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins has no installation candidate
""""

---

### Post by mcduck on 2007-09-26
> **phizikal said:**
> I know i have all my repos. 

"""""""
 sudo apt-get install gstreamer0.10-plugins
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package gstreamer0.10-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins has no installation candidate
""""

You misunderstood what I meant. Don't try to install a single package called 'gstreamer0.10-plugins', instead do a search in Synaptic and install all gstreamer0.10 plugin packages..

---

### Post by phizikal on 2007-09-26
I used synaptic to get all the plugins. and I am still getting this error.

I dont have no sound and I can't find my sound card nor the howto fix sound problem tutorial doesn't help...

---

