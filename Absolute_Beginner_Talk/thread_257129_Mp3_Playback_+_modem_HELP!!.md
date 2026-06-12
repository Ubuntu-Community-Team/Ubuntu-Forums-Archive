---
title: "Mp3 Playback + modem HELP!!"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by ChesterBlack on 2006-09-14
hi
is there any way by which i can enable the mp3 support without using Synaptic manager, i can't use synaptic manager as i can't configure my modem to work in ubuntu.

i have a PCTel 688 HSP modem which is not supported.

or is there any way by which i can get my modem to work.

thanks. :cry:

---

### Post by oedipuss on 2006-09-14
I don't know about the modem, but for mp3s you could download the package from another pc / OS (I'm assuming you have access to one, since you obviously have access to the forums =D) 
Check here for the packages you'll need : [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I think gstreamer0.10-ffmpeg should do the trick. You can download single packages from [here]("http://packages.ubuntu.com/").

It could be somewhat difficult though, since you could be missing dependencies, and would need to install them one by one ... 

Well anyway, when you have the deb file, you can go back in ubuntu and install it with 'sudo dpkg -i *package.deb*' . At this point, dpkg should tell you what other package you're missing. 

There could be an easier method, though ..

---

### Post by helmut_hed on 2006-09-27
I've heard that the Smartlink drivers will work for your modem, and this post appears to confirm it:

[http://phep2.technion.ac.il/linmodems/archive-sixth/msg01584.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg01584.html)

---

