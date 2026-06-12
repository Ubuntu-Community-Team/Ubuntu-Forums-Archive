---
title: "mp3's wont work"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by 068139 on 2008-04-14
i installed ubuntu yesterday, finally got flash files to stream online with help from starcannon and VNC.

Now I'm having problems playing audio files. I've downloaded Amarok to be my application to play audio files. I've got a sound card, I can't use on-board sound because it's blown (dont ask).

When I open an audio file with any application it just freezes..

---

### Post by stchman on 2008-04-14
> **068139 said:**
> i installed ubuntu yesterday, finally got flash files to stream online with help from starcannon and VNC.

Now I'm having problems playing audio files. I've downloaded Amarok to be my application to play audio files. I've got a sound card, I can't use on-board sound because it's blown (dont ask).

When I open an audio file with any application it just freezes..

You need the proper CODECs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

This will get you playing MP3s.

---

### Post by RiceMonster on 2008-04-14
Have you installed the Ubuntu Restricted Extras package? If not, open up a terminal (applications > accessories > terminal), then run this command:

```
sudo apt-get install ubuntu-restricted-extras
```

Or, if you prefer, you can go to Applications > Add/Remove and find it in the Other section.

---

### Post by 068139 on 2008-04-14
Just installed both of them now guys, still not working. I havn't yet installed the driver because I cannot. I figure this is the problem. It's an apollo PCI sound card and the version is ver 2.60p  05/28/2001

=[

---

### Post by Pijits_1 on 2008-04-14
If your using Amarok you'll need to download the codecs from the amarok site. 

[http://amarok.kde.org/wiki/MP3](http://amarok.kde.org/wiki/MP3)

---

