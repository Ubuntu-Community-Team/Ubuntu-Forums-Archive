---
title: "Gimp 2.8 network saving bug???"
date: 2012-11-02
forum: Art &amp; Design
---

### Post by artspace on 2012-11-02
I currently upgraded to Ubuntu 12.04.1 64bit and installed Gimp 2.8.2.

Then I found a serious problem. I use NAS to store all my work files and access them via Samba file sharing, but when I try to save a file over the network in Gimp 2.8, I get message telling me the location is not found. I can open files via gvfs without any problem but whenever I want to save or save as a file the error message pops.

I did try some workaround, such as reopened the gvfs folder and reassign the path every time when saving a file. Gimp did save file to the NAS in this way; however, the saved file was corrupted and showed only an empty layer.

BTW, my Ubuntu 12.04.1 was clean installed and the Gimp 2.8 was installed using the otto-kesselgulasch ppa. And this problem does NOT occur in Gimp 2.6.12 which is the default version provided by Precise Pangolin.

Does anyone meet the same problem? I googled for hours but couldn't find any discussion on this issue...

---

### Post by artspace on 2012-11-05
Just tried Ubuntu 12.10 + Gimp 2.8.2 with a live CD (64 bit), and the exactly same problem happened, too.

Gimp 2.8.2 is the default version in Ubuntu 12.10 so I installed it directly through the Software Center.

I've reported this bug to GNOME Bugzilla.

---

