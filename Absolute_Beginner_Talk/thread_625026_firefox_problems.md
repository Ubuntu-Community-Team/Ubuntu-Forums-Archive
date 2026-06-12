---
title: "firefox problems"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-11-27
I have been using ff 2.0.0.5 and figured it was time to update.. for whatever reason, I've never been able to click on the "check for updates", it's always greyed out. When I first installed ubuntu, ff was giving me issues before and I used the ubuntuzilla script. My ff has been crashing like mad lately though so I figured I should update. Went and dl'd the tar, unpacked it, backed up my favorites and uninstalled the previous version. Now though it doesn't want to open. Every time I click on ff it just goes like it's loading and then disappears?!? Anyone have any ideas on what to try? Is the previous ubuntuzilla script messing with things? I'm just at a total loss on what to do next now.. checked these forums, ff's forums, googled and still no luck! :( Thanks guys!!

---

### Post by angryfirelord on 2007-11-27
Why not just update through the Ubuntu repos instead?
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
Or, if you un-installed it already:
```
sudo apt-get install firefox
```

---

### Post by nanotube on 2007-11-27
> **andyho said:**
> I have been using ff 2.0.0.5 and figured it was time to update.. for whatever reason, I've never been able to click on the "check for updates", it's always greyed out. When I first installed ubuntu, ff was giving me issues before and I used the ubuntuzilla script. My ff has been crashing like mad lately though so I figured I should update. Went and dl'd the tar, unpacked it, backed up my favorites and uninstalled the previous version. Now though it doesn't want to open. Every time I click on ff it just goes like it's loading and then disappears?!? Anyone have any ideas on what to try? Is the previous ubuntuzilla script messing with things? I'm just at a total loss on what to do next now.. checked these forums, ff's forums, googled and still no luck! :( Thanks guys!!

to see why it's failing to start, open a terminal, and run command
```
firefox
```
from there, that will let you see some error output, if any.

also, try starting with a fresh profile - frequently ff problems are due to various cruft that's built up in the profile over time.

---

### Post by andyho on 2007-11-27
> **angryfirelord said:**
> Why not just update through the Ubuntu repos instead?
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
Or, if you un-installed it already:
```
sudo apt-get install firefox
```

Yeah I figured I would just try to install from the repos first, but when I did that it stated ff was already installed?! Even though I had just uninstalled and rebooted the machine. When that didn't work is when I went to the tar file. If I do sudo apt-get dist-upgrade, that's going to update me to gutsy right?! I didn't want to do that just yet as I've been reading the forum people have had minor issues here and there with it so I was kinda just waiting it out to update the distro. Feisty's been fine for me. ;)

> **nanotube said:**
> to see why it's failing to start, open a terminal, and run command
```
firefox
```
from there, that will let you see some error output, if any.

also, try starting with a fresh profile - frequently ff problems are due to various cruft that's built up in the profile over time.

I get...

andyho@andyho-ubuntu:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 169
   Major opcode:  147
   Minor opcode:  3
   Resource id:   0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
   Major opcode:  147
   Minor opcode:  3
   Resource id:   0x0
Failed to open device
Segmentation fault (core dumped)

---

### Post by andyho on 2007-11-27
Ok.. well not exactly sure what I did other than editing the menu item, but it's working now and it's the correct version!?! I just checked in the terminal too and there's no error now either... Someday I'll get all this linux stuff down!! \\:D/

---

