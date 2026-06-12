---
title: "Ubuntu setup guide for new users"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2007-08-13
For new users to Ubuntu, this may be of some assistance when trying to configure Ubuntu:

[B]Make the fonts in Ubuntu appear similar to the Windows XP fonts (less strain on the eyes)
[/B]
Install msttcorefonts (System>Administration>Synaptic Package Manager> search for msttcorefonts and install these.

Next, download the xml files and save them to your desktop: xml files

Open a terminal: Applications>Accessories>Terminal

cd Desktop sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Remember to reboot for the settings to take effect.

[B]Multimedia codecs
[/B]
Something which caused anguish in the past has been made simple.

Click on Applications>Add/Remove Applications>search for Ubuntu Restricted extras, install these. You will now have most the of the codecs needed to play streaming video and audio. In the same application, search for and install the Flash plugin. Search for and install the VLC Media Player, I found this the most useful and reliable media player to use, especially for streaming.

[B]Firefox media streaming
[/B]
Search for and install the media player connectivity add on in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

When it’s installed use the wizard and configure VLC to play all streaming video.

*Note I encountered a problem which resulted in degraded quality when I stream video from Yahoo using VLC, fortunately I found a fix; this may or may not work for you. When you open a link to streaming content from Yahoo, click on ‘Video Quality’, the option next to ‘help’ (your current preference / detected streaming rate is displayed). Mine is 300k. Click on 100k, then ’select’, an advert may reappear, when it’s finished, click on ‘Video Quality’ again and select your original settin (mine was 300k so I clicked it again), then ’select’. When you click on the small ‘play button’ the quality should be greatly improved.

[B]Mount Windows and enable write access to the Windows partition (for users dual booting between Windows XP and Ubuntu).
[/B]
Open a terminal Applications>Accessories>Terminal:

sudo mkdir /media/windows

Still in the terminal, Back up your disk configuration file:

sudo cp /etc/fstab /etc/fstab_backup sudo gedit /etc/fstab

In the text editor, append the following line at the end of the file:

/dev/hda1 /media/windows ntfs umask=0222 0 0

This is taken from the Ubuntu documentation [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

The instructions indicate they are for Edgy 6.10, but they work fine in Feisty 7.04.

Next, click on System>Administration>Synaptic Package Manager> search for and install NTFS CONFIG (an application which enable write access to the Windows partition).

When NTFS CONFIG is installed, click on Applications>System Tools>NTFS configuration tool, check ‘Enable write support for internal device’, if you share Windows and Ubuntu on the same hard drive.

This basic guide should help to set you up with some minor, but important features, made a lot easier with Ubuntu Feisty 7.04. More to follow shortly.

Sources:

[www.ubuntu.com](www.ubuntu.com)

[www.ubuntuforums.org](www.ubuntuforums.org)

For addtional info on setting up Realplayer and desktop widgets check out this link:
[http://opensourceroolz.wordpress.com/](http://opensourceroolz.wordpress.com/)

---

### Post by rufi_dukes on 2007-08-13
i tried to get the fonts by typing what you suggest:
"cd Desktop sudo tar xvjpf fontconfig.tbz -C /etc/fonts/"

and i got this:

"tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information."

thx for posting the routine,
rufus

---

### Post by msingletary on 2007-08-15
Where do you "download the xml files" so that they can be saved to the desktop and extracted/installed as instructed?

---

### Post by Michaelt74 on 2007-08-19
Here's the link, sorry!

[http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)

---

### Post by juamez. on 2007-10-13
Also: why not use apt-get install ntfs-3g? Since this is afterall included in the universal ubuntu repo and has reached version 1.0 ...

---

### Post by funrider on 2007-10-13
good thread. but you should post it in the "how-to" forum

---

