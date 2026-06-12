---
title: "Any ppc owners try out Ubuntu 10.04?"
date: 2010-04-28
forum: Apple Hardware Users
---

### Post by Dukenukemx on 2010-04-28
With 10.04 coming out tomorrow, has anyone tried it so far on ppc machines?  

Tempted to try it myself, but I feel I might end up regretting it.

---

### Post by avtolle on 2010-04-28
Have tried (am trying) it out on G4 Cube. Have not had any issues. For grins, I've added the Lubuntu desktop package and have been pleased with the (apparent) increase in speed when I log in with it as opposed to Gnome. Had to use my own /etc/X11/xorg.conf file but that was expected.

---

### Post by Dukenukemx on 2010-04-28
So, all the things I did to get 9.10 running I'll have to do with 10.04?  Can I just upgrade or I have to reinstall?

---

### Post by avtolle on 2010-04-28
I've two cubes. One, I did the "recommended" upgrade without moment. The other I did a reinstall using the alternate install iso. The latter (my preferred way) went OK, with the need to manually create the /etc/X11/xorg.conf file. As has been the case since 7.10, I was not able to use the "live" (Desktop) cd for installation (I always try it once in hopes it works, so I can share my experience), as it just didn't work (from DVD, due to the size of the iso).

As usual, YMMV. Good luck.

---

### Post by zeroti on 2010-04-28
> **avtolle said:**
> I've two cubes. One, I did the "recommended" upgrade without moment. The other I did a reinstall using the alternate install iso. The latter (my preferred way) went OK, with the need to manually create the /etc/X11/xorg.conf file. As has been the case since 7.10, I was not able to use the "live" (Desktop) cd for installation (I always try it once in hopes it works, so I can share my experience), as it just didn't work (from DVD, due to the size of the iso).

As usual, YMMV. Good luck.

If dvds give you issues, you could try overburning a cd.

I did the "update-manager -d" installation method, and the keyboard and mouse became non-responsive during the update, so when "clean up" came, I couldn't click the dialogs, so I had to hold down the power button to restart. one way to avoid this could be using a command like "sudo apt-get -y dist-upgrade".

I don't know if this is related, but I'm getting "software rasterizer" with "glxinfo | grep render" instead of hardware rendering with my graphics card. It could be related to the fact that I don't have an xorg.conf file, but I read somewhere that kernel mode-setting should be able to figure things out without one.

In any case, I'll try re-installing with a live cd.

---

### Post by B_Free on 2010-04-28
There are a few issues booting and shutting down. Not bad. You do have the xorg problem. Apparently that has to be expected. It is the same set up as previous versions. The desktop version was not a problem for my 450 PPC. The background is different and nice.

---

### Post by Dukenukemx on 2010-04-29
10.04 is out today, is there a final release for ppc?

---

### Post by hydraulicjj on 2010-04-29
> **Dukenukemx said:**
> 10.04 is out today, is there a final release for ppc?

I don't know about a final release but there's the [daily build live cd]("http://cdimage.ubuntu.com/ports/daily-live/current/") and the [daily build alternate cd]("http://cdimage.ubuntu.com/ports/daily/current/"). I'd say that a powerpc port will probably come out at a later date.

---

### Post by WRATGUT? on 2010-04-30
> **Dukenukemx said:**
> 10.04 is out today, is there a final release for ppc?

There is now:

[URL="https://wiki.ubuntu.com/PowerPCDownloads"]http://cdimage.ubuntu.com/ports/releases/lucid/release/
[/URL]

---

### Post by Dukenukemx on 2010-05-01
> **zeroti said:**
> 
I don't know if this is related, but I'm getting "software rasterizer" with "glxinfo | grep render" instead of hardware rendering with my graphics card. It could be related to the fact that I don't have an xorg.conf file, but I read somewhere that kernel mode-setting should be able to figure things out without one.

In any case, I'll try re-installing with a live cd.
I have the same problem you have with software rasterizer.  Were you able to get 3D acceleration working again?  If so, how?

---

### Post by linuxnoob420 on 2010-05-01
My Imac g4 1.0 ghz wont even boot into the beta I will try the full release today 
the beta just gets a blank screen IDK??

---

