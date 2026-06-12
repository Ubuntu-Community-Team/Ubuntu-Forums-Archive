---
title: "XGL ATI X700 on Dapper Help"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-05-06
I am using Kubuntu Dapper with an ATI X700Pro. I followed [this tutorial]("http://smorgasbord.net/ati_beryl_kde_dapper_my_guide") to get things started but of course it did work. I have the option to select XGL session at the startup menu. But anything graphical crawls and beryl does not start up. My normal kde session works just fine and I seem to have beryl installed because I can open beryl-settings.

My fglrxinfo
```
bob@mybox:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18
```when I enter in beryl
```

bob@mybox:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```I do have server-xgl installed but for some reason its just not working. I know theres a million posts about this but I've been going through them all for the last couple of hours with no luck so any help is appreciated. Thanks.

---

### Post by overdrank on 2007-05-06
> **thelocust said:**
> I am using Kubuntu Dapper with an ATI X700Pro. I followed [this tutorial]("http://smorgasbord.net/ati_beryl_kde_dapper_my_guide") to get things started but of course it did work. I have the option to select XGL session at the startup menu. But anything graphical crawls and beryl does not start up. My normal kde session works just fine and I seem to have beryl installed because I can open beryl-settings.

My fglrxinfo
```
bob@mybox:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18
```when I enter in beryl
```

bob@mybox:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```I do have server-xgl installed but for some reason its just not working. I know theres a million posts about this but I've been going through them all for the last couple of hours with no luck so any help is appreciated. Thanks.

Well I hate to be the bad news but dapper no longer supports beryl. If you look at the date of the post beryl is not supported after march 2007, That is why I am running edgy and dapper. :(

---

