---
title: "what kind of codec does this require?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by ubunter1 on 2007-04-18
hi i can pretty much watch any video on the net thanks to all the codecs and help from the ubuntu community,but this one gets me, when i go to hgtvpro i want to watch the construction videos,cause im a noob at that too:)  but it says something about a specific mplayer plugin but i do have all installed so am wondering if anyone can view this or help.here is the site- [http://www.hgtvpro.com/hpro/pac_ctnt/text/0,2595,HPRO_20196_55073,00.html?c=481&videoid=63323](http://www.hgtvpro.com/hpro/pac_ctnt/text/0,2595,HPRO_20196_55073,00.html?c=481&videoid=63323)
here is a screenshot- in firefox as well .thanks for your help.

---

### Post by wormser on 2007-04-18
It works in my Mplayer.  I think you need the libdvdcss2 and w32 video codecs.  You can find the diections toward the bottom of [this page]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html").

---

### Post by ubunter1 on 2007-04-18
do i just enter those 2 lines in the etc sources list then save?.

---

### Post by wormser on 2007-04-18
> **ubunter1 said:**
> do i just enter those 2 lines in the etc sources list then save?.

Yes, enter those to lines to /etc/apt/source.list.  I usually put a comment above them describing them.  ## w32 codecs.....  It helps when you go back to edit the file later.

Then do

**sudo apt-get update**

Then the command:

**sudo apt-get install w32codecs libdvdcss2**

---

### Post by ubunter1 on 2007-04-18
i did it but it still pops up with a totem disclaimer saying i cant play the filed:confused: .
thanks for your help though.

---

### Post by wormser on 2007-04-18
I had that same problem.  You need to uninstall the Totem plugin for Firefox.

**sudo apt-get remove totem-mozilla**

You might need to close and open Firefox again.

---

### Post by ubunter1 on 2007-04-18
it still wont work,this is crazy,but im sure some stuff is messed up now but ill keep trying your advice,mplayer is installed and the codecs now on that site it thinks like its going to open but doesnt here is a screen,thanks for the continued help for a noob:( .

---

### Post by ubunter1 on 2007-04-18
now when i click my own link it wants me to install adobe flash player version 9.tar or rpm file.:confused:

---

### Post by x-ray vision on 2007-04-18
Try right clicking in the area where the video should be playing, click 'configure' and change the video output to 'gl'.

---

### Post by ubunter1 on 2007-04-18
> **x-ray vision said:**
> Try right clicking in the area where the video should be playing, click 'configure' and change the video output to 'gl'.

did that now i can actually hear the video but not watch it,ill try the other settings as well.and ideas?. thanks.

---

### Post by ubunter1 on 2007-04-18
how do i in the terminal locate the file install flash player 9 thats on my desktop?

---

