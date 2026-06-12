---
title: "Network Video Files"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by roton on 2007-11-30
Hi, I installed Ubuntu yesterday and am slowly getting into it after being an xp user for so long.

The issue I am having is that I have installed vlc but network files never get opened with it.
Local files are fine, they seem to know that vlc is what they need to be played with.

I have tried right clicking on the network file and going to "open with" but this results in vlc being loaded with no file in it. 

I tried right clicking and properties and then open with vlc everytime, but again this doesn't work and it opens with Totem regardless :(

Lastly I went to /usr/share/mime and typed "ls video/* | sed 's/.xml/=vlc.desktop/' | tee -a ~/.local/share/applications/defaults.list" but alas files opened over network open with Totem rather than vlc :(

Does anyone have any ideas?

---

### Post by hyper_ch on 2007-11-30
How do you connect to the network server? Samba? SFTP? ...?

---

### Post by roton on 2007-11-30
The machine I'm connecting to has windows file sharing enabled so I just click on network and windows network. There I find a list of all my shares. I think xp uses CIFS.

---

### Post by hyper_ch on 2007-12-01
Ok... I thought simplest method would be to mount the remote folder into your system... but I only know how to do that with sshfs

---

### Post by roton on 2007-12-01
Thanks hyper_ch, I just realised its SMB. I will google on mounting network drives now and hope it works.

---

