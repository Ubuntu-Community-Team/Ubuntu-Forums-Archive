---
title: "Live Streaming Video will not work in ubuntu"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by rex66 on 2007-06-13
Hi all....I'm very new to linux and I tried Fedora first. I like Ubuntu much better but I'm having one problem. I can't get live streaming video to work from meadowlands race track. It worked fine in Fedora, but I do not want to switch back as ubuntu seems to be much smoother for everything else on my system. Anyone have any tips to try? I've already installed all the gstreamer goodies.

Thanks
rex66

---

### Post by mgmiller on 2007-06-13
If you give a link to what you are trying to receive, maybe someone here can trouble shoot it for you.

---

### Post by rex66 on 2007-06-13
Thanks mg....I wasn't sure if link posting was allowed. This is the link. 

[http://www.thebigm.com/liveVideo.asp](http://www.thebigm.com/liveVideo.asp)

In fedora I would then click on  	"Click here for live video
(all connection speeds)"  

and the video feed was great for several hours.

Thanks again

---

### Post by mgmiller on 2007-06-13
Actually, I may have figured it out.  You need to install a firefox extension called media player connectivity.  And you also need to have vlc (a media player) installed.  You can install vlc through synaptic.  After they are both installed, tell mediaplayerconnectivity to  use vlc for windows media streams.  Worked for me.  The command line to enter in MPC is /usr/bin/vlc on the windows media line.  You will find the controls for it in firefox under the Tools drop down.

---

### Post by mgmiller on 2007-06-13
I just tried it again and it worked fine.  One tweak in MPC is to have the check box under the letter A checked so it autoplays.  You should have vlc installed first so MPC can find it on the initial install and you can then easily default it to vlc for windows media.  I usually have that set to default to gmplayer, but it wouldn't work for this stream.  MPC is a very handy extension as it lets you quickly and easily change around the video players for different streams.

---

### Post by rex66 on 2007-06-13
mg...thanks for all the help....I'm still having trouble....I followed your directions and tried it and it did not work....i went back to look at mpc to make sure i pasted the command line correctly and all of the media players were gone from the list except real media....any idea what i could have done to eliminate the others?

---

### Post by mgmiller on 2007-06-13
Try rerunning the configuration wizard again.  Look in firefox  Tools>Media player Connectivity>configure.  and then click the box on the top that says Wizard and then start configuration wizard.  You should have vlc already installed, or it won't see it as a choice.

---

### Post by rex66 on 2007-06-13
Okay....i uninstalled mpc.....(I had installed it before VLC) ...then reinstalled it. It works fine now!....Thank you my friend....you've been a tremendous help!

rex66:D

---

### Post by mgmiller on 2007-06-13
:lolflag:

I love this forum.

Welcome to Ubuntu.

---

### Post by kittyhawk63 on 2007-06-13
.

---

### Post by kittyhawk63 on 2007-06-13
Remember to mark your thread as "Resolved."
kh

---

### Post by rex66 on 2007-06-13
kitty....after poking around I'm still unable to find how I mark it resolved??

---

### Post by mgmiller on 2007-06-13
Since you own the thread, try editing it again, if need be, click on the "go advanced" button and then just change the name of the thread to:

 Re: Live Streaming Video will not work in ubuntu-resolved.

---

