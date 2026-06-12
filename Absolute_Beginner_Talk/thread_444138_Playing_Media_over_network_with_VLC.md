---
title: "Playing Media over network with VLC"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-05-15
Hi guys,

I have Ubuntu installed on a laptop and a desktop computer.  My desktop has all my media on it... videos, music, etc.  I'm trying to play the files from the laptop over the network using VLC.  Here's what's happening:

When I double click on the video, it opens it in the default Ubuntu media player (even though, I've set it so that VLC should be the default for .avi's - when I play local files they open in VLC by default).  And it says I need to download some codecs (which I don't want to do, so I cancel it).  So I try opening VLC and dragging the file into the VLC playlist.  It doesn't appear in the playlist.  Same problem with MP3's.

So basically, VLC won't open anything over the network (it works fine on local files).  I have the folder shared as NFS, but I also tried SMB.

As a note, when I had Windows XP on the laptop and Ubuntu on the desktop, I could play the files on the laptop using VLC.

Any ideas?  Is it an issue with VLC or with the network in general?

Thanks!

---

### Post by rich.bradshaw on 2007-05-15
Can you open any other files? For instance a .doc file or a .jpg?

You can actually get VLC to stream it the otherway i.e. the computer with media plays it and your other comptuer can play it - this is how I have done it in the past, though your way seems more sensible!

---

### Post by Gothelittle Rose on 2007-05-18
Funny thing, I'm dealing with the exact same issue. I don't want to stream from my desktop. My desktop is basically my media storage. I want to be able to drag-drop into a playlist and just run a bunch of mp3's off my desktop through the network.

Is there anything a little friendlier than Comes-With-Ubuntu-Player that can do this? Or any tweak that will make just about anything able to do it?

---

### Post by phr0ze on 2007-05-18
VLC will not work like this over a network on linux. I was dissapointed because I like VLC so much on windows. You can mount the network share in a way to make VLC work fine. However, it looked like a pain so I ended up using another program which will play media over the network. I can't remember which one it is though. Also I can not find ANY program on linux which will play ipod ready video over the network. I have to copy the file to a local folder first. I think those are mp4. PM me to remind me if you need to know which programs I am using.

---

### Post by Saklander on 2008-02-18
Has anybody got a good solution for this problem? I feel that the Linux version of VLC should seriously consider implementing this. Of course I am biased because this is for me a dealbreaker. 

so what programs are you others using to get this result (video playback over network) in ubuntu?

---

### Post by Nythain on 2008-02-18
simplest solution i can think of is mount the network share... its really not hard using samba, and i imagine its only easier using nfs... may sound wonky and confusing but im a firm believer that network shares should be mounted for anything anyways... my network share is automounted via fstab every time i book actually... you dont have to have it automount really, its just as easy to set it up to mount when you want to mount it, you could even write a simple executable to do it upon clicking...

as for other programs that will play media off an unmounted network share i dont know any off the top of my head... you could look into mplayer maybe, xine-ui, or if you are using kde, kaffeine (wich i highly doubt will do it)

---

### Post by mangurt on 2008-02-18
I'm not too sure, but could you set up mythtv to do this?  Have the computer running the back end, and then have the front end on the laptop?

---

### Post by hyper_ch on 2008-02-18
Mount the remote filesystem in your local one:

NSF:  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

SSHFS: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS) (encrypted)

---

### Post by orduek on 2008-03-01
I have the same problem. I can't play media files through samba network with VLC.
It was very simple to set up this network and its much more complicated to set up unix one.
Any other solution to this problem?

---

### Post by hyper_ch on 2008-03-03
orduek: See the above post

---

