---
title: "[SOLVED] help understanding amarok"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-05-14
Can't get amarok to play my files on the network.  Get this message:
```
 
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.

```
I can play internet radio, I can navigate to files, they just won't launch.
Does Amarok only work effectively with KDE?  I'd really prefer to stick with Gnome until I get more comfy.  
How can I tell whether I have all my necessary packages installed?

Thanks folks.

---

### Post by Jeff24K on 2007-05-14
What do you mean by "files on the network"? What type of files, and are you trying to play them from an NFS share or similar, or are you trying to "stream" them somehow? Can you play the same types of files locally, if they're on the same machine as Amarok?

---

### Post by Ateo on 2007-05-14
If you're trying to play files with paths like smb://server/blah, it won't work. Amarok (it might depend on your backend engine) requires the file to be on a mounted drive. smb://.... are not mounted. So, either try changing backend engines or mount the network share with said multimedia.

I could be wrong as I haven't used the newest version of amarok.

HTH

---

### Post by il-luzhin on 2007-05-14
thnx

---

