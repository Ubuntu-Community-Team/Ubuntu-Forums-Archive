---
title: "Help Me PLzzzzzzzzzzz!!!!"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by arunmvishnu on 2005-11-22
Today i got Ubuntu 5.10:KS  CD and i installed it. My serial mouse is configured by the help from ubuntu wiki:D . I mounted my FAT32 and NTFS disks;) . But now i need help for :( 
1) Configuring D-Link V/D/F modem(internal). Iam using Conexant Soft56k Data Fax Voice SpearkPhone driver in XP.
2) How can i install XMMS, XINE and its MP3 and other plugins by downloading those packages using windows. 
3) My printer Canon Pixma ip1000 is not dected. So i need its driver.

---

### Post by Brunellus on 2005-11-22
1) It's a softmodem and therefore depends on Windows.  Linux support for this sort of modem is poor.

Having said that:  do you dial-up for internet access?  

Xine and XMMS are available in the universe repository.  Follow these directions for adding the repositories:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

And then install xine and xmms using synaptic.

Multimedia codecs are not distributed with ubuntu for legal reasons.  But if you want to find out about how to get them, refer to the RestrictedFormats wikipage:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

I don't know much about printer drivers;  someone else will have to answer that.

(PS: try to be more descriptive in your subject-field.  We are here to help.  Just ask us what you need to know and we'll see what we can do.  )

---

### Post by Axeface49 on 2005-11-22
I did a google search for canon printer drivers and found this website, its not in english but you might be able to download the .rpm's and use alien to convert them to .deb

No Guarentee's as I'm new to linux myself but.. I suppose its worth a try... :)

Feel free to correct me if I'm wrong

[http://aris.pituruh.com/2005/09/06/instalasi-driver-printer-canon-pixma-1000-di-linux/](http://aris.pituruh.com/2005/09/06/instalasi-driver-printer-canon-pixma-1000-di-linux/)

```

alien <file.rpm>
sudo dpkg -i <file.deb>

```

Edit: I also did a search for conexant drivers

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

They might work... Again.. no guarentees.. :)

Hope this helps,
Axeface

---

### Post by arunmvishnu on 2005-11-23
hi,
 Thank you guys. Iam writting this post in linux. But one problem is since the modem driver from the Linuxant is free, they gve only 14.4kbps speed. I cannot spend 19$ for buying its licence. 
Now iam  adding the repositories. The downloading speed is very less, 2kbps. I installed alien and downlaoding printer driver. Thank you verymuch for ur help.

---

