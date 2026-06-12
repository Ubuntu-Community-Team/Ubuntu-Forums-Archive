---
title: "dwl-g132 not working"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by froggger on 2007-10-19
ok, so in this thread:[http://ubuntuforums.org/showthread.php?t=516438&highlight=dwl-g132](http://ubuntuforums.org/showthread.php?t=516438&highlight=dwl-g132)
he said that he got it working without ndiswrapper.
how do i do that??
i got into network manager and itried wlan0 for the connection name, but no go.

any ideas to make this work without ndiswrapper.

BTW i am using gutsy gibbon.

Oh and teh connection i'm trying to get is unencrypted.

---

### Post by James7 on 2007-10-22
Hey Frogger, 

Ok, I can't tell you about your particular wifi setup. But when I installed Feisty on the family PC the wifi card was not found. I installed ndiswrapper and ndiswrapper-utils (I know these have been problems for you). Then I used them to install the Windows driver for the wifi card.

When Gutsy went final, I clean-installed it onto that same machine and it found the wifi card with no need for ndiswrapper, etc.

Have you tried to backup your data and clean-install? :)

PROBABLY someone here will have better advice for you. I am just curious if you are having these problems after having done a clean-install.

---

