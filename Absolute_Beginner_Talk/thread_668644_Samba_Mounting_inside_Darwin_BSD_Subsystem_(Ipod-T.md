---
title: "Samba Mounting inside Darwin BSD Subsystem (Ipod-Touch/Iphone)"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Leed on 2008-01-15
There are many very helpful posts around about mounting the new iPods to Ubuntu, but I'm wondering if the opposite is also possible.

My basic Idea is to use the ipod-touch as my home Sound System, that could play all my mp3 files. Now I'm wondering if I could have a server running (with something like a 200BG Harddrive) and mount it's filesystem inside the ipod, then somehow confuse the ipod to make it include all songs on the mounted drive into it's playlist. 

Now obviously there's no official solution to this, for it would stop people paying more for the 16GB ipod instead of the 8GB... but we all have Jailbreak, with a Linux subsystem (Darwin) running inside, so shouldn't it be possible to extend the ipod's harddisk? Would it work with Samba, or some other system?

---

### Post by mattismyname on 2008-01-18
I think the tough part would be getting the exported filesystem mounted on the ipod.  My iphone only seems to support mounting hfs filesystems, not nfs or samba.  Thus playing through the "official" mp3 player is probably pretty damm difficult.

There is an app in installer called iRadio which is capable of decoding and playing mpeg streams.  This would probably be the best bet.  Perhaps there are other apps out there that can stream mp3s from an http server on your network.

You also might be able to hack something together with ssh to transfer the data and then some other app on the phone to decode and play the mp3.

---

### Post by Leed on 2008-02-15
interesting thoughts, the radio thing may work, but I guess it would prevent me from controlling which songs are being played, it would need some kind of remote tool.... Would be like playing iTunes on a Server machine and controlling it via VNsea on the iPod. 

In fighting to get firmware 1.1.3 working with amarok, I changed the iPods new media directory (/var/mobile/Media) into a symbolic link that points to the folders linux uses (/var/root/Media). **[COLOR="Red"]**Warning This does stop iTunes working with the device***[/COLOR]**, [COLOR="Blue"]but it lets Amarok use it[/COLOR]. 
Maybe making turning the linux folder into a link would have worked better, but there's no turning back now for me. 
-> Anyway, this gives me the idea, if I could use a Network Mountpoint instead of a symbolic link, I could have my whole iPod library on the server, that is if the iPod is dumb enough not to notice. 

but I don't know much about network mounting, is a mount with the hfs system possible via Ubuntu?

---

### Post by mattismyname on 2008-02-15
Only for a local disk...  To mount a disk from the Ubuntu box onto the iphone you would have to use nfs/samba/sshfs or something of the like and I don't think the iphone kernel can mount using those methods.

---

