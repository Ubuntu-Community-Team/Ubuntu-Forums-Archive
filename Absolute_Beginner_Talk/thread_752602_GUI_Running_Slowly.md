---
title: "GUI Running Slowly"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Daggity on 2008-04-11
To begin with, let me start way back when. When I first installed Linux Mint (I know, not exactly Ubuntu, but it's hardly different.). I had put in the Live CD, and it would not allow me to run in a higher graphics mode than the lowest. I thought this was odd, but I installed it anyways and thought I could fix it later.
Once I had it installed, I could not run in a better graphics mode still. I installed Compiz Settngs Manager and it Compiz itself. I had updated the computer all the way. When I restarted my computer after this, I could not load up the xserver. Something about a fatal error. I was successful in using a back up, though, and have reached my GUI.
My problem now is that it runs as if I have no graphics card installed. I've checked and tried to use different graphics drivers to no avail. I don't believe that's the problem though; as I was able to run an HD video perfectly.
I believe what may be the problem here is that the xserver is not acquiring any memory set aside for it's usage. 


Oh, and as a side note, when I used the sudo dpkg-reconfigure xserver-xorg, it kept getting stuck at the screen asking me for the color bits. It would just return to the command line.

---

### Post by crjackson on 2008-04-11
> **Daggity said:**
> To begin with, let me start way back when. When I first installed Linux Mint (I know, not exactly Ubuntu, but it's hardly different.). I had put in the Live CD, and it would not allow me to run in a higher graphics mode than the lowest. I thought this was odd, but I installed it anyways and thought I could fix it later.
Once I had it installed, I could not run in a better graphics mode still. I installed Compiz Settngs Manager and it Compiz itself. I had updated the computer all the way. When I restarted my computer after this, I could not load up the xserver. Something about a fatal error. I was successful in using a back up, though, and have reached my GUI.
My problem now is that it runs as if I have no graphics card installed. I've checked and tried to use different graphics drivers to no avail. I don't believe that's the problem though; as I was able to run an HD video perfectly.
I believe what may be the problem here is that the xserver is not acquiring any memory set aside for it's usage. 


Oh, and as a side note, when I used the sudo dpkg-reconfigure xserver-xorg, it kept getting stuck at the screen asking me for the color bits. It would just return to the command line.

You should post your hardware specifications to include your graphics adapter.  No one will be able to help you unless you provide this information.

---

### Post by Daggity on 2008-04-11
I use the, "Mobile 915GM/GMS/910GML Express Graphics Controller." with the, "i810 Intel Integrated Graphics..." driver. Is there a command I that would allow me to copy/paste and show you the information you need?

---

