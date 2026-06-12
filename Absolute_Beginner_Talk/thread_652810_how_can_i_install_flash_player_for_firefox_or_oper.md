---
title: "how can i install flash player for firefox or opera in 64bit ubuntu?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by horry on 2007-12-29
i download the flash player, untar it, run 'install_flash_player_9_linux' in a terminal, but i got this below. how can i make my firefox support flash?
thanks a lot.

---

### Post by Jimmyfj on 2007-12-29
You should be able to do so through either Synaptic, System>Administration>Synaptic, search for flash in the search-field - or through Add/Remove Programs, Programs>Add/Remove Programs>Others

---

### Post by horry on 2007-12-29
> **horry said:**
> i download the flash player, untar it, run 'install_flash_player_9_linux' in a terminal, but i got this below. how can i make my firefox support flash?
thanks a lot.

so sorry to the administrator, plz delete this thread, i made a duplication.

---

### Post by Sef on 2007-12-29
> so sorry to the administrator, plz delete this thread, i made a duplication.

Other thread has been locked; however, a link to here has been provided.

---

### Post by Sef on 2007-12-29
> You should be able to do so through either Synaptic, System>Administration>Synaptic, search for flash in the search-field - or through Add/Remove Programs, Programs>Add/Remove Programs>Others

Make sure that Universe and Multiverse repositories have been opened.  Flash is in Multiverse.

In Add/Remove > change the top right box to 'All Available Applications'.

In Synaptic > Settings > Respositories > check Universe and Multiverse.

---

### Post by RomeReactor on 2007-12-29
Hi. What error message were you getting? if you installed Flash from the repositories, then you need to use [this package to correct a bug]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb") (the fix will be made available in the repositories relatively soon). For Opera, the current stable version (9.25) has a problem with Flash, but you can use the [latest beta]("http://www.opera.com/download/linux/?ver=9.50b"). For more details, try [this thread]("http://ubuntuforums.org/showthread.php?t=644075").

---

### Post by Sef on 2007-12-29
Rome Reactor:

This is the error message the duplicate post:

> 
ERROR: Your architecture, \'x86_64\', is not supported by the
Adobe Flash Player installer.


Since the OP was trying to install it directly from the Adobe site that error message is to be expected.

---

### Post by RomeReactor on 2007-12-29
> **Sef said:**
> Rome Reactor:

This is the error message the duplicate post:



Since the OP was trying to install it directly from the Adobe site that error message is to be expected.

Thank you for the clarification.

horry, the 64 bit architecture needs a special wrapper for the flash plugin (which is 32-bit only), so, in Firefox, try going to a website that requires Flash, such as YouTube; when it requests to install the plugin, say yes. However, as far as I know the plugin available in the repositories is still buggy, so to confirm this is still the case restart Firefox and go to YouTube to see if it works. If it still doesn't, you need to follow my earlier post.

Unfortunately, Flash won't work with Opera 64-bit.

---

