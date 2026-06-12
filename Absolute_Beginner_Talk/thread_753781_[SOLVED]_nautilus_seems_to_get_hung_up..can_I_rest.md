---
title: "[SOLVED] nautilus seems to get hung up..can I restart nautilus without rebooting"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by hovzio on 2008-04-13
hi, sometimes when im using xmms and theres alot of drag and drop going on (making playlists ect..) nautilus seems to get hung up. As soon as the mouse hovers over a desktop icon it turns into this weird little "birdlike fingericon?" It dosnt happen too often just when im moving, copying lots of files in naut. For a while things still run smoothly and then piece for piece it kinda quits working. Its like i have no access to the files on my desktop. Programs will start and run fine and are usable.(like xmms still runs but cannot add any new songs unless i add them via terminal) so I am assuming that its nautilus but im not sure. Can I restart nautilus without doing a reboot and without interfering with the rest. I can cp, mv ect.. files fine from within the terminal so.. and Ive just started interpreting logfiles so as of now they havent helped me much. thanks for any help!

---

### Post by Martje_001 on 2008-04-13
Press ALT+F2 and enter 'killall nautilus'. If nautilus doesn't start after that press ALT+F2 again and typ 'nautilus'.

---

### Post by stchman on 2008-04-13
> **hovzio said:**
> hi, sometimes when im using xmms and theres alot of drag and drop going on (making playlists ect..) nautilus seems to get hung up. As soon as the mouse hovers over a desktop icon it turns into this weird little "birdlike fingericon?" It dosnt happen too often just when im moving, copying lots of files in naut. For a while things still run smoothly and then piece for piece it kinda quits working. Its like i have no access to the files on my desktop. Programs will start and run fine and are usable.(like xmms still runs but cannot add any new songs unless i add them via terminal) so I am assuming that its nautilus but im not sure. Can I restart nautilus without doing a reboot and without interfering with the rest. I can cp, mv ect.. files fine from within the terminal so.. and Ive just started interpreting logfiles so as of now they havent helped me much. thanks for any help!

I find that restarting the workspace fixes any Nautilus problems.

CTRL-ALT-BKSP

---

### Post by Martje_001 on 2008-04-13
> **stchman said:**
> I find that restarting the workspace fixes any Nautilus problems.

CTRL-ALT-BKSP
That's for restarting the X-server. Use it rarely, it also logs other users off, and does not save opened documents, or unsaved settings.

---

### Post by hovzio on 2008-04-13
thanks!!!works perfect, nautilus restarts on its own to.thank you so much.I dont need to restart x i just alt f2 and killall.great. I wish i could understand the whys and hows but for now the solution is more than satisfying.thanks

---

