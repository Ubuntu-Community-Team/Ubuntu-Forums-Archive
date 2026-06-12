---
title: "Newbie: Flash/Quicktime for Dapper Drake?"
date: 2007-02-14
forum: Apple PPC Users
---

### Post by nordic1 on 2007-02-14
I am brand new to Kubuntu and I am still working on getting the proper software installed. Is it possible to get Flash and Quicktime playback for Firefox running on a ruby iMac? I have searched previous posts and I have not had any luck. I have tried to install the mPlayer plug-in but the terminal window is mind-boggling for me. Any help in pointing me in the right direction and/or "hand-holding" would be greatly appreciated.

---

### Post by pay on 2007-02-14
Try gnash for flash.

---

### Post by beanworks on 2007-02-18
I see on other threads that gnash is on the backports repository for edgy elf, but is it available for dapper?  I have the backports repositories enabled on synaptec, but searching for gnash gets nothing.:(

---

### Post by loungepirateriot on 2007-02-23
For Quicktime support:

Open a noob's best friend, Synaptic Package Manager. 
(Found at System-->Administration-->Synaptic Package Manager)

Search for the following packages.
If they are not installed, click next to them and hit "apply"

mplayer 
mplayer-firefox
win32codecs
libquicktime
gstreamer ffmpeg
gstreamer gl
gstreamer plugin base
gstreamer plugin good
gstreamer plugin bad
gstreamer plugin ugly
gstreamer plugin bad multiverse
gstreamer plugin ugly multiverse

If you don't find any of the above, search the forums for how to add the canonical repository and the medibuntu reposistory.  These are not official Ubuntu repositories, but are commonly used.

Search for vlc plugin for firefox.
DO NOT INSTALL IT.
If it is already installed, uninstall it.
Mplayer plugin seems to work much better, especially for QT format, and vlc plugin will take priority over mplayer in firefox.
(For someone who wants to manually uninstall vlc plugin, it's in /usr/lib/firefox/plugins)

Now hit Alt+F2 add copy in the following:
> gksudo gedit /etc/mplayer/codecs.conf

In the menu go to Search-->Find
type in "ffsvq3" and hit ok
comment out the paragraph so it looks like this:
> #videocodec ffsvq3
#  info "FFmpeg Sorenson Video v3 (SVQ3)"
#  status working
#  fourcc SVQ3
#  driver ffmpeg
#  dll svq3
#  out YV12,I420,IYUV
save the document

and restart firefox!

HTH

---

### Post by 3rdalbum on 2007-02-24
> **loungepirateriot said:**
> For Quicktime support:

Open a noob's best friend, Synaptic Package Manager. 
(Found at System-->Administration-->Synaptic Package Manager)

Search for the following packages.
If they are not installed, click next to them and hit "apply"

mplayer 
mplayer-firefox
win32codecs

You can safely ignore most of loungepirateriot's post. The Commercial and Medibuntu repos are x86-only. Many of the packages he talks about are only available on x86, including win32codecs.

And I would recommend VLC for PowerPC users, as it does have some support for Windows Media formats.

---

