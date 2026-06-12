---
title: "hmm.."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by woodgod on 2007-03-05
I used that codeing line but it can't find gtstreamer0.10-pitfdll

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse \
gxine libxine-main1 libxine-extracodecs ogle ogle-gui gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good libdvdread3 flashplugin-nonfree ffmpeg lame faad sox mjpegtools

---

### Post by STREETURCHINE on 2007-03-05
have you enabled all your repositories.?

---

### Post by AndyCooll on 2007-03-05
Easiest way to install gstreamer is to open up Synaptic (System > Administration > Synaptic Package Manager) and do a search for gstreamer. Then select the good, bad and ugly packages.

:cool:

---

### Post by RomeReactor on 2007-03-05
Hi. Do you have Universe repositories enabled? if not, then open Synaptic (System-->Administration-->Synaptic Package Manager) and click on "Settings-->Repositories"; on the first tab, check all the boxes there, and press the Reload button. **gstreamer0.10-pitfdll** should now be available.

---

### Post by woodgod on 2007-03-05
still not there guys i had it installed on a previous installation of it with no worries ( about a week  or 2 ago)  now it can't find it even after enabeling all repositories

---

### Post by kittyhawk63 on 2007-03-05
> **woodgod said:**
> still not there guys i had it installed on a previous installation of it with no worries ( about a week  or 2 ago)  now it can't find it even after enabeling all repositories

Woodgod, have you done a recent update?
"sudo apt-get update" (do this in terminal-no quote marks)
I found gstream when I followed the aforemention guide from RomeReactor.

---

### Post by woodgod on 2007-03-05
ok thanks that fixed it kittyhawk

---

### Post by kittyhawk63 on 2007-03-05
> **woodgod said:**
> ok thanks that fixed it kittyhawk

Glad I could help.

---

