---
title: "flash problems"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by SirCoreyMarshall on 2007-12-22
hey ubuntu community!
i used to be into ubuntu / linux but have forgotten everything.......
i think i am using this command right

sudo apt-get install flashplugin-nonfree

but i get the error at the end of the terminal window saying

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


Help me out here guys

---

### Post by PriceChild on 2007-12-22
Adobe updated the tar.gz archive that the ubuntu package downloads.

However Ubuntu has not updated its package yet because it would break konqueror in kubuntu.

You can see the current status of the bug at [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

---

