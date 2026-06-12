---
title: "boot selection on restart"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Ryokukitsune on 2007-10-27
this is just a thought and and possibly a suggestion/question for the novelty of convince.

when I restart my machine so far the only way I have to select which OS I want to boot is to wait for that 10 second (or less depending on your settings) window where grub loads. I have Ubuntu and Windows installed and I sometimes miss that window if I'm forced to leave the room.

is there a way to instruct Grub (or any boot loader) before hand, say at the log-off window, to load a specific OS on next power up? I mean, if you can chose what flavor of desktop environment I'd like to have the ability to boot Windows (or other OS) on restart.

wouldn't that be convent?

---

### Post by Halfling Rogue on 2007-10-27
Pretty sure you have to edit /boot/grub/menu.lst , and change the boot= to whatever partition you want.

---

### Post by kellemes on 2007-10-27
As far as I know there is no clean way of doing this.. but surely you could create a bashscript that handles it for you.
Like..
Having 2 different versions of menu.lst, one with Windows as default OS, and the other with Ubuntu as default OS.. you could let the script exchange the files at your command.

For more Grub info see here.. Maybe you'll find a way.. :)
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Duck2006 on 2007-10-27
Or just change the time from 10 seconds  to 30 seconds or longer. You can always hit enter if it's to long to wait.

---

