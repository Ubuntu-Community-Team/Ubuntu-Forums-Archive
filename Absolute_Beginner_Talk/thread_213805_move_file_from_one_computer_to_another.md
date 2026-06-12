---
title: "move file from one computer to another"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-07-11
hi; i want to download fwcutter to my desktop, then transfer to my laptop (which cannot go online).  What's the best way to do this?

thanks,
-steve

---

### Post by briguy on 2006-07-11
USB drive, if you have one (and USB ports on both computers).

---

### Post by stalker145 on 2006-07-11
> **stevieb@verizonmail.com said:**
> hi; i want to download fwcutter to my desktop, then transfer to my laptop (which cannot go online).  What's the best way to do this?

thanks,
-steve

I, personally use a flash drive. You could also burn it to a CD if you don't mind using up all that space.

---

### Post by bigken on 2006-07-11
personaly I would buy a usb caddy cheap as chips

---

### Post by stevieb on 2006-07-11
and how do i tell synaptic package manager to put it on my usb drive?  i've downloaded it but "find" doesn't show it.  and how do i tell my laptop spm to look for it on the usb?

thanks,
-steve

---

### Post by briguy on 2006-07-12
I see what you're trying to do.  Go to this site [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_20060108-6build1_i386.deb&md5sum=a86e66aba8afc1a7ba1c872ae4192a57&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fb%2Fbcm43xx-fwcutter%2Fbcm43xx-fwcutter_20060108-6build1_i386.deb&md5sum=a86e66aba8afc1a7ba1c872ae4192a57&arch=i386&type=main) and download the deb file, put that on your usb key, to install it on your laptop put the file somewhere and in that same directory do

```
sudo dpkg -i bcm43xx-fwcutter_20060108-6build1_i386.deb
```

You may have to do the same thing for any dependencies fwcutter has, they are listed on this site [http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter)

---

### Post by Brunellus on 2006-07-12
USB drives, and a protocol we used to call "Sneakernet" :-P

you'd have to download all the individual .deb files you need, and install them manually using 

sudo dpkg -i packagename

if possible, make a note of what packages depend on what other ones, and install in dependency order.

---

