---
title: "Feisty + Beryl + MBPro CoreDuo 15&quot;"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by stickboy3k on 2007-04-20
Well I couldn't install, but then was able to go through the text mode install using the Alternative cd.

Then x wouldn't start so I did the work around to install fglrx then startx.

Now I'm in Feisty and loving it. Screen brightness, keyboard backlight brightless, volume, etc all work perfect.

I'm just unable to get beryl installed and running. I also tried compiz since it was already installed. I can live without it but if anyone has been able to get it to run on a Macbook pro 15" Core Duo and wouldn't mind tossing me some pointers, I'd really appreciate. Here's some of what I've done:

Followed walkthrough here: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

That walkthrough worked perfect in Edgy on this same triplebooting macbook pro. I then added:

```
Section "ServerFlags"
Option "AIGLX" "off"
EndSection
```

to my xorg.conf so beryl would use xgl. Now I get this error when trying to start beryl:

GLX_EXT_texture_from_pixmap is missing
using non-tfp mode
GLX_SGIX_fb config is missing
No managable screens found on display localhost1.0

Thanks all,
Ron

---

### Post by stickboy3k on 2007-04-20
A quick little update.

I've been able to get beryl working now. I had noticed it mentioned that beryl is now included in the official repositories, so I thought to check the version number that I had installed. I had installed version 0.2.1.dfsg+git20070318-0ubuntu2 (latest on official repository). Previously (running edgy) I had installed from the repository listed in the howto that I followed which installed version 0.2.0~0beryl1.

So I opened Synaptics and removed all of the beryl things that I had installed, then I disabled the official repositories leaving only those listed in the howto. Then I installed the previous version that I had tried. Finally I reenabled those offical repositories.

Now I've got beryl running (using beryl-xgl, which was missing from 0.2.1), the only downsides right now are that it's an older version and software update keeps bugging me to install the new version.

---

### Post by ronocdh on 2007-04-20
> **stickboy3k said:**
> A quick little update.

I've been able to get beryl working now. I had noticed it mentioned that beryl is now included in the official repositories, so I thought to check the version number that I had installed. I had installed version 0.2.1.dfsg+git20070318-0ubuntu2 (latest on official repository). Previously (running edgy) I had installed from the repository listed in the howto that I followed which installed version 0.2.0~0beryl1.

So I opened Synaptics and removed all of the beryl things that I had installed, then I disabled the official repositories leaving only those listed in the howto. Then I installed the previous version that I had tried. Finally I reenabled those offical repositories.

Now I've got beryl running (using beryl-xgl, which was missing from 0.2.1), the only downsides right now are that it's an older version and software update keeps bugging me to install the new version.
Hm, very interesting, thanks for the follow-up. I'd like to test it myself this weekend. I must ask, though: do you have full 3D acceleration? What do you get when you type **fglrxinfo** in the console?

---

### Post by stickboy3k on 2007-04-20
> **ronocdh said:**
>  What do you get when you type **fglrxinfo** in the console?

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)
```

---

### Post by ronocdh on 2007-04-20
> **stickboy3k said:**
> ```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)
```

Humbug. Thanks. I never got it working with Edgy, although with Dapper I had almost no trouble. I'll give Feisty final a spin tonight and see what I come up with. Thank you again.

---

