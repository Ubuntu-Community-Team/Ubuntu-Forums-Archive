---
title: "Video Codecs Have Quit Working!"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-10-31
I'm running Gusty 64-bit and I'm having problems with the gstreamer ugly set of plugins.  I installed this package via synaptic.  I should be able to play divx and flv files directly in totem, but every time I try to open a divx file or a flv file, I get the following error message:

Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies

Can anybody tell me what's going on here, and how I can fix it?  

Thanks,

Helixed

---

### Post by amtnbiker16 on 2007-10-31
i used the add/remove applications program for codecs
you might try that

---

### Post by santiagoward2000 on 2007-10-31
> **helixed said:**
> I'm running Gusty 64-bit and I'm having problems with the gstreamer ugly set of plugins.  I installed this package via synaptic.  I should be able to play divx and flv files directly in totem, but every time I try to open a divx file or a flv file, I get the following error message:

Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies

Can anybody tell me what's going on here, and how I can fix it?  

Thanks,

Helixed

I'm not sure about this, but does Ubuntu come with Totem for Gstreamer? Xubuntu comes with Totem for Xine, it took me some time before I realized that.

---

### Post by helixed on 2007-10-31
I did try using add/remove, and it says the codecs are installed.  There's an xine extra plugin set, but it's not a 64 bit package.  Regardless, the videos don't work in VLC either, so it's not just totem.

Santiagoward, Ubuntu comes with the Gstreamer good package installed, but I need the ugly set, which is the restricted codecs.

Thanks,

Helixed

---

### Post by helixed on 2007-11-04
Any help?

---

### Post by helixed on 2007-11-05
Okay, I've just spent a ton of time and I finally got this to work.  Hopefully this might help somebody else out.  In the Medibuntu documentation, I used the following lines of code for 64-bit Gusty:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_amd64.deb

wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu1_amd64.deb)
sudo dpkg -i w64codecs_20061203-0medibuntu1_amd64.deb

Totem still won't play a DVD, but at least now VLC will.  I don't know how the other codecs work;  I haven't tested them yet.

Helixed

---

