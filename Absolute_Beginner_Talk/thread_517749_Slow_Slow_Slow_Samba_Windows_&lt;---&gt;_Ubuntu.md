---
title: "Slow Slow Slow Samba Windows &lt;---&gt; Ubuntu"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-08-04
ok... i for the life of me cant figure this one out... i've read millions of posts and tried tons of stuff... but it just isnt workin.

I recently aquired a wireless router (linksys wireless g, forget the exact model number) and switch the laptop over from wired to wireless (pretty obvious choice for a laptop)
Before switching samba transfers and file browses were fine... i could watch a video on the laptop from the ubuntu box perfectly and consistantly...
Then, after switching over things went horrible... speeds fluctuated sporratically and never got anywhere near as high or consistant as before. Random fluctuation of 0-500k.
After reading a bunch of posts i tried switchign the ubuntu box over to a newer wireless nic (standard linksys wireless g pci card)... that didnt help.
I went out and bought a new linksys pci adapter for the laptop, thinking that the crappy dell drivers and onboard wireless adapter. No luck there either.
I've added and removed lines from my smb.conf untill it ultimately looks like this
```

[global]
netbios name = SWINEBOX
workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

security = share
restrict anonymous = no
domain master = no
preferred master = no
name resolve order = hosts wins bcast

wins support = yes

[stuff]
case sensitive = no
guest ok = yes
path = /data/
read only = no

```
and still no luck... two new wireless adapters, and just about every suggestion i could find online has gained me a wee bit more stability, but its still not enough to watch/listen/burn anything over the network.

this is really annoying as my machine servers for the entire home network and am brought to an inconsistant uber slow halt. Any suggestions, tips tricks, or tweaks... im open to anything at this point

---

### Post by jimrz on 2007-08-05
seems that, at least on the linux side (from either a win or a linux share and using either wifi or wired connection), you need to mount your samba share on the machine that you want to play the media on for it to work. this drove me crazy, since playing the same type stuff on the win side from ubuntu worked fine, until I found [[COLOR="Sienna"]**_this HOW TO_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473") which works perfectly on each of the several machines that I have used it on. if this does not fix it, you might check and see if ndiswrapper is required to get proper performance out of your lynksys cards and, if so, which version of the windows driver work best for it.

---

### Post by Nythain on 2007-08-05
well... the machine that is doing the playing is a windows machine, the machine serving is the ubuntu box. I have mounted the share as drive letter e on the windows machine already, but it didnt really help much... and as far as installing ndiswrapper... would i really need to. I was under the impression that ndiswrapper was mainly needed if either A. there werent any drivers for your adapter (eg Broadcom chipsets) or B. you needed certain functionality out of your card that wasnt available in the current linux drivers (eg WPA support, wich i dont use, i stick with a simple 128 WEP key, just enough to keep the sicko's and perves off my network)

what program would one use to check for packet loss and or bad packets during transfers. im not yet the most familiar with linux network admin tools.. ifconfig will tell if there have been any but it wont tell me when, where how or why.

any more suggestions, beyond ndiswrapper and mounting from anyone... this problem sucks

---

### Post by jimrz on 2007-08-05
you might check and see if there are any firmware updates available for either your router or card(s). might help

seems I have seen some threads here indicating that there are some cards (sorry, don't remember which) that are recognized OTB and appear to connect but will not function properly until ndiswrapper is applied.

---

### Post by Nythain on 2007-08-05
thanks for the few sugestions... Im Giving Up... this problem is enough to drive even the most zen buddhist monk flip out... guess my roomies cna just bugger off untill i somehow magically get the money to get a new pc... then ill just slap windows back on this one, and serve that way since it just aint happening with ubuntu

---

