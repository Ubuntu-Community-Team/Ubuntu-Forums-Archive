---
title: "Maximizing DMA"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by dylanknightrogers on 2005-09-24
okay, ive enabled dma with the help of someone else on the forum, but still, my cd-rom and dvd-rom drives are not operating quicly enough.

under Windows, they're fast as hell.

besides actually enabling the dma tag, how can i speed up my drives?  They're kinda slow.

Thanks a googol.

---

### Post by papangul on 2005-09-25
Do you know how to configure hdparm (/etc/hdparm.conf)? This is my relevant portion:

/dev/cdroms/cdrom0 {
	dma = on		   
	interrupt_unmask = on
	io32_support = 1
}
In ubuntuguide there is only instructions about "dma=on", not the other two.

---

### Post by BoHu on 2005-09-25
[QUOTE=papangul]Do you know how to configure hdparm (/etc/hdparm.conf)?[/QUOTE]
 speaking of hdparm, how do get the settings to survive a reboot? I tried -k1 but it doesn't work.

---

### Post by papangul on 2005-09-25
[QUOTE=BoHu]speaking of hdparm, how do get the settings to survive a reboot? I tried -k1 but it doesn't work.[/QUOTE]
 You have to save hdparm setting by entering it in /etc/hdparm.conf

---

### Post by dylanknightrogers on 2005-09-25
Yes, I know how to edit the hdparm.conf file.

One question:  Will the CD-ROM drives burn and copy data as fast as they do under Windows? 

Thanks a billion.

--Dylan

---

### Post by papangul on 2005-09-26
Have you tried to set the /etc/hdparm.conf as above(my first post in this thread), and has it speeded up things?

---

