---
title: "Is there any problem installing Ubuntu somewhere else than on hda?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-01
Hi,

the internal harddisk on which Ubuntu is installed is usually called hda and most people performing a standard install will get Ubuntu installed on a partition of hda like hda1 etc. My situation is slightly different: Ubuntu is installed on the internal harddrive of my laptop but instead of hda this drive is named sda (Ubuntu is installed on sda1). 

This doesn't appear to be a problem but recently I checked the /etc/acpi/sleep.sh script for suspend and saw that there were some references to /dev/hda....so I guess that's not good! Here are a few commands that get performed on /dev/hda while they should be /dev/sda on my system:

hdparm -w /dev/hda
hdparm -C /dev/hda
hdparm -d 1 /dev/hda

I thought about substituting hda with sda but I fear that this situation is not limited to this file unfortunately. Suspend seems to work fine but I don't what this hdparm command is supposed to do. Probably it is important but it is not applied to my harddisk since it is /dev/sda and not /dev/hda.


Do you know if this is normal or if I should absolutely install Ubuntu on a harddisk called hda and nothing else??? I hope I don't have to reinstall everything...

Thanks




PS:
By the way my harddisk got named sda because I did the installation from a LiveUSB (copy of LiveCD on an external USB disk). When in the LiveUSB the internal harddisk of my laptop is seen as /dev/sda while the external USB disk is /dev/sdb

---

### Post by dstew on 2007-05-01
If it works, don't worry about it. I think the system can map the hda's onto sda's.

---

### Post by kilou on 2007-05-01
Thanks for the reply. Well it works but suppose that the hdparm command is a safety feature when suspending the computer so I'd like to make sure it is OK. Is there anyway to check if hda is mapped onto sda? It guess it is not because on a normal install hda is the internal harddisk while sda is an external one.....

Another "issue" with that is with laptop mode and the control of harddisk spindown. In /etc/laptop-mode/laptop-mode.conf it seems that hdparm is used for hda devices while sdparm should be used for sda devices....... I've seen that while on battery and with laptop mode enabled, my harddisk stops spinning only after a couple of secs and have to restart spinning up always when I click somewhere etc. This is probably due to this sda vs hda "mess".

I've read that before kernel 2.6 SATA harddrive were assigned hda and after kernel 2.6 they were sda. However my laptop harddrive is IDE not SATA (at least I suppose...). In Edgy (installed from a LiveCD, not from LiveUSB) my laptop harddrive was hda.....

Should I reinstall Feisty to solve this??

---

### Post by kilou on 2007-05-01
From what I could read up to now sda is used for SCSI drives while hda is used for IDE drives. I guess that running an IDE drive as SCSI will probably degrade performances no???

---

### Post by dstew on 2007-05-02
I remember from trying to understand CDRecord that many drives are actually SCSI at heart, but the controllers repackage the drive instructions. I guess that Feisty is using kernel software that treats all drives as SCSI, and the kernel software will translate drive instructions into whatever the hardware needs. So, no, I do not think  there will be any performance issues. I am pretty sure that any hda's in older software will be translated appropriately by the kernel into sda's. Maybe some kernel guru could explain better.

---

### Post by kilou on 2007-05-02
Well apparently there is a new "stuff" in Feisty called libata and this makes all IDE drives seen as sda :confused: My question is then: does everybody here using Feisty have sda and no more hda hard drive???? If this libata is effectively changing hda into sda, why does the suspend script (sleep.sh) have references to hda in the hdparm command? Is this a "bug"?

---

### Post by dstew on 2007-05-02
In my Edgy sleep.sh, all the references to /dev/hda are conditional, that is, the statements are not executed unless /dev/hda exists. I don't know about Feisty. And I think Feisty names all disks sda, sdb etc. No more hda's at all.

---

### Post by mcduck on 2007-05-02
> **kilou said:**
> From what I could read up to now sda is used for SCSI drives while hda is used for IDE drives. I guess that running an IDE drive as SCSI will probably degrade performances no???

Quite the opposite, actually. The change was done because SCSI/SATA driver handled PATA drives better than the old PATA driver did :D

---

