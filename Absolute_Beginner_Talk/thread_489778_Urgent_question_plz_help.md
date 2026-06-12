---
title: "Urgent question plz help"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-07-01
I installed ubuntu on my new machine and currently dont have internet on it, however I'd like to play music in proprietary format. Is there a way to copy the codecs from a machine with internet?

---

### Post by moore.bryan on 2007-07-01
[I]what ubuntu are you running?  depending, you could just go to [packages.ubuntu.com]("http://packages.ubuntu.com") on the internet connected machine and download the "laundry list" as debs and then install them locally...
[/I]gstreamer0.10-pitfdll
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gxine
libxine-main1
libxine-extracodecs
ogle
ogle-gui

---

### Post by KIAaze on 2007-07-01
Everything except downloads can be done offline. So if you can download the necessary files with another PC and transfer them to your own, there should be no problem.

If you just want to install the most common proprietary codecs like in this tutorial here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")
it's actually quite easy since it only involves installing packages.

_1)If the other PC uses Windows:_
Go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and search&download the following packages:
> ubuntu-restricted-extras
libxine-extracodecs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-pitfdll
w32codecs

(after a package search, click on the link corresponding to your distro, then scroll down and click on the link corresponding to your processor (amd64,i386 or PowerPC))

You should get a bunch of .deb files this way.

Transfer them to your PC and then install them by doing:
```
sudo dpkg --install xxx.deb
```

_2)If the other PC uses GNU/Linux:_
This makes it easier. :)
Open synaptic on your PC, select all those packages for installation:
> ubuntu-restricted-extras
libxine-extracodecs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-pitfdll
w32codecs

Click on "File->Generate package download script".
Transfer the saved script to the other PC and run it there.
(ex: If saved as "download_script.sh", run the command "./download_script.sh". (double-click in the GUI should also work. ;) ))

The script should do all the downloads for you. I think it does it where it is, so it's better to place it in it's own folder before running it.
Transfer all the .debs to your PC.
Open synaptic.
Click on "File->Add downloaded packages".

(So, it's about the same as before except that everything is downloaded automatically by the script. :D )

If you need to install things from source (.tar.gz) or other, it's the same.
Download, transfer, do the rest on your PC.

---

