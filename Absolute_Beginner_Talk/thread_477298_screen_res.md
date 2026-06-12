---
title: "screen res"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mowermanjp on 2007-06-18
Hi everyone, 
reposting this as a new post in case its not read in the original post.
Still having trouble with setting resolution default. everytime i start computer i have to use the nvidia control panel to pick the resolution, its never listed in the resolution preference tab. how do i set it to boot with the correct resolution?

---

### Post by AndyCooll on 2007-06-18
In a command line type:

```
sudo dpkg-reconfigure xserver-xorg
```

Work your way through the questions (accepting most of the defaults). One of the options towards the end relates to screen configuration.

Alternatively you could manually edit the xorg.conf file to add additional screen resolutions (you'll find plenty of threads telling you howto do this if you do a search)

:cool:

---

