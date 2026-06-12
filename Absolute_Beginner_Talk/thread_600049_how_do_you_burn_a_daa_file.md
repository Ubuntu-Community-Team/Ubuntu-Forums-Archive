---
title: "how do you burn a daa file?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-11-01
how do you burn a daa file?

---

### Post by Pumalite on 2007-11-01
[http://my.opera.com/sjosul/blog/2007/10/06/poweriso-daa-image-file-in-linux](http://my.opera.com/sjosul/blog/2007/10/06/poweriso-daa-image-file-in-linux)

---

### Post by RRS on 2007-11-01
I used PowerISO a couple weeks ago to make a Win98 restore disc for a friends machine from a .daa file, worked fine.

Here's the commands I used:
```
wget http://poweriso.com/poweriso.tar.gz
```
```
tar -zxvf poweriso.tar.gz
```
```
sudo mv poweriso /usr/bin
```
```
rm poweriso.tar.gz
```
```
poweriso -?
```
```
poweriso convert /"path to folder with .daa file"/"name of .daa file".daa -o /"path to folder"/"name of file".iso -ot iso
```

The first downloads the package, the second unpacks it. The next two moves the unpacked binary and removes the download.

"poweriso -?" opens the instruction manual, so to speak. The final operational command I used above is outlined there.

Use your path and file name where I've shown, don't use the quotation marks. Also, if your file name has any spaces in it replace them with an underline ( _ )

I've converted at least three .daa files to .iso this way and created bootable disks with no problems though I have heard of issues with large (above 2g?) files.

Hope this helps you out.

---

### Post by mkquist on 2008-01-10
RSS thanx for the concise and accurate instructions, worked like a champ!

---

