---
title: "multimedia"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by kwlam on 2006-10-04
I am using ubuntu 5.04. I cannot play vcd, or mp3. I think I need the codec. I cannot use wget,etc in my computer and I can only use http. What software or package do I need to download to enable the multimedia. How to install after I download the software? With synaptic package manager?
Thanks.

---

### Post by Kateikyoushi on 2006-10-04
You need to add the multiverse, universe repository in synaptic >> settings >> repository.


Then

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

```

[More help here.]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs")

---

### Post by davmac on 2006-10-04
There are many ways of solving this, but I found the easiest was to use EasyUbuntu. You can download it and find out more at [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

As you would expect from something called EasyUbuntu, it is not too difficult and the instructions are very good.

Hope this helps,

Dave Mac

---

### Post by kwlam on 2006-10-04
My problem is that I cannot use update manager like windows update. Therefore, I need to download the necessary programme and install myself. 
Can I just download the codec and install myself? For example, I use mandriva before. I need to download the java, flashplayer etc. and them run the rpm or the tar, etc.
When I use mandriva, I download xine and it contained all the rpm,  including the codec. However, I have downloaded and installed realplayer 10 gold but I still cannot play the vcd and mp3.
How to do it in Ubuntu?
Thanks.

---

### Post by davmac on 2006-10-04
If you're going to download something yourself then you need to find the .deb file. Then open up a terminal, navigate to the relevant directory and type "sudo dpkg -i thepackagename.deb"

I thought that synaptic, apt-get and wget all use http protocol so would have thought you'd be OK just installing with synaptic. Did this cause a problem when you tried it?

Dave Mac

---

### Post by Nhatz on 2006-10-04
yo dude... try this...
for mp3 playback use xmms and for mpg playback use xine..
you can get it and its dependecies here.. [http://packages.ubuntu.org](http://packages.ubuntu.org)..... chow! hehehe. hope this will solve your problem

---

### Post by Nhatz on 2006-10-04
oops....! it's [http://packages.ubuntulinux.org](http://packages.ubuntulinux.org), hehehehe my bad... chow!

---

