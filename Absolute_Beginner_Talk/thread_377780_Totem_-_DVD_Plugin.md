---
title: "Totem - DVD Plugin?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by bks on 2007-03-06
I am unable to play DVD movies with Totem because it lacks the plugin.  Where do I get the plugin?

---

### Post by r4ik on 2007-03-06
Try,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)

From: [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Good luck !

---

### Post by bks on 2007-03-06
Thank you, this support community ROCKS!

---

### Post by endtroducing on 2007-03-06
Hi,

Enable universe en multiverse repositories.

sudo apt-get update

Get libdvdcss2. This is for encrypted dvd playback. Read the liscence it might not be allowed in your country.

wget [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb

Then

sudo apt-get install libdvdread3
sudo apt-get install libdvdplay0
sudo apt-get install libdvdnav4

E

---

### Post by bks on 2007-03-11
I followed your instructions and they worked great, but libdvdcssplay0 cannot be found. What now?




**EDIT: I gave it a try and it works! So I guess I don't need that last pkg. Thanks for the help!!

---

