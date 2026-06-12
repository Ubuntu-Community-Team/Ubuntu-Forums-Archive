---
title: "Simple file server"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by pminmo on 2006-10-24
I want to setup a minimalist file server.  i.e. Intel PC box with harddrive, wired network, with an older PC.  Administration from a network connected PC. Installation and setup can have the necessary extra hardware, cd drive, usb drive, keyboard, monitor, mouse....
It would be great to just download an iso cd file and boot and go for installation, but is probably asking too much...A http administraion for the server would be ideal...with a gui second and command line 3rd..

Is Ubuntu server the way to go, or some other linux server software more suited?

Thanks

---

### Post by PriceChild on 2006-10-24
If you only want to serve files to a local network I would advise a standard install of Ubuntu

Then set up a samba fileshare.

Pricey

---

### Post by hyper_ch on 2006-10-24
if you want to operate a pure server then I rather recommend debian sarge 3.1 (or wait until december until debian 4 comes out (although there are rumors it's going to be released some time in the 1st quarter of 2007).
Anyway, upgrade from 3.1 to 4 shouldn't be any problem.

However you stated it should support a usb drive. I'm not sure how well debian handles usb... normally debian servers don't have a keyboard or mouse or such things :) at least the one I rented has nothing.

As for your file server: You want to have it more like ftp or http? Or shall it be accessible directly in the local network from Windoze clients?

If you just want to setup a linux box and have it share a drive in a lan network with windoze clients then I would go for samba.... there's also a gui tool for configuring it but I just forgot its name...

Well, if you could be more specific what you actually want to do then I or someone else could give you better advice...

---

### Post by Bachstelze on 2006-10-24
As far as servers go, Ubuntu is pretty much the same as Debian. I've used both and didn't notice any major difference except the use of sudo.

I also recommend a FTP server, standard protocol, will never ever fail on you. Unlike Samba which I've found to be problematic from time to time. USB drives shouldn't be a problem but you'll neet to mount them manually, good opportunity to learn how to use the mount command ;)

And as a FTP server, I definitely reccomend vsftpd.

---

### Post by PriceChild on 2006-10-24
> **HymnToLife said:**
> USB drives shouldn't be a problem but you'll neet to mount them manuallyI don't have to...

---

### Post by Bachstelze on 2006-10-24
Well, last time I checked, when running a "pure" server (i.e. with no GUI), you have to. I might be wrong though...

---

### Post by PriceChild on 2006-10-24
Ah ok, it might be a gnome feature.

---

### Post by pminmo on 2006-10-24
Its just a home network, other family members will be using winXP so I want to map it as a network drive for them to share files.

Basically unplug all assets except network and CPU/drive box and let it run 24/7.  Network is behind a firewall and encrypted.

I really don't need ftp, or a http server.

I don't need usb, just brought it up as an option.

so it's a box with a motherboard /power supply/ hard drive when functioning and the motherboard has wired network capability and video.

---

### Post by dca on 2006-10-24
On sourceforge, there was an OS or something called 'FreeNAS'.  That might be what you're looking for...  [http://sourceforge.net/projects/freenas/](http://sourceforge.net/projects/freenas/)
 
Also, going the Ubuntu full vers (not Ubuntu server ed.) was good advice, too.  There was a utility that used to be included w/ Fedora Core -- WebAdmin utility was good for remote set-up & access....

---

