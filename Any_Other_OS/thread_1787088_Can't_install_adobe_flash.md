---
title: "Can't install adobe flash"
date: 2011-06-20
forum: Any Other OS
---

### Post by Proxmty on 2011-06-20
I'm using Linux mint and having problems installing flash player 10. Can anyone tell me the best way of doing it? have downloaded the tar.gz file and tried installing it with apt-get install but it just says it can't find the packages...

---

### Post by lovinglinux on 2011-06-21
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by nomko on 2011-06-21
I'm not sure if this package does exist in Mint, but did you looked in synaptic for flashplayer-nonfree? Install that one.
 
Do you need flash for Firefox?

---

### Post by Proxmty on 2011-06-21
@lovinglinux - thanks will try that and see
 
@nomko - yes I looked for flash-plugin non-free, it's even there but I just get error messages when I try to install it (sorry am not at the linux machine so can't say which message it gives right now)
 
I heard flash came as part of firefox but whenever I go to youtube it says 'you don't have the latest version of flash'

---

### Post by jramshu on 2011-06-21
Nope, flash doesn't come with FF. It should be part of the DVD extras that comes with Mint though.

---

### Post by Darkbird70 on 2011-06-21
I had that problem to, you got to go to **software center** **> adobe flash** **plugin > install **:D

---

### Post by nomko on 2011-06-21
> **Proxmty said:**
> @lovinglinux - thanks will try that and see
 
@nomko - yes I looked for flash-plugin non-free, it's even there but I just get error messages when I try to install it (sorry am not at the linux machine so can't say which message it gives right now)
 
I heard flash came as part of firefox but whenever I go to youtube it says 'you don't have the latest version of flash'
 
What you should do then is this:
 
- open nautilus
- press Ctr+H to see all the hidden files/folders
- go to: .mozilla ==> dot mozilla (this is a hidden folder)
- go to the folder firefox
- go to the folder plugins
- copy the file extracted from the .tar.gz in this folder
 
Start mozilla and type in the navigation bar: **about: plugins **(this is one word, no spaces between about: and plugin)
Scroll down untill you see someting called shockwave flash.
There you can see if Firefox recognized the flashplayer
 
Many users think that the downloaded .tar.gz has to be installed by either using GDebi or by some command. It's just a matter of copy and paste ;)

---

### Post by Perfect Storm on 2011-06-21
Moved to Other OS/Distro Talk.

---

### Post by dockalek on 2012-06-10
> **nomko said:**
> What you should do then is this:
 
- open nautilus
- press Ctr+H to see all the hidden files/folders
- go to: .mozilla ==> dot mozilla (this is a hidden folder)
- go to the folder firefox
- go to the folder plugins
- copy the file extracted from the .tar.gz in this folder
 
Start mozilla and type in the navigation bar: **about: plugins **(this is one word, no spaces between about: and plugin)
Scroll down untill you see someting called shockwave flash.
There you can see if Firefox recognized the flashplayer
 
Many users think that the downloaded .tar.gz has to be installed by either using GDebi or by some command. It's just a matter of copy and paste ;)

@nomko Could you please specify what you should actually copy to the hidden file. Since when I extract the .tar.gz file I have got many folders and have no idea which one is the one I need to copy there. Is it the libflashpayer.so file?
Thanx

---

