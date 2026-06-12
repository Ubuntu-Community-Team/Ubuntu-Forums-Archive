---
title: "[SOLVED] Updates won't download"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-09-09
After reinstalling Ubuntu and updating it, there are 15 updates left which I can't download. Here is the message I get:

> W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.04+20070601_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.04+20070601_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007f-0ubuntu0.7.4_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007f-0ubuntu0.7.4_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu4_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.0.2-1ubuntu4_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.6.0debian1-5ubuntu2.1_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.6.0debian1-5ubuntu2.1_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.23_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.59.23_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_7.2_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_7.2_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.0.2-1ubuntu4_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.0.2-1ubuntu4_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_1.0.2-1ubuntu4_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-1-utils_1.0.2-1ubuntu4_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.5.2-3ubuntu8_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_6.5.2-3ubuntu8_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_6.5.2-3ubuntu8_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_6.5.2-3ubuntu8_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/b/bughelper/python-launchpad-bugs_0.1.13.2_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/b/bughelper/python-launchpad-bugs_0.1.13.2_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.23_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.59.23_all.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_6.5.2-3ubuntu8_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_6.5.2-3ubuntu8_amd64.deb)
  404 Not Found


W: Failed to fetch [http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_6.5.2-3ubuntu8_amd64.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_6.5.2-3ubuntu8_amd64.deb)
  404 Not Found




How do I download these?

---

### Post by Vixis on 2007-09-09
Try links without rs.
like: 
[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)

---

### Post by lioninthesky on 2007-09-09
Is the 'rs' portion of the URL being referenced in your apt sources file (/etc/apt/sources.list)?  If so, you may want to remove all instances of it.  

[http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)

Works fine as:

[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)

Something is referencing the 'rs' portion of the URL in order to grab those packages.  My suggestion would be to start by taking a look at your sources.list file.

---

### Post by swoll1980 on 2007-09-09
I smell Automatix2 in here it reaks

---

### Post by Baby Boy on 2007-09-09
> **lioninthesky said:**
> Is the 'rs' portion of the URL being referenced in your apt sources file (/etc/apt/sources.list)?  If so, you may want to remove all instances of it.  

[http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://rs.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)

Works fine as:

[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.04+20070601_all.deb)

Something is referencing the 'rs' portion of the URL in order to grab those packages.  My suggestion would be to start by taking a look at your sources.list file.
It turns out it was a lot simpler than that. In the *Software Sources* menu, *Download from* option was set to my country's server. When I set it to *Main Server*, the updates were downloaded and installed.

Thanks for that *etc/apt/sources.list*  tip lioninthesky :).

---

