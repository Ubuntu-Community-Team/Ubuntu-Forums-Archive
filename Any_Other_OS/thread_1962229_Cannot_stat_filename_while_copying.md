---
title: "Cannot stat filename while copying"
date: 2012-04-20
forum: Any Other OS
---

### Post by pmorton on 2012-04-20
I wish to copy a directory structure from a USB drive to a sata local drive. I get the following error message for a number of files:

cp: cannot stat `/media/disk3part1/mydirectory/my_file-name': No such file or directory'

The files nevertheless exist. Does anyone know what could be causing this?


(please ignore thread prefix - I'm using Ubuntu 11.10 - don't know why I have to add an irrelevant prefix to post!)

---

### Post by |{urse on 2012-04-20
Can you post the actual cp command you issued before recieving that error?

---

### Post by pmorton on 2012-04-20
> **|{urse said:**
> Can you post the actual cp command you issued before recieving that error?

Yes. Here it is:

root@TonidoPlug2:/media/disk1part1/Indi/off_office_NAS#   cp -r /media/disk3part1/* ./

---

