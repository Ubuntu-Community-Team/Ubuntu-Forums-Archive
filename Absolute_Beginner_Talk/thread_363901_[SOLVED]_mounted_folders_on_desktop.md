---
title: "[SOLVED] mounted folders on desktop"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-02-17
Hi. everybody

I read somewhere that if you mount your partitions to the media folder ( /media/winxp ) then they would automatically be bookmarked in the left pane of nautilus.

This sounded good to me, and since I have 9 partitions I didn't like the look of seeing them all mixed in with my current operating system folders.

So I remounted all 9 and after rebooting all 9 are in the left pane of nautilus but they are also now represented as icons on my desktop. I don't want the desktop icons. Does anyone know how to get rid of them?

---

### Post by Maestro23 on 2007-02-17
Might help: [http://www.ubuntuforums.org/showthread.php?t=362911&highlight=desktop+icons](http://www.ubuntuforums.org/showthread.php?t=362911&highlight=desktop+icons)

---

### Post by rusty4r on 2007-02-17
The link you refered to gives these instructions:

> alt-f2, gconf
go to apps > nautilus > desktop and uncheck "volumes_visible"

When I push alt-f2  little gui box comes up asking what progam to run, so I figured that I was supposed to type in "gconf". But, the little box says it can't find gconf.

Does that mean I don't have it or am I doing this all wrong?

---

### Post by Maestro23 on 2007-02-17
> **rusty4r said:**
> The link you refered to gives these instructions:



When I push alt-f2  little gui box comes up asking what progam to run, so I figured that I was supposed to type in "gconf". But, the little box says it can't find gconf.

Does that mean I don't have it or am I doing this all wrong?

Probably don't have it installed.  Search for it in Synaptic  and install.

---

### Post by rusty4r on 2007-02-17
Well I started Synaptic and sure enough it was not installed. So, I installed it. 

I tried the 'fix' once again but still the same answer:

> Could not open location 'file:///gconf' 
The location or file could not be found.

So I thought maybe i need to reboot before it will show up. I rebooted and tried it again. Still the same result.

---

### Post by rusty4r on 2007-02-17
OK I did a search for all files with name gconf. I found 255 but only a few were executable. I tried gconf-editor and got what i beleive to be the right utility. I followed the rest of the 'fix' and presto the icons are gone.

Problem solved. Btw there was no exec. file named gconf just folders with that name.

Anyway thank you very much Maestro23 for the link and the help, and Meng of course for the how to.

---

