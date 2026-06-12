---
title: "multimedia codes"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-13
Hi 

had to reinstall ubuntu last nite.
i'm following teh ubuntuguide (13 - i don't know if it is the number, but i'm already getting unstuck) on 'How to Setup Multimedia Codecs'

This is the transcript on two i have chosen:

sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame

 and

sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


Can someone explain why it couldn't fine gstreamer? and secondly, what it means w32 has no installation candidate?

and moreover what i do to resolve the issues. I imagine i could have problems with the rest of the codecs too. The first one installed but these two haven't; and am i right in thinking all are important?

thank you for your response,

sophtpaw

---

### Post by ubuntu_demon on 2005-07-13
you should do this first : 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

This will solve your problem :)

---

### Post by sophtpaw on 2005-07-13
[QUOTE=ubuntu_demon]you should do this first : 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

This will solve your problem :)[/QUOTE]


HI, yes, i have installed extra repositories. How many are there exactly? and does one have to have each and every single one of them for things like installing Multimedia Codecs to work?

I have 16, 271  packages in my Synaptics status bar

your response appreciated


sophtpaw

---

### Post by Knome_fan on 2005-07-13
Could you post your sources.list?

If you did indeed take the one from ubuntuguide you shouldn't have these problems.
gstreamer0.8-lame is in hoary multiverse if I rember correctly and w32codecs should be in the hoary-extras backports repository.

---

### Post by sophtpaw on 2005-07-13
[QUOTE=Knome_fan]Could you post your sources.list?

If you did indeed take the one from ubuntuguide you shouldn't have these problems.
gstreamer0.8-lame is in hoary multiverse if I rember correctly and w32codecs should be in the hoary-extras backports repository.[/QUOTE]


Well spotted!

indeed i had only changed from the list what was in the list. i.e. backports did not initially show in the list, therefore i did not add that. However, i have now taken everything from section 4 of the U-guide and pasted it in the list, saved and now i have a bigger repository showing in Synaptic. In other words i have the necessary pool for w32codecs to be installed.

Thx for pointing out my inaccuracy,

regards,

sophtpaw

---

