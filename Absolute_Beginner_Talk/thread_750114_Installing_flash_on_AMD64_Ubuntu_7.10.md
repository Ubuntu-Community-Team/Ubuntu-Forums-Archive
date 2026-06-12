---
title: "Installing flash on AMD64 Ubuntu 7.10"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-09
I've read a few tutorials and well, none of them have worked. First I tried this howto, [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash), but it didn't work. Then I found this thread, [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727). I installed the "flashplugin-nonfree" plugin from the synaptic manager, but when I open a webpage with flash on it it still tells me to "install missing plugins." Then when I try and install the plugin, it tells me that the plugin is already installed hahaha. I went back to the howto and it told me to type this

sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2

So I did, but then my terminal told me this: 

WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 5632B of archives.
After unpacking, 5353kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.


And with all these warnings about harmful code, can you really blame me? :D Ugh I hope someday I will finally be able to use linux without having to ask so many questions!!

---

### Post by Baby Boy on 2008-04-09
I'm experiencing the same problem. Hopefully, someone will know how to solve it.

---

### Post by gandaran on 2008-04-09
adobe has updated their flash to version 9.0.124, so the link to install flash is broken now.
for 32-bit user's, you can still install by downloading the adobe flash tarball and run the installer or just disable the ubufox firefox extension and go to a flash webpage and click install on that missing plugin message.
for 64-bit user's you'll have to wait until that link or package is fixed.

---

