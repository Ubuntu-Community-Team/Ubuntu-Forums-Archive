---
title: "Pen - thumb drive usb not seen"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Cav-man on 2008-03-30
Hi all,
        any help most appreciated.

I have G.G 7.10 recently installed. I have also recently bought a 2gb Kingston usb pen drive which automounts fine on a red hat box as well as xp. 
On my new G.G. install, other pen drives automount no problems, but the Kingston is not seen?
It does not appear on fdisk -l. It has the FAT32 filesystem on it.
When i perform the command mesg | tail : i get :

[ 8520.609999] sd 5:0:0:0: [sda] Attached SCSI removable disk
[ 8520.610098] sd 5:0:0:0: Attached scsi generic sg0 type 0
[ 8520.637820] usb 2-1.3: new full speed USB device using uhci_hcd and address 30
[ 8520.733759] usb 2-1.3: device descriptor read/64, error -32
[ 8520.932587] usb 2-1.3: device descriptor read/64, error -32
[ 8521.124425] usb 2-1.3: new full speed USB device using uhci_hcd and address 31
[ 8521.535381] usb 2-1.3: device not accepting address 31, error -32
[ 8521.625076] usb 2-1.3: new full speed USB device using uhci_hcd and address 32
[ 8522.035118] usb 2-1.3: device not accepting address 32, error -32
[ 9524.111823] usb 2-1.4: USB disconnect, address 28

I have tried the following modprobe commands with no success:

sudo modprobe -r ehci_hcd

 sudo modprobe ehci_hcd

Any ideas??

Regards

Chris

---

### Post by Duck2006 on 2008-03-30
After you last use it did you do a safe remove with it, or just unplug it?

---

### Post by Cav-man on 2008-03-30
> **Duck2006 said:**
> After you last use it did you do a safe remove with it, or just unplug it?

It has never worked in my G.G. box so it was not mounted to be able to unmount when pulling it out.
When using on the redhat machine yes i did remove it properly as with the Win XP box. There is nothing wrong with the Pen drive itself. I am not sure what to do ??
Any ideas?

---

### Post by Cav-man on 2008-03-31
Can anyone help with this??

---

### Post by hyper_ch on 2008-03-31
if you start gparted, is the device listed there?

---

### Post by Cav-man on 2008-03-31
> **hyper_ch said:**
> if you start gparted, is the device listed there?

No, the device is not listed in gparted, only the 80 gb IDE hd. Any ideas?

---

### Post by Cav-man on 2008-03-31
Anyone else got any ideas on this one??

---

### Post by Cav-man on 2008-04-05
I am still checking this thread in case anyone can help on this one.

---

