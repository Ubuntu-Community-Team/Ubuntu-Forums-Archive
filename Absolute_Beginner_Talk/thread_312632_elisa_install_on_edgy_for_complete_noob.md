---
title: "elisa install on edgy for complete noob"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by el tonae on 2006-12-04
I just upgraded to edgy yesterday and I'm trying to install elisa multimedia.  I haven't got far at all, owing mostly to the fact I have no idea what I'm doing.  I'm hoping any help with this will also help enlighten me on the general concept of repositories and synaptic and apt-get.

First I followed the steps on how to install elisa on edgy found here at elisa's wiki.  [https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy](https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy)

```
$ sudo apt-get install gstreamer0.10-plugins-bad \
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-alsa \
  gstreamer0.10-gnomevfs gstreamer0.10-pitfdll \
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse

```

After running this code in the terminal, I got the following error:

```

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-plugins-bad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer0.10-plugins-base
E: Package gstreamer0.10-plugins-bad has no installation candidate

```

I found a promising thread ([http://ubuntuforums.org/showthread.php?t=298969&highlight=elisa+install](http://ubuntuforums.org/showthread.php?t=298969&highlight=elisa+install))  in the Programming Talk section of this forum, but I'm afraid much of the suggestions went over my head.  Thus the post in Absolute Beginner Talk. :)

Specifically, it was suggested to install various packages in synaptic, however when I went to search for them, synaptic said "There is no matching application available."  I searched for gstreamer and libgstreamer0.10-dev and a couple others. So, I'm wondering if my repositories are not set up correctly...

Here's what my sources.list file looks like now after some modifications.

```

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free 

```

As far as I can tell I've enabled the entries that needed to be enabled.. Are there completely new entries I have to make?  Is there maybe a terminal command I have to run to reinitialize sources.list after I change it?

So I'm sure I'm just totally missing a pretty simple step.  Sorry I'm such a noob. :) Any suggestions would be much appreciated.  Thanks!

Tony

---

### Post by kvonb on 2006-12-04
Just a quick reply, try uncommenting the last two lines (the non-free ones), then type:

```
 sudo apt-get update
```

I don't know if you did that already, but just in case they didn't tell you to do that!

Then try the other stuff again
 and see what happens.
Regards, Kev :)

EDIT: Actually, if you are running Edgy you don't need to manually edit the sources.list, just run synaptic from the menu and go to Settings->Repositories and enable universe and multiverse in there.  Also you will need to type:

```
 sudo apt-get install build-essential
```

...before you can do ANY compiling at all.

I just looked at the instructions on the site you gave and they don't tell you any background info.

Just ask again if you have problems :)

---

### Post by el tonae on 2006-12-04
Thanks for the reply Kev.

It turns out I really did miss something pretty obvious.  I didn't realize that add/remove programs and synaptic are two different applications.

I've been putzing around in add/remove, which is why i could find any of these dependencies.  In any case, I found synaptic and after a quick search already found gstreamer.  Hopefully this will do the trick.  

If you don't mind, Kev, what does
```
sudo apt-get install build-essential
``` do and when should I run that command?

thanks again!

tony

---

### Post by kvonb on 2006-12-04
Hi,

The build-essential contains ALL the tools needed to compile source code on Ubuntu, sorry I must have had way too much coffee this morning as you will only need this if you are going to compile elisa from source code!  If you are installing the .deb packages you won't be needing all that extra guff although it may come in handy if you ever need to compile anything at a later date (if something asks you to do a "make" and "make install").  So you can safely ignore my "sudo apt-get install build-essential" line :)

The link you provided in your earlier post talks about compiling the latest version for "subversion", if you go that route then you will need the build-essential packages before starting those instructions.

Hope that makes sense :D

PS. I know what you mean about the add/remove progs thing, it is just a cut down version of Synaptic Package Manager which contains EVERY package that is available for Ubuntu!  One thing about Linux/Ubuntu is that there are usually several ways of doing the same thing, ie apt-get is the same as Synaptic, just a text version.

Regards, Kev  :)

---

### Post by el tonae on 2006-12-05
HOLY CRAP IT WORKS!  but boy is it slow.

Turns out there's a rendering engine this application needs called Pigment that must be complied and installed w/ all dependencies before you can even think about elisa.  Oh, and both elisa and pigment needed compiling, so you your tip was essential.  Thanks. :)

After a few minutes of playing with it though it's apparent my computer's too slow or elisa is too young (still in development)

I think I'll try freevo next and see how that stacks up.

tony

---

### Post by RAOF on 2006-12-05
Elisa is definitely too young.  There's a reason there aren't any packages for it on the homepage :).

---

