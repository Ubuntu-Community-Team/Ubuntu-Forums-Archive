---
title: "Not an ISO9660 image"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-23
I downloaded Fodora when trying to burn the ISO file with K3B I got this message {Not an ISO9660 image} can someone help what is it and how to burn the file.
THANKS

---

### Post by banewman on 2007-11-23
ummm... how did you download... what does your file browser say the file is - 
right click it and select properties. :)

---

### Post by xeth_delta on 2007-11-23
Are you sure the image is not damaged?

Xeth

---

### Post by jmfa59 on 2007-11-23
I did through FTP this is the properties of the file

---

### Post by jmfa59 on 2007-11-23
> **xeth_delta said:**
> Are you sure the image is not damaged?

Xeth

Twice I did it

---

### Post by xeth_delta on 2007-11-23
You could try mounting the image to see if all is OK.

If I recall correctly the syntax should be

[HTML]sudo mount -t iso9660 -o loop image mount_point[/HTML]

Xeth

---

### Post by samuel.rajesh on 2007-11-23
Check the Md5 sum ,i did the same with open suse 10.3 and had a simlar problem ,the md5 sum matched but yet i cudnt write ,i used nero and it worked .

Sam

---

### Post by jmfa59 on 2007-11-23
> **samuel.rajesh said:**
> Check the Md5 sum ,i did the same with open suse 10.3 and had a simlar problem ,the md5 sum matched but yet i cudnt write ,i used nero and it worked .

Sam

The Md5 sum is OK I first tried Nero I was able to burn it , it is not bootable and you can't see what is in it if you explore it and it is full if you check the properties.

---

### Post by exidez on 2007-11-26
i have this problem too, but with an ISO that i created using k3b
When copying the cd i used 'Clone Copy' and not the 'Normal Copy"

The reason why i did this is because some of the files did not show up when i mounted the image (when normal copied), yet they are there on the original disc. The original disc also didn't allow me to view the disc as a normal user, it said i did not have permission. I was allowed only as root. Maybe because this disc is also designed for MAC?
So i used Clone copy to copy the disc (had to be done as root through k3b) but now i cannot mount the image as i get the same problem above. Not an ISO9660 image.

Hopefully someone can give me light on this....
how can i mount his image??? I dont want to waste a disc

$ sudo mount talknow.iso /media/talknow -t iso9660 -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

