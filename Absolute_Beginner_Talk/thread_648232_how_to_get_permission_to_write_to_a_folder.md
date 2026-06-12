---
title: "how to get permission to write to a folder"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2007-12-23
Hi all,

I'm trying to get my WinTV-NOVA-TD dual tuner stick to work in Ubuntu 7.10 64-bit.

I've tried all sorts of things from posts on various forums and the consensus seems to be that it should work in Kaffeine player.

When I try to open DVB client in Kaffeine I get a "cannot bind info" socket message.

I found this site:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-TD-Stick)

and that suggests that I need

dvb-usb-dib0700-1.10.fw firmware file  to be in /lib/firmware

I have downloaded

dvb-usb-dib0700-1.10.fw firmware file 

to my desktop but when I try to drag and drop it into /lib/firmware I get a " you do not have permision to write to this folder" message.

How do I do this and does anyone think it will help?

Thanks, John Williams

---

### Post by blueridgedog on 2007-12-23
You may be able to drag and drop with a root enabled version of nautilus:

in a terminal gksudo nautilus

Careful while there...

---

### Post by logos34 on 2007-12-23
> **johnwillyums said:**
> I have downloaded

dvb-usb-dib0700-1.10.fw firmware file 

to my desktop but when I try to drag and drop it into /lib/firmware I get a " you do not have permision to write to this folder" message.

How do I do this and does anyone think it will help?

in the terminal:

**sudo mv** Desktop/dvb-usb-dib0700-1.10.fw /lib/firmware

---

### Post by johnwillyums on 2007-12-23
Hello Logos.

That worked and I,ve now got that file in the /lib/firmware folder.

However it doesn't seem to have made any difference. When I open Kaffeine I get a "cannot bind info socket " message if I ok that I get to a window where I can choose DVB client. 

If I do that and then try to configure I get the "cannot bind info socket" message again.

So I'm no better off. This device works perfectly in Vista 64x it seems such a shame I cannot get it to work in my Ubuntu 64x dual boot.

Thanks for your help. Any other suggestions would be welcome, John Williams

---

