---
title: "Ubuntu Edgy After Installation Guide"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by saygin on 2007-02-15
hi, I am a new linux user too, and I know that after first time installation, people don't know what to do next. So I prepared this for newbies. I hope it helps. (if there are mistakes although I've checked twice, please warn me!)

----------------------------------------------------------

First, make sure you have added the universe and multiverse repositories (Click System->Administration->Synaptic... after that, Settings->Repositories. In the Ubuntu 6.10 tab, click all the checkboxes). I want to write my additional repositories. To see and add them, Open Synaptic, Settings->Repositories
I have selected all the check-box in the "Ubuntu 6.10" tab, and then, my repos written in "Third Party" tab are:
"deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all"
"deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main main-all"
"deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all"

first, installed nvidia driver.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

then, because I still have Windows and NTFS partition disk, we need to read and write on it. So, install NTFS3G.
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

We always need to zip and unzip rar files, and we need to install rar and unrar packages. To deo this, in Synaptic Package mark for installation  the packages "rar" and "unrar" (unrar-nonfree) and click apply.

Now, we want to listen MP3s or play DivX files right? Therefore, I prefer to use Xine for movies, and I use Rhythmbox for MP3s although I don't like it much. Open a terminal and copy and paste the code.
"sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui"
after installing them, click Applications->Add/Remove... and type "Xine" in searchbox. If Xine Media Player is not installed, install it. (In fact by the code above, you installed gxine, however gxine is not as good as Xine itself sometimes, so I suggest Xine itself.)

although we installed the packages, there is no support for Windows Media Codecs and Real Media. (Wmv,Wma and Rm,Ra...) For this, we are going to dowload the codec pack from Debian repositories. Open a terminal and write the codes below:
"wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb"
"sudo dpkg -i w32codecs_20061022-0.0_i386.deb"
There is a useful information for this on Ubuntu Documentation:
   
Note: The w32codecs package from the Debian repositories have been tested and work with Ubuntu systems however not all Debian packages will work correctly with Ubuntu, so for your safety do not add Debian repositories to your /etc/apt/sources.list

WMV files encoded with DRM (Digital Rights Management) cannot be played with this package.

If you are experiencing choppy audio when playing WMV files, try the fix described here. [http://ubuntuforums.org/showpost.php?p=136306&postcount=2](http://ubuntuforums.org/showpost.php?p=136306&postcount=2)

If you still cannot play WMV files after installing w32codecs, try the method suggested here. [http://ubuntuforums.org/showthread.php?p=1649012](http://ubuntuforums.org/showthread.php?p=1649012) " (I needed to do this)

And last, we need to install flash player on firefox. I guess firefox can install it when you go to a site with flash. If it doesn't, do the following.
First thing, we download the tar.gz version of it from adobe's web site, and untar it.Go to that folder, then as it tells in the instructions, we write "./flashplayer-installer" in the terminal. It will ask you to close all browsers first, so do it. After that it will ask you the path of firefox. It was "/usr/lib/firefox" for me. Check it. then it will be ready!

And now, in case you may need to compile a program in the future, we will install compilers. Open a terminal and just write "sudo apt-get install build-essential". This command will install the packages to compile stuff.

I also want to add some extra fonts like "Times New Roman" to my linux. So, only thing I need to add is msttcorefonts package. You can add it by using Synaptic or open a terminal and write "sudo apt-get install msttcorefonts".

---

### Post by dbbolton on 2007-02-16
good job. you might repost this or have it moved to the howto section though ;)

---

