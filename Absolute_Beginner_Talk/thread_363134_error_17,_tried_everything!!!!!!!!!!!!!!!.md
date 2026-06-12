---
title: "error 17, tried everything!!!!!!!!!!!!!!!"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-02-16
i installed ubuntu onto an external usb harddrive and at the end of the installation i restarted the computer as it said. 

i went into the BIOS and booted from the external harddrive and grub started. i was given all of the options i had to boot.

I then selected ubuntu and i got Error 17

I then booted from the live cd and i went through the procedure to restore GRUB, it said it was sucsessful but on restart i didn't work.

PLEASE HELP!!!!

i've been trying to solve this problem for 2 days.

I AM A [B][U]SUPPER NOOB[U][I][B] to linux, so any and all help is appreciated but plz keep it in simplist terms plz!!!!

thanks[/B][/I][/U][/U][/B]

---

### Post by cobra0289 on 2007-02-16
> **gameman12 said:**
> i installed ubuntu onto an external usb harddrive and at the end of the installation i restarted the computer as it said. 

i went into the BIOS and booted from the external harddrive and grub started. i was given all of the options i had to boot.

I then selected ubuntu and i got Error 17

I then booted from the live cd and i went through the procedure to restore GRUB, it said it was sucsessful but on restart i didn't work.

PLEASE HELP!!!!

i've been trying to solve this problem for 2 days.

I AM A [B][U]SUPPER NOOB[U][I][B] to linux, so any and all help is appreciated but plz keep it in simplist terms plz!!!!

thanks[/B][/I][/U][/U][/B]

You probably are using the default "Use entire disk" to install.  Use Gparted during install to make several smaller partitions.  The firdt being about a 20 mb primary partition and make it the /boot partition, then a swap , then a root "/", then a "/home" partition.  That should take care of it.

---

### Post by gameman12 on 2007-02-16
.

---

### Post by gameman12 on 2007-02-16
wasn't sure how to do that........sry

---

