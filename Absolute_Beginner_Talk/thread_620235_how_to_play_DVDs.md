---
title: "how to play DVDs"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-22
The computer shows that there is a DVD in my cd drive but when I try to play it using Totem , it does not work.  I also tried VLC player and that failed me as well.  Any ideas? Oh and I also did these steps to try to get it to work but it failed me. 

------------------------------------------------------------------------------------------------------------------------------
[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)
DVD are usually encrypted and therefore, due to legal reasons, Ubuntu Linux does not ship the package which decrypt DVD.

However, Ubuntu offers an easy way to get this package install. This tutorial will show which packages have to be installed in order to get most multimedia applications to run under Ubuntu.

The default movie player on Ubuntu is Totem, a Gnome movie player based on GStreamer or xine. As GStreamer is the default library used with Totem, this tutorial will be focused on GStreamer backend.

To get started with the codecs, we are going to install all the GStreamer library packages available on the repository:

$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse

From now on, you should be able to play any divx, non encrypted DVD and music.

In order to be able to play encrypted DVDs, we need to install libdvdcss2 package. As I said earlier, this package is not provided by Ubuntu for legal reasons. However, a script is supplied in order to easily install this package. This script is provided by libdvdread3 package.

Let's go back to the command line and, for people using Ubuntu Feisty 7.04 or Ubuntu Edgy 6.10, type:

$ sudo /usr/share/doc/libdvdread3/install-css.sh

People using releases prior to Edgy Eft, such as Ubuntu Dapper 6.04 will type:

$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh

People using Debian based distribution might have to use:

$ wget [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
$ sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

Now, libdvdcss2 is installed and that's it :), insert a DVD in your player, Totem should open up and the DVD start playing.
---------------------------------------------------------------------------------------------------------------------------

---

### Post by dward526 on 2007-11-22
Did you install the 'restricted' pack offered by Ubuntu, it tends to resolve most media issues

---

### Post by overdrank on 2007-11-22
To add to dward526
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Re.../WindowsCodecs](https://help.ubuntu.com/community/Re.../WindowsCodecs)
Good luck! :KS

---

### Post by Arthur Archnix on 2007-11-22
I followed those same instructions. My guess is they're wrong, but maybe it works for some people.

Anyway, just enable the mediabuntu repository and then install libdvdcss2.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
```

More information here:
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by kahram.yoon on 2007-11-23
thanks for the help DVDs are working now thanks.

---

### Post by Arthur Archnix on 2007-11-23
No problems.. you can help future uses by marking your threads as solved. Check out thread tools.

---

