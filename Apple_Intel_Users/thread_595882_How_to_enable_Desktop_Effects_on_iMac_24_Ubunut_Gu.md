---
title: "How to enable Desktop Effects on iMac 24 Ubunut Gutsy 64 bit"
date: 2007-10-29
forum: Apple Intel Users
---

### Post by vikramsharma on 2007-10-29
I have installed the latest drivers andn everything seems to be working alright, I have the ATI control manager install, I get the right info when I give the command "flgrxinfo",but I am not able to enable the Desktop Effects.  I am also not able to install Beryl on the Ubuntu Gutsy 64 bit, anything I am missing, I have installed emerald and in the startup sessiom I have included "compiz --replace" and  "emerald  --replace".  Please guide me, I have 3 iMac desktop machines in my office, one is running the 32 bit version of Gutsy without any problem and all the effects enabled.  I am only having problems enabling Desktop Effects on the 64 bit version of Ubuntu Gutsy on iMac 24.

The specs of my iMac are 2 GB RAM, 2.4 GHz with 256 MB ATI 2600 pro graphics card.

Thanks in advance guys.

---

### Post by FunkyM on 2007-10-29
I also got this issue and I think the resolution of 1960x1200 is what makes it fail despite having setup everything correctly (tried both XGL and AIGLX methods, nothing works). Seems as if only ATI can fix it. If anyone has got it working though... please scream out loud!

---

### Post by cyberdork33 on 2007-10-29
First make sure that you have installed XGL.

```
sudo aptitude install xserver-xgl
```

---

### Post by vikramsharma on 2007-10-31
> **cyberdork33 said:**
> First make sure that you have installed XGL.

```
sudo aptitude install xserver-xgl
```

Sorry for the delayed reply, in haste I had forgotten to install xserver-xgl after installing it all the desktop effects were working fine.  I took me quite sometime to figure out how to install the latest 64 ati drivers.  Thanks a lot man.

---

### Post by cyberdork33 on 2007-10-31
> **vikramsharma said:**
> Sorry for the delayed reply, in haste I had forgotten to install xserver-xgl after installing it all the desktop effects were working fine.  I took me quite sometime to figure out how to install the latest 64 ati drivers.  Thanks a lot man.
yes they are a pain. Especially on 64-bit.

---

