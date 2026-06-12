---
title: "Using windows in Vmware server(how to browse my dvd rom drive?)"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-04-04
I want to be able to browse the contents of my cd that is in my dvd rom drive from windows that are running inside the vmware player

i used this config file for vmware emulation
[http://www.ffnn.nl/media/articles/linux/vmware-player-images/template-windows.vmx](http://www.ffnn.nl/media/articles/linux/vmware-player-images/template-windows.vmx)

I am only able to browse only ISO images with this config file

Who can i make it possible to browse my real dvd drive?

---

### Post by hyper_ch on 2007-04-04
I guess you'll have to use VmWare Server.. with that you can edit the settings and hence also assign a physical drive.

---

### Post by mikeyphi on 2007-04-04
I'm running a virtual machine but your setup seems different to mine.....
I don't know what I'm talking about! but try amending the line 

ide1:0.deviceType = "cdrom-image"

to remove the '-image' portion......remember to save the new file!

---

### Post by fasoulas on 2007-04-05
I was able to do it with 

ide1:0.deviceType = "atapi-cdrom"
AND
ide1:0.fileName = "auto detect"

but how can i make my ubuntu partition to be shown as a hard disk in windows?

---

