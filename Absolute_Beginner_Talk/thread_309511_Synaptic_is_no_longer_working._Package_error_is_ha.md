---
title: "Synaptic is no longer working. Package error is hanging it"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by HEMOglobina on 2006-11-29
Everytime I try to launch Synaptic this is what I get:

```
E: The package awcommon needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

I tried to run maya7 on my machine but I was not able to make it work. I guess awcommon somehow broke my synaptic.

Does anyone knows how could I fix it?
Thank you,
HEMOglobina

---

### Post by MasterOfDisaster on 2006-11-29
Does apt-get work?

If so, try 'apt-get remove awcommon', or 'aptitude remove awcommon' in the terminal.

---

### Post by HEMOglobina on 2006-11-29
Hello MasterOfDisaster.
This is what I typed at the terminal:
```
sudo apt-get remove awcommon
```
This is what I got back
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package awcommon needs to be reinstalled, but I can't find an archive for it.

```
Nothing gets removed...

Then I tried:
```
sudo aptitude remove awcommon
```
This is what I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  automatix2 gimp gimp-data gimp-python gnome-games gnome-games-data gnome-system-tools gnupg libgimp2.0 libgnomeprintui2.2-0 libgnomeprintui2.2-common 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libtotem-plparser1 tar totem 
  totem-mozilla totem-xine vino x11-common xbase-clients xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following packages will be REMOVED:
  awcommon 
0 packages upgraded, 0 newly installed, 1 to remove and 31 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Writing extended state information... Error!
E: I wasn't able to locate file for the maya7-0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

```
I'm not even able to install simple things like pear-package.
I hope there is a way to fix this.

Thank you for your help,
HEMOglobina

---

### Post by MasterOfDisaster on 2006-11-29
Try running 'sudo aptitude -f remove', then 'sudo dpkg --configure -a'.

I'm throwing out commands here, sorry.

---

### Post by ragingmon on 2007-05-29
I removed awcommon following this link >>[http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it](http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it)
read on the comments, especially the comment of chas.

hope it helps

---

### Post by vhof on 2007-12-12
I went to the directory where I installed the deb 
sudo dpkg -i _the_name_of_filename_.deb

Where _the_name_of_filename_.deb (in your case is *awcommon*.......)

---

