---
title: "Wifi &amp; mp3 codec issues"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by mj52730 on 2008-03-29
Hello. I am running Ubuntu 7.10 as a 2nd OS on my new Toshiba laptop. I just installed this & being quite new I am having trouble figuring this out. I have already gotten some info on using the ndiswrapper to use the windows driver for my wifi card (realtek rt8187b), but when I download the latest ndiswrapper, I can't figure out how to install it & if I did I don't know where to get the windows driver I can use. I get a bunch of errors in the terminal when I try to install the darn thing. Is there somewhere I can get some EXTREMELY detailed instructions on how to do this? 

Also, I can't play mpg or mp3 files for lack of codecs. I have gone into synaptic and checked the universe, restricted & multiverse options and when I try to open an mp3 with the media player, I get the "search for a suitable codec" box. I click search & get 1 on the list, "GStreamer extra plugins". I check the box next to that and the "Confirm installation of restricted software" box pops up, so I click confirm, & get this error:

*cannot install 'gstreamer0.10-plugins-ugly'* says that this application conflicts with other installed software, but doesn't tell me what software. tells me to go to synaptic to resolve but doesn't tell me how. Any ideas?

---

### Post by mj52730 on 2008-03-29
Well I thought trying to install vlc player might solve my mp3 issue but once again, I follow the instructions on how to install that TO THE LETTER & guess what? DOESN'T WORK! I've downloaded alot of software and followed the install instructions and I can't get 1 damn thing to install or work on this OS! In this instance, this is what the VLC instructions tell me to do:

   % sudo apt-get update
   % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

& this is the error I get:

matt@matt-laptop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-plugin-vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
  vlc-plugin-esd: Depends: vlc-nox but it is not going to be installed
E: Broken packages

**WTF?????**

---

### Post by bhold on 2008-03-29
This thread shows how I downloaded my realtek driver and installed with ndiswrapper...

[http://ubuntuforums.org/showthread.php?t=650066&highlight=bhold](http://ubuntuforums.org/showthread.php?t=650066&highlight=bhold)

At the realtek download site, search for RTL8187B then download, that should get the files you need.

As far as installation of ndiswrapper, I think all I did is Applications -> Add / Remove, search for ndiswrapper, and install.

As far as your codec questions, sorry, I can't help you much there. The entire codec thing in linux seems to me to be largely a matter of trial and error. I do know that some linux distributions come with a larger number of pre-installed codecs than ubuntu - linux mint is one that comes to mind.

---

### Post by Bubba64 on 2008-03-29
Here is a popular link with a list of codecs. 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Here is ubuntu wiki a great site for finding answers by using the search bar
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
This is a relative page to start on for downloads to enable your computing and media pleasure.

---

### Post by Ub1476 on 2008-03-29
#
Card: Trendnet TEW-424UB

    *
      Chipset: Realtek RTL8187B
    *
      usbid: (as reported by lsusb ) 0bda:8189
    *
      Driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")
    *
      Other: Works with WEP, have not tried other encryptions, using ndiswrapper from kernel 2.6.20 (Ubuntu)

[Ndiswrapper:Ubuntu help]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

You cannot install any codecs because you have broken packages. Try those commands:

```
sudo apt-get autoremove
sudo apt-get install -f
sudo dpkg -reconfigure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mj52730 on 2008-03-29
Thanks bhold, I used that link & thought I got my driver installed, but when checking for installed drivers here's what I get:

matt@matt-laptop:~$ sudo ndiswrapper -l
net8187b : driver installed
net887b : invalid driver!
matt@matt-laptop:~$ 

Plus I cannot figure out what to do now to configure the driver if it's there or how to find any evidence that the software is installed.

---

### Post by Ub1476 on 2008-03-29
You tried to follow the Ubuntu wiki (look at my above post)?

---

### Post by mj52730 on 2008-03-29
**ub1476-**

Tried entering those commands, still get the same resultwhen trying to install vlc after entering that stuff.

---

### Post by Bubba64 on 2008-03-29
I believe totem zine conflicts with gstreamer but there are other zine plugins that work.

---

### Post by bhold on 2008-03-30
> **mj52730 said:**
> Thanks bhold, I used that link & thought I got my driver installed, but when checking for installed drivers here's what I get:

matt@matt-laptop:~$ sudo ndiswrapper -l
net8187b : driver installed
net887b : invalid driver!
matt@matt-laptop:~$ 

Plus I cannot figure out what to do now to configure the driver if it's there or how to find any evidence that the software is installed.

mj52730, I recall running ndiswrapper -l but never got any errors. I am working from memory here because the system I had wireless working on under ndiswrapper is out of action due to HW problems. I would suggest the following:
1. On the chance you got a bad driver download file, download again and re-install.
2. Ub1476 posted a link with ndiswrapper trouble-shooting, give it a try.
3. If still no results you might try posting details in the Networking / Wireless forum.

---

