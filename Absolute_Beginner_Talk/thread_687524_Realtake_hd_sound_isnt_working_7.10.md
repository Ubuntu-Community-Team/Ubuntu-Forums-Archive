---
title: "Realtake hd sound isnt working 7.10"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by haxer on 2008-02-04
Got this from doing 

haxer@haxer:~$ lshw -class sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

Have tried different guides with no lead :(  now what to do.

About the beans ..  havent been doing this ubuntu for 2years :)

---

### Post by peterff on 2008-02-10
Hi,

I've got the same soundcard, and installing linux-backports-modules-generic worked for me.

---

