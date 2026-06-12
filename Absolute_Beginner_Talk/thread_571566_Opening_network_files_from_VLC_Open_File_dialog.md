---
title: "Opening network files from VLC Open File dialog?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by cloudy-b on 2007-10-09
Hi all,

I am a relative newbie to Ubuntu; just installed onto an old laptop. Loving it so far! I do have a question about the file manager. I did a search, and someone asked similar thing, but no replies... so:

I am using VLC to watch some tv shows (Divx, Xvid) which have subtitle files (.srt). I keep the tv shows on a shared drive on my Desktop computer and connect to it via the network. I can see the folders and files using Nautilus, but the only way I can open a video and it's subtitle file (that I know how) is via VLC's Open File dialog box. The problem is that I cannot seem to pull up the network shares in that dialog box. What am I missing, or where should I look?

Any help would be greatly appreciated. Copying the tv shows and subs to the local drive takes too long, btw. Thanks!

Barron

---

### Post by notwen on 2007-10-09
What method are you using to access thee shared network files? SMB or NFS?  Are you mounting said shared folders anywhere?

---

### Post by cloudy-b on 2007-10-09
I believe it is SMB. (I see the little SMB on the icon) On the desktop (WinXP), I am using the basic file sharing to share the folder.

---

### Post by Zedix on 2008-01-08
I had the same problem... Solved it by copying the smb path and pasting it in the Open File dialog :) Worked great!

For example: Open File > and put the path, for ex: smb://yourpc/Videos/movie.divx

---

