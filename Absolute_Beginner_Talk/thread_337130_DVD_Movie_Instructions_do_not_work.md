---
title: "DVD Movie Instructions do not work"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by deejoshy on 2007-01-12
Hi,

I have installed Ubuntu and everything works fine except trying to watch a DVD.  I followed these instructions and got no errors:

1.  install the libdvdread3 package
2.  download and run install-css.sh

However, no matter what DVD movie I put in I still an error message.  Here is the one I got for my "The Sound of Music"  DVD

Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".


Here is the message I get if I try to play an .AVI movie:

Totem could not play 'file:///media/cdrom0/????/????.avi'.
You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

Any hints as to how I can finally watch a DVD?  ](*,) 

Thank you.

Davito
Washington, DC

---

### Post by orb9220 on 2007-01-12
libdvdread3 package is in synaptic package manger and does not require 
2. download and run install-css.sh.
also you will need the libs for css and ? I forget all. You can search in synaptic using dvd as search term.
or
you are not getting the right info.
The easy method is to use automatix since it will allow you to install all the video and audio codecs you need. Plus it has alot of other programs you might want.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by obsidion on 2007-01-12
>Hi,

>I have installed Ubuntu and everything works fine except trying to watch a DVD.  I followed these >instructions and got no errors:

>1.  install the libdvdread3 package
>2.  download and run install-css.sh

>However, no matter what DVD movie I put in I still an error message.  Here is the one I got for my "The >Sound of Music"  DVD

>Totem could not play 'dvd:///media/cdrom0'.
>No URI handler implemented for "dvd".


>Here is the message I get if I try to play an .AVI movie:

>Totem could not play 'file:///media/cdrom0/????/????.avi'.
>You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

>Any hints as to how I can finally watch a DVD?  ](*,) 

  For the avi install aviplayer, do a search in synaptic for avi and install most of the avifile stuff, you may also need the w32 codecs.
  The best and fastest with the least hassle that I have found to play dvds is vlc.


I added 
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main

to my sources.list in order to get the codecs.

---

### Post by deejoshy on 2007-01-15
Thank you all.  The Automatix site is what did the trick.  At last, I can watch my new dvd of The Sound of Music, which I got for Christmas.

Linux  rocks.

David  :D

---

### Post by TrikkeDaddy on 2007-01-18
DVD works now! One thing, the dvd runs a bit slow and stops a bit.  Is this because of memory?

---

