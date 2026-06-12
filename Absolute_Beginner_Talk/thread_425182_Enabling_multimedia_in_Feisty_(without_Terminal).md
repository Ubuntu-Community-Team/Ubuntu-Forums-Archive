---
title: "Enabling multimedia in Feisty (without Terminal)"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Road King on 2007-04-27
While Ubuntu isn't Windows, it's getting closer in ease of use.  
But most advice given is still like that given in the early days of 
Windows, when experienced MS-DOS users told newbies how to do 
everything at the DOS command line.  In the spirit of encouraging 
the use of Linux on the desktop, I offer this alternative no-
Terminal method of "enabling multimedia in Feisty" for new Linux 
users.  This should achieve the same end as in the same subject
sticky post, but without having to use the command line.

In Firefox, go to this URL to download a key file:

[http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)

In the Firefox File menu, select Save Page As... and save the 
file to your home directory or a subfolder of that named Keys.
(if you're doing this from a post on a website or forum, you can
just right-click on the link above and select "Save Link As...")

In the Ubuntu Applications menu, select Add/Remove Applications.

In the Add/Remove Applications window, click the Preferences button.

On the Ubuntu Software tab in the Software Sources window, check 
the first four blocks for repositories.  Unless you're programming, 
leave the Source code block unchecked.

On the Third-Party tab, click the Add button and for the APT line, 
enter: deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
and click the Add Source button.

Click the Add button again and for the APT line enter:
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
and click the Add Source button.

On the Authentication tab, click the Import Key File... button.
Browse to the medibuntu-key.gpg file you downloaded in Firefox, 
highlight it, and click on the OK button.

Click the Close button in the Software Sources window.  You'll 
get a window saying your software information is out of date.
Click the Reload button in that window.  Don't be surprised if
you get a response the medibuntu repository is out of service
and will be ignored.  You'll have to reload later.  You can do 
that with the Reload button of the Synaptic Package Manager,
which is accessed under Administration, in the Ubuntu System menu.

The first thing you'll want to install in Add/Remove Applications is
the "Ubuntu restricted extras" in the "Other" category.  Check it and
click the "Apply" button.  This will install:
sun-java6.plugin
sun-java6-bin (Sun Java 6 Web Start in Add/Remove Applications)
sun-java6-jre
flashplugin-nonfree (Macromedia Flash plugin in Add/Remove Applications)
liba52.0.7.4
libdvdread3
libid3tag0
libmad0
libmpeg2.4
libsidplay1
gstreamer0.10plugins-ugly (GStreamer extra plugins in Add/Remove Applications)
gstreamer0.10plugins-ugly-multiverse
cabextract
liblame0
mmttcorefonts (Microsoft Core Fonts in Add/Remove Applications)

Next, select the "Sound & Video" category in Add/Remove Applications
and check the following packages:
GStreamer ffmpeg video plugin (gstreamer0.10-ffmpeg)
GStreamer plugins for mms, wavpack, quicktime, musepack (gstreamer0.10-plugins-bad)
GStreamer plugins for aac, xvid, mpeg2, faad (gstreamer0.10-plugins-bad-multiverse)
Click the Apply button to install them, then click OK to close 
the Add/Remove Applications window.

There are some things you'll want to install not in Add/Remove Applications.
For these, launch the Synaptic Package Manager under Administration in the
Ubuntu System menu.

First, do a Search for pitfdll.  Then click on the check box next to 
gstreamer0.10-pitfdll (or whatever the latest version is) and chose 
Mark for Installation.

Next, do a Search for medibuntu.  You'll first need to ensure the 
repositories were loaded when not out of service (see above).  
Mark libdvdcss2 (or the latest version) and w32codecs for installation, 
then click the Apply button.  When installation is done, close the 
Synaptic Package Manager Windows.

You can also use Add/Remove Applications to install the X.Org accelerated 
Nvidia or ATI video drivers.  Search for NVIDIA or ATI in the System Tools
category.  Pay attention to the note in the NVIDIA description about the
command you use in Terminal to enable the driver.  Then restart GNOME 
with the Ctrl-Alt-Backspace keyboard combination.  Worked for me.

---

### Post by az on 2007-04-27
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Bachstelze on 2007-04-27
Is that anothe crappy "Just Works" thingie that, in fact, breaks more often than not ? We've had enough of them.

---

### Post by compiledkernel on 2007-04-27
HymnToLife - the link or the OP? 

Road King - I felt that Adamant1988's sticky thread was pretty easily accomplished 

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by Bachstelze on 2007-04-27
Hmm, in fact it seems like somebody just find out that he/she could add repos in Synaptic :p

---

### Post by Road King on 2007-04-27
Considering the technical bent of the audience, I'm not surprised at the replies to my post.

HymnToLife writes:
> Is that anothe crappy "Just Works" thingie that, in fact, breaks more often than not ? We've had enough of them.

and compiledkernel asks:
> HymnToLife - the link or the OP? 

I read this as HTL preferring to manually type in commands and edit configuration files, rather than having software do that for him.  That's a reasonable position.

HymnToLife adds:
> Hmm, in fact it seems like somebody just find out that he/she could add repos in Synaptic

HTL, I'm not surprised you missed the point, given your perspective... and I don't mean that in a denigrating way. Actually, one of the points of my post is you DON'T have to go into Synaptic to add repos.  Add/Remove Applications' Preferences brings up only that part of it you need.

compiledkernel also wrote:
> Road King - I felt that Adamant1988's sticky thread was pretty easily accomplished

compiledkernel, I don't disagree with that, from a technical perspective.  The question is whether you want the use of desktop linux to expand.  Do you want its use reserved to only those who are technically astute, or are willing to become so by learning console commands and manual editing of configuration files?  

Given the Ubuntu team expended resources to create a tool that not only reduces the need for that knowledge, but that of using SPM as well, tells me they thought a less technical way of accomplishing these tasks was worth it.  All I did was outline how to use that tool as an alternative.

---

