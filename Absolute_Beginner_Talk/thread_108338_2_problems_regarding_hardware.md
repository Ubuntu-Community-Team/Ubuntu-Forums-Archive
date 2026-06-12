---
title: "2 problems regarding hardware"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by guiamaral on 2005-12-25
hi folks,

i've just migrated to ubuntu linux after some years of microsuck windows and i'm just doing fine with it, although i'm having a few problems.

there they go:

1)
I cannot read/write my NTFS parition. Ubuntu says that i can't see it because i'm not the owner, so when i click the icon on my desktop, it denies the access. it happens even when i run 'su root'.

so, how do I fix this problem?

2) 
i have a encore ethernet adapter, which runs faster than the onboard eth, but ubuntu did not recognise it. as i downloaded the drivers somewhere on the web, i did decompress the gz file, but i can't decompress the tar file.

how do I decompress it and install the hardware?

thank you

happy new year

---

### Post by jimrz on 2005-12-25
1- to get your ntfs partition to auto mount and allow all users to read [**[COLOR="Sienna"]see this[/COLOR]**]("http://ubuntuguide.org/#automountntfs"), I understand that it is now possible to read/write ntfs, but also that it is somewhat problematic. Can't say for sure if the problem part is true as I have not tried it yet.   Be sure you unmount the ntfs partition before trying to do anything new with it.

2- Do your BIOS have a setting which allows you to disable the onboard eth? If so, doing that may allow ubuntu to see the card you want to use.

---

