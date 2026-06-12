---
title: "KTorrent wont work"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-05-31
Alright, I just finished installing KTorrent 2.1 for the second time using the synaptic package manager, and the program loads up and all, but it wont open any .torrent files! Anytime I try and have it load up a torrent, it says:

"An error occurred while loading the torrent. The torrent is probably corrupt or it is not a valid torrent file"

Okay, I know this isn't just the torrent, because any torrent from any tracker I open up gives me that same error. I've tried Demonoid, The Pirate Bay, IsoHunt, etc, and it gives me that same error. What is wrong?

---

### Post by xyrer on 2007-05-31
Are you using what version of ubuntu? and ktorrent is exactly what version?

---

### Post by Shadoweater12081980 on 2007-05-31
did you fully uninstall the old KTorrent ?

# sudo apt-get autoremove ktorrent

This will remove all the rubish that gets left behind with the old install including libraries which are not doing anything

Then install in the usual way

# sudo apt-get update
# sudo apt-get upgrade
# sudo apt-get install ktorrent

See how you go then

Hope this helps

---

### Post by Exershio on 2007-05-31
I'm doing that now Shadoweater, I'll let yuo know how it goes. Thanks!

---

### Post by Exershio on 2007-05-31
>_> I did exactly what you told me to and it still gives me this problem. I'm running the newest Xubuntu (Feisty I think)

---

### Post by anaconda on 2007-05-31
Does it work better if you first save the torrent file to your disk and then open it with ktorrent?

---

### Post by Exershio on 2007-05-31
Nope, I've tried that as well, and it still wont read any torrent files. I don't want to use BitTorrent because it isn't very featurefull, and Azureus is too much of a memory hog (I only have 256mb of ram).

Are there any other simple solutions?

---

### Post by fearpi on 2007-06-02
I get this same error message, but only on certain torrents. Where the torrent is doesn't seem to make a difference, nor does the filename.

---

### Post by forestpixie on 2007-06-02
I had some problems with Ktorrent - Downloading and installing the version from the Ktorrent website cleared them up - if you're getting version 2.1 with apt-get theversion from the site is 2.14.

Might help.

---

### Post by hyper_ch on 2007-06-02
Running ktorrent 2.1.4 from the feisty repos and it works fine...

---

### Post by forestpixie on 2007-06-02
Wasn't sure as mine shows 2.14 - but I know I got it elsewhere - and Exersio seems to be getting 2.1 from Synaptic?

---

