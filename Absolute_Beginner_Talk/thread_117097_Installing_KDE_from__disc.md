---
title: "Installing KDE from  disc"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by Maccabee on 2006-01-14
I got two disks one with KDE 3.4 release in rpm files intended for updates for FC4 and second KDE 3.5 in tar bz format
I want to know whether it is possible to install it on my Ubuntu Breezy(5.10)
by converting rpms it into .deb using alien?
And is there any method for the tar bz?

---

### Post by curuxz on 2006-01-14
Ok firstly, how about just going into the repos' in synaptic?

Im asuming your a dial up user saving bandwidth. Well alien is the way to go in my view, simply type "sudo alien -cv NAME_OF_RPM" in a console and it should generate a deb file.  Then "sudo dpkg -i NAME_OF_DEB" and away you go. Bearing in mind tho it will take a while to convert all of kde and you will have to do it one package at a time, Its realy worth doing it through synaptic

---

### Post by Maccabee on 2006-01-15
Ok thats done for RPMs but after installing the stuff shall I make any changes inorder to boot directly into KDE and not to GNOME.

(I ve no net connection)

---

