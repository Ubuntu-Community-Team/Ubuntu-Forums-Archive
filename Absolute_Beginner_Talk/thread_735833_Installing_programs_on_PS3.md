---
title: "Installing programs on PS3"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Shunsuke_01 on 2008-03-26
Sorry if this is the wrong place (as I'm very new, I have absolutely no idea where to post this),

but could someone please give me step-by-step instructions for installing programs like VLC on my PS3?

When I type "sudo apt-get install vlc", it comes up something saying it could not find package vlc. How can  I fix this? And is installing programs for Ubuntu on the PS3 the same as doing it on a desktop?

Thanks.

---

### Post by kesman on 2008-03-26
I think you need to check your /etc/apt/sources.list and add there a repository that contains vlc. Also, search for it with
```

apt-cache search vlc

```
because it may be there with a different name.

---

