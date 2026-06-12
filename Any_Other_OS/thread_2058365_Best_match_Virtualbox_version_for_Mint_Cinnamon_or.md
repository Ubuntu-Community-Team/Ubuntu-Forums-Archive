---
title: "Best match Virtualbox version for Mint Cinnamon or Mate 64 bit"
date: 2012-09-15
forum: Any Other OS
---

### Post by afz12 on 2012-09-15
I have Mint running on my second notebook and I quite like Mate and Cinnamon versions. However, Oracle doesn't supply a Virtualbox version specifically for Mate. Is there a "best match" version that would supply most of Virtualbox functionality, if not all of it? I suspect Mate's core is possibly close to Ubuntu 12.04, as it is fairly recent and differs mainly in its front end and mix of packaged software but does anyone have a better guess than I? Any suggestions appreciated, I'll try them out and report back.

---

### Post by Perfect Storm on 2012-09-15
Moved to Other OS/Distro Talk.

---

### Post by Habitual on 2012-09-15
[http://download.virtualbox.org/virtualbox/4.2.0/virtualbox-4.2_4.2.0-80737~Ubuntu~precise_i386.deb]("http://download.virtualbox.org/virtualbox/4.2.0/virtualbox-4.2_4.2.0-80737%7EUbuntu%7Eprecise_i386.deb")
should do it for ya.

and don't forget [http://download.virtualbox.org/virtualbox/4.2.0/Oracle_VM_VirtualBox_Extension_Pack-4.2.0-80737.vbox-extpack](http://download.virtualbox.org/virtualbox/4.2.0/Oracle_VM_VirtualBox_Extension_Pack-4.2.0-80737.vbox-extpack)

Edited the ExtPack link...
[]("http://download.virtualbox.org/virtualbox/4.2.0/virtualbox-4.2_4.2.0-80737%7EUbuntu%7Eprecise_amd64.deb")

---

### Post by afz12 on 2012-09-15
Thanks Habitual - I'll give it a whirl tonight!

---

### Post by agklimit on 2012-09-16
Here's one Mint user happily using the Ubuntu release of VB. (Although Mint did protest when I d-loaded that, saying that it's better to use the officially supported one - but it does work OK).

---

### Post by SeijiSensei on 2012-09-16
I recommend that rather than downloading and installing the .deb file, you follow the instructions on the Linux download page to add the VB repositories to /etc/apt/sources.list.  Then copy that long command to install the repository key by pasting it into a terminal.

Once you done both those things, just run

```

sudo apt-get update
sudo apt-get install virtualbox-4.1

```

If you follow these steps, VB will be managed like all the other packages on your system.  You will be notified if updates are available which you can install using the System Update function that you use to upgrade all other packages on the system.

---

