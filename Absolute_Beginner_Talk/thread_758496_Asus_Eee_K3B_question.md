---
title: "Asus Eee K3B question"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Slimboyfat on 2008-04-18
I suspect that this is a newbie question, so I haven't posted it in the Multimedia section.

The Eee, as you know, only has a 4gb flash drive, so I have a 500gb NAS drive on my home network for all media storage and a 2gb flash card in the slot, for additional local storage.

I am in the process of burning some mp3 CDRs for the car and have installed K3B, as it recognises the dual layer CDRs

The problem is that K3B doesn't let me navigate to non-local directories(not even the 2gb flash card) - so I cant drag and drop from my existing mp3 locations

The only way I have got around this is to duplicate the mp3s in a local folder, but I don't have enough memory space for a full CDR and it's an unnecessary, time consuming duplication.

Can anyone tell me how to force K3B to recognise my network, or suggest an alternative that won't give me this problem?

Answers on a postcard please

regards
Slimboy...

---

### Post by luisromangz on 2008-04-18
If you can mount the remote file system into a normal folder, k3b should see it.

---

### Post by talsemgeest on 2008-04-18
I'm on my windows box now so I won't be able to check if it works, just going from memory. You should be able to type or copy and paste the location into the adress box as far as I can remember...

---

### Post by Paqman on 2008-04-18
Your NAS is probably designed to share with Windows networks, and so is probably going to be using Samba. This thread should tell you [how to permanantly mount Samba shares locally](http://ubuntuforums.org/showthread.php?t=288534).

If it's a posher NAS it might be able to use NFS though. If that's the case then that's preferable over SMB/CIFS.

---

