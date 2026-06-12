---
title: "Yet another DVD play back thread"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-15
Hi Guys,

I've tried following all the guides that I can find on various forums to get Totem Movie Player to play DVDs yet when I try to do so, I still get the error message 'An error occurred - The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I've tried all the various guides related to the installation of libdvdcss yet I still can't play DVDs.

What is the problem/what am I doing wrong?

Cheers :-)

---

### Post by tgm4883 on 2007-06-15
Did you follow this?

[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html)

---

### Post by mikeypc2006 on 2007-06-15
What are the 'Terminal' commands for step 1?

---

### Post by Bachstelze on 2007-06-15
[Where's the terminal ?](http://www.psychocats.net/ubuntu/terminal)

---

### Post by mikeypc2006 on 2007-06-15
Ok, but what are the specifc commands that I need to write in 'Terminal' to do step 1 in the first link posted?

I know where to find the Terminal and everything, I just need the specific commands!

---

### Post by John.Michael.Kane on 2007-06-15
Run this first
```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
```

This second
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Next run

```
sudo aptitude install libdvdcss2 totem-xine gxine libxine-extracodecs  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

If totem-xine does not play your movies you can try the below players

```
sudo aptitude install mplayer vlc
```

---

### Post by meborc on 2007-06-15
```
sudo gedit /etc/apt/sources.list
```
take the # off all the lines starting with deb...
save and close
```
sudo apt-get update
sudo apt-get install gxine libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```

edit: ahh... so fast :)

---

### Post by carloslosgrande on 2007-06-15
Hi Mikey, I just went to the link and saw this;
Playing DVDs

The movie players provided with Ubuntu are capable of reading DVDs that are not encrypted; encrypted DVD support is not available by default in Ubuntu due to legal restrictions surrounding the DVD format. However, it is possible to play encrypted DVDs on Ubuntu by installing some additional software.
[Caution] 	

In some countries it is possible that the use of some of the following software to play or copy DVDs is not permitted by law. Verify that you are within your rights in using it.

   1.

      Install the following packages from the &#8220;Universe&#8221; and &#8220;Multiverse&#8221; repositories (see Add Applications):
          *

            gxine
          *

            libdvdcss2
          *

            libdvdnav4
          *

            libdvdplay0
          *

            libdvdread3
   2.

      Click Applications &#8594; Accessories &#8594; Terminal and type the following into the screen which appears, followed by the Return key:

    >   sudo /usr/share/doc/libdvdread3/install-css.sh

   3.

      Press System &#8594; Preferences &#8594; Removable Drives and Media and click on the Multimedia tab.
   4.

      In the Command box under Video DVD Discs, type &#8220;gxine -S dvd:/&#8221; (without quotes) and then press Close.
   5.

      Insert a DVD disc into the DVD drive of your computer. It should play automatically in gxine. You can press the f key to watch the DVD full-screen.

The quote box has the command to enter,........ it begins with 'sudo'.......after you enter this it'll ask for your password. Enter it and after it finishes......go to the next step

---

### Post by ts51 on 2007-06-15
[http://www.getautomatix.com/](http://www.getautomatix.com/) 

I'm pretty sure this program, automatix, can do it for you.

---

### Post by Bachstelze on 2007-06-15
Yes, and it can also break your whole system. Please, please, *please* don't use it !

---

### Post by kelvin spratt on 2007-06-15
i use automatix never had a problem

---

### Post by simoneale on 2007-06-15
> **HymnToLife said:**
> Yes, and it can also break your whole system. Please, please, *please* don't use it !

I'll Vouch for that!!! :(

---

### Post by Ssj3_man on 2007-06-22
> **SD-Plissken said:**
> Run this first
```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
```

This second
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Next run

```
sudo aptitude install libdvdcss2 totem-xine gxine libxine-extracodecs  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

If totem-xine does not play your movies you can try the below players

```
sudo aptitude install mplayer vlc
```

this works  -VLC player part 
thanks man

---

