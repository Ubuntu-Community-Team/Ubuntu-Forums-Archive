---
title: "which Automaix download for 7.10"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-10-31
I need to install Automatix, but I am given two choices.  Which one do I choose?

Ubuntu 7.10 (Gutsy AMD64)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb)

OR

Ubuntu 7.10 (Gutsy i386)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb)

---

### Post by overdrank on 2007-10-31
> **ammmom said:**
> I need to install Automatix, but I am given two choices.  Which one do I choose?

Ubuntu 7.10 (Gutsy AMD64)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb)

OR

Ubuntu 7.10 (Gutsy i386)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb)

Hi and I would recommend neither but with that said what is the architecture that you installed  if in doubt always choose i386. :KS

---

### Post by taurus on 2007-10-31
You don't need it because you can get all your codecs from here, [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by lfaraone on 2007-10-31
Please, please, please do not use automatix.
Its use is unsupported, and it may break your box.

---

### Post by ammmom on 2007-10-31
Okay, thanks.  It was just suggested once, when I asked a question from here before.  Good to know.

---

### Post by poision_heart on 2007-10-31
Hi if no automatix then how to install multimedia codec?How abt easyubuntu?Well libxine is better or gstreamer?Pls guide

---

### Post by Maestro23 on 2007-10-31
> **poision_heart said:**
> Hi if no automatix then how to install multimedia codec?How abt easyubuntu?Well libxine is better or gstreamer?Pls guide

Please read taurus' post.

---

### Post by oldos2er on 2007-10-31
See [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to add this repository to your sources.

 Then in a terminal type "sudo aptitude install ubuntu-restricted-extras libdvdcss2"

---

### Post by poision_heart on 2007-10-31
Thanks for help.Do i need to add repositories in synaptic?

---

### Post by Maestro23 on 2007-10-31
> **poision_heart said:**
> Thanks for help.Do i need to add repositories in synaptic?

The link tells you everything you need to do.

---

### Post by stchman on 2007-10-31
> **ammmom said:**
> I need to install Automatix, but I am given two choices.  Which one do I choose?

Ubuntu 7.10 (Gutsy AMD64)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-amd64/automatix2_2.0.1-7.10gutsy_amd64.deb)

OR

Ubuntu 7.10 (Gutsy i386)
[http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb)

You don't need Automatix to do stuff.  Just use the package manager.

What are you wanting to do with Automatix?  If you want mp3, mpeg2, mpeg4, etc use this line:

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

```

That will take care of it for you.

---

