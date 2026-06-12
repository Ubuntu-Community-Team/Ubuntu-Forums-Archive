---
title: "mp3 playback on rythmbox"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2007-02-21
Forget the repositoriesm for a second please.  Can someone just tell me a URL where I can get mp3 playback codec for rythmbox?  It's default ogg I know.  Now, when I had Breezy, there wasw a place I could go and download a thing that let me play mp3 as well as ogg on Rythmbox.  The same thing's gotta exist for Dapper Rythmbox.  Help?

---

### Post by ashmew2 on 2007-02-21
whats the forget about repositorism thingy ? :P Why dont u just opena  terminal and do 
```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

Then u can play any song file with any player of your choice..
If you are having trouble with enabling multiverse/universe repositories (which i think is the reason for anti-repositorism :P) , u can understand how to do so by clicking [here]("https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto")

---

### Post by tonyr1988 on 2007-02-21
If you don't want to use repositories (for some reason), you can get the *.deb files at [http://packages.ubuntu.com](http://packages.ubuntu.com) (gstreamer0.10-plugins-ugly for mp3 support, I believe), but you'll have to worry about dependencies.

---

