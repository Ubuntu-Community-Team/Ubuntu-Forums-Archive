---
title: "What now"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2008-04-16
Have this pci audo: CMI8738. Went to their web & found they have a linux driver. Told me to visit:alsa-project where i downloaded the drivers. Now what do i do? TIA

---

### Post by Tatty on 2008-04-16
Ok firstly do you need to install any drivers?  Ubuntu comes with Alsa by default and your audio drivers should be auto-detected.  If you do not hear any sound then i would advise simpler troubleshooting methods first.

If you are certain that you need to install your drivers, then could you give us some info about what you have downloaded, as there are seveal methods of installing things in linux.  is it a tar?  If so, have a look inside and see if it comes with instructions on how to install.  If it says you need to compile it from source then see this link...

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

i also reccomend having a look at using checkinstall when compiling...
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by jtmedin on 2008-04-19
I have no sound from my sound card. I had asked for help in debuging but got no response so thought i should install the drivers.

---

### Post by jtmedin on 2008-04-19
The drivers are *tar.bz2 & their were libs, firmware, oss, tools, plugings & utils also available.

---

### Post by zvacet on 2008-04-19
Applications<accessories>terminal

```
sudo aptitude install rar unrar p7zip p7zip-full
```

After that just right click on package and select **unpack here**.That will create folder.In that folder you will find install file with instructions.

---

### Post by jtmedin on 2008-04-23
Ok thanks, did the sudo ... & got a lot of work done with no errors that i could see. Still no sound ;-(. Went to prefereces -> sound & tried several of the devices they sugessted but no banana. Should i reboot ? TIA

---

