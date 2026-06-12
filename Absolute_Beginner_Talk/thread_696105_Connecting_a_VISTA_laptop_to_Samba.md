---
title: "Connecting a VISTA laptop to Samba"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by SteveHall on 2008-02-13
Newbie here...

I've installed Ubuntu 7.10 onto a PC that has an ethernet connection to a router modem.  I've followed all the Linux instructions on the "HOWTO: Setup Samba peer to peer with Windows" Sticky post it in the Absolute Beginner Talk section.  All of this has gone fine.  However when I now come to set up my Windows VISTA laptop I can't get it to see the Linux machine.  I think this HOWTO guide was put together pre-VISTA as I can't follow the instructions properly.

I'd really appreciate some help getting my VISTA laptop to be set up to be able to see the Linux machine and the share I've set up on it.

Thanks

Steve

---

### Post by Existentialist on 2008-02-13
From my computer you can click tools in the menu bar and select map network drive.  For the path you put in \\192.168.x.xxx\sharename    where the x's are the ip address of the Ubuntu box, and the sharename is the name of the folder you shared on Ubuntu.

---

### Post by mrsteveman1 on 2008-02-13
In your case, first make sure Vistas network adapter has both network discovery and file sharing enabled.

If that doesn't work you may need to disable NTLMv2, which is somewhat difficult if you aren't using Vista Ultimate, but I'll look into it again if you are using home edition.

---

