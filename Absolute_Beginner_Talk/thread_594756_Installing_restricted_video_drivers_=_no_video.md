---
title: "Installing restricted video drivers = no video"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by BRODEL on 2007-10-28
I just installed 7.10 last night and was planning on trying out vmware server on it. After install it says there are some updates so I say ok install them. Then it pops up and says do I want to enable restricted video drivers. I can't think of a reason why not, sure. Then I notice an error in firefox when I try to view my downloads and notice firefox was one of the items updated so I figure I'll reboot and let all of those updates take effect.

Now when it's booting I see the logo with the progress bar and then it goes black and instead of seeing a login screen I see nothing. My guess is that it has to do with the restricted video drivers, but I don't know how to put them back the way they were. I could just reinstall and I might do that, but I was thinking I wouldn't get any 3D effects if I just reinstalled and never updated and now I'm curious as to why the restricted drivers don't work for my card anyhow. 

The video card I have is a ATi 9600 Pro by the way... hopefully someone can shed some light on this for me. Thanks in advance.

---

### Post by Qwerty_ on 2007-10-28
Try Cntrl+Alt+F2 this should bring you to a terminal prompt.

Then type

```
sudo dpkg-reconfigure xserver-xorg
```

Alternatively bootup in recovery mode and run the same command.

---

### Post by BRODEL on 2007-10-28
awesome! That looks like it fixed it. (after I noticed dplg had been replaced with dpkg :) )

After it asked me about the video card, it asked me a lot of questions I didn't really have the answers to about the mouse and keyboard settings and protocols to use. I just kept the defaults and I hope that works out fine. Everything looks like it works ok for now anyway. 

Anyway, thanks for the incredibly fast solution to that problem!

---

