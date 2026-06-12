---
title: "YPOPs and WWWOFFLE proxy (Kubuntu/Kmail)"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by rivkaopreis on 2007-10-31
I have installed YPOPs (for POP3 access to Yahoo mail --> [http://ypopsemail.com/](http://ypopsemail.com/)) using the Ubuntu package and instructions from [http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/) The installations went well as far as I can tell but... I am running the WWWOFFLE proxy server and don't know how to configure the proxy settings for YPOPs. The dialog asks me to specify HTTPS Proxy Host; HTTPS Proxy Port; HTTP Proxy Host and HTTP Proxy Port. Randomly searching the WWWOFFLE config files I found that the ports probably are 8443 (https) and 8080 (http) but I don't know what to fill in at the "host" bit of both... is this supposed to be a name or an IP or....?? This is probably a very silly question but I just have no idea about this sort of thing. I tried just filling in "localhost" but that didn't work, Kmail giving me the following error:
Could not login to localhost.
Server does not respond properly:
HTTP/1.0 500 WWWOFFLE Server Error
Does anyone know how to configure this properly???

If not, I would also be happy to just disable WWWOFFLE for a while since I only want to download mail from my Yahoo account once so I can close it (haven't used it for ages but don't want to lose my archive of old mails) but I can't find out how to do that either and uninstalling it seems a bit drastic...

Any suggestions would be more then welcome!!
Thanks very much!

---

### Post by editrix on 2008-06-11
I can't get wwwoffle working at all in Hardy, but I suspect it's a FF problem.

However, there's an extension for FF (if that's what you're running) that puts a button at the bottom of your screen and you can just click to turn the proxy on and off. Works a treat when FF works. Sorry I can't recall the name, but I can't access my FF at all to see what it's called.

---

