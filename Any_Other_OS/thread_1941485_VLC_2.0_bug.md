---
title: "VLC 2.0 bug"
date: 2012-03-15
forum: Any Other OS
---

### Post by JohnTeush on 2012-03-15
Hi everyone ;),

I'm a Linux Mint 11 user and like many, I tried to install the new VLC 2.0. After many fails, this method worked on my laptop :

[PHP]sudo add-apt-repository ppa:videolan/master-daily
sudo apt-get update && sudo apt-get dist-upgrade[/PHP]

VLC works perfectly on this computer (Linux Mint 11).

But on my other computer (Linux Mint 11 too) it almost did : same code pasted before, VLC 2.0 is launching and reads mp3, but when I want to open a video (whatever the extension is, .avi, .mov, .mkv, .mp4), VLC blinks and shuts down. I don't understand why it did work on the laptop but not on this one...

I tried to delete it completely and reinstall, it's still the same issue ! Moreover, I don't know how to downgrade to the previous version of VLC...

I ran VLC in a shell, it returns nothing for a .mp3 because it works, but for a .mkv, this is what I get when VLC crash :

[PHP]MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself
MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself[/PHP]

And for a .avi :

[PHP][mpeg4 @ 0x123a140]Invalid and inefficient vfw-avi packed B frames detected
Erreur de segmentation[/PHP]

And I'm kind of lost, if someone has an idea...

Thanks

---

### Post by oldos2er on 2012-03-15
Moved to Other OS/Distro Talk.

---

### Post by wolfen69 on 2012-03-15
> **JohnTeush said:**
> I don't know how to downgrade to the previous version of VLC...


First, uninstall vlc 2.0 and then remove or disable the vlc repository. Then
```
sudo apt-get update
```
You will then be able to reinstall the previous version of vlc.

---

### Post by JohnTeush on 2012-03-19
Since I was unable to solve this problem with 2.0, I followed your steps and reinstalled the previous version.

Thank you !!

---

### Post by DrunkenMonkey on 2012-05-20
Hi, sorry for reviving an old thread,  I have the same problem but on ubuntu 11.04. I'm using VLC media player 2.1.0-git Rincewind, all other players work without problems. I know how to revert to the previous install but I would like to get vlc 2 working if possible, any ideas?

---

### Post by YavorAtanasovUs on 2012-05-21
Same problem here....

---

### Post by andrew.46 on 2012-05-22
> **DrunkenMonkey said:**
> Hi, sorry for reviving an old thread,  I have the same problem but on ubuntu 11.04. I'm using VLC media player 2.1.0-git Rincewind, all other players work without problems. I know how to revert to the previous install but I would like to get vlc 2 working if possible, any ideas?

Rincewind is working fine here and I have recompiled just now to check:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.1.0-git Rincewind (revision 669ce09)
VLC version 2.1.0-git Rincewind (669ce09)
Compiled by root on skamandros.andrews-corner.org (May 22 2012 20:17:58)

```

Where is your version coming from?

---

### Post by DrunkenMonkey on 2012-05-25
Thanks for your reply and sorry I took so long to get back. I got it from ppa:videolan/master-daily, it was the only way I could find to install, apart from compiling and that never goes well for me. I might have a go though.

---

