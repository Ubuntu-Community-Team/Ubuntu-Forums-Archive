---
title: "how do I get mp3's to play"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by nydadx1x on 2008-02-09
I have a computer I installed ubuntu 6.06 on about a year ago.  Through help from this forum I was able to play mp3 and avi files in movieplayer (totem).  For the life of me I can't find that information on here again.  Can anyone help?  Or is there a way to access my old posts on here?  Thanks for your time.

---

### Post by HappyFeet on 2008-02-09
here you go. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Haluci on 2008-02-09
Try installing the ubuntu restricted extras, by typing

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

This should enable mp3 playback support.

---

### Post by PmDematagoda on 2008-02-09
Open the Synaptic Package Manager, search for "gstreamer" and then install the required packages.

---

### Post by nydadx1x on 2008-02-09
*

      Ensure the relevant repositories are enabled. Click System &#8594; Administration &#8594; Synaptic Package Manager &#8594; Settings &#8594; Repositories and then click Add. Check the Community maintained (Universe) and Non-free (Multiverse) boxes, click Add. Close the Software Repository window, and click Reload in Synaptic Package Manager.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Quit out of Synaptic, then click Application &#8594; Accessories &#8594; Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

Ok, went to that page and did all of the above.  Mp3s and avi's still won't play.

---

### Post by nydadx1x on 2008-02-09
> **Haluci said:**
> Try installing the ubuntu restricted extras, by typing

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

This should enable mp3 playback support.
got this error message:

E: Couldn't find package ubuntu-restricted-extras

---

### Post by antisocialist on 2008-02-09
maybe you need a proprietary driver so sound will work?

go to sys>admin>res drivers manager and install everything there

if that dont work then go to add/remove
at the top make sure you choose all available applications
search for "ubuntu restricted extras"
install it
it should now work

---

### Post by nydadx1x on 2008-02-10
> **PmDematagoda said:**
> Open the Synaptic Package Manager, search for "gstreamer" and then install the required packages.

THAT DID IT!!!!  Thanks loads.

---

