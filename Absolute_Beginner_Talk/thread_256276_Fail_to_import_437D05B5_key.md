---
title: "Fail to import 437D05B5 key"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by fer5437 on 2006-09-12
I try to import the [email]ftpmaster@ubuntu.com[/email] key which is 437D05B5. I get this error> gpg --keyserver subkeys.pgp.net --recv 437D05B5
gpg: WARNING: unsafe ownership on configuration file `/home/fer/.gnupg/gpg.conf'gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


What should i do now?? Please help

---

### Post by Najand on 2006-09-12
Do it again; sometimes it fails and when you do it again it just  works.

---

### Post by fer5437 on 2006-09-12
I had tried it since yesterday and I getting the same error. What is the other opinion to troubleshoot this issue??

---

### Post by Najand on 2006-09-12
Hmm, are you behind a proxy?

---

### Post by fer5437 on 2006-09-14
Yes, I using proxy to connect to internet. But I had try this command in terminal root export http_proxy="myproxy". This really break my head. Help Please..

---

### Post by Najand on 2006-09-14
If you are using gnome, set your proxy by clicking:
> System -> Prefrences -> Network Proxy
if you are just using command line and no X server:
After exporting http_proxy="myproxy" add the option 
> "--keyserver-option honor-http-proxy"
to your gpg command.

---

### Post by fer5437 on 2006-09-14
I got this after add the option in> root@z-cg-fer:/etc/apt# gpg --keyserver-option honor-http-proxy subkeys.pgp.net --recv 437D05B5
gpg: WARNING: unsafe ownership on configuration file `/home/fer/.gnupg/gpg.conf'usage: gpg [options] [filename]
root@z-cg-fer:/etc/apt#


So what is this mean? I successfully download the key or not? Thank you for your fast respond.

---

### Post by Najand on 2006-09-14
Use sudo, not root user...
Use:
```

gpg --keyserver-option honor-http-proxy --keyserver subkeys.pgp.net --recv 437D05B5

```

---

### Post by fer5437 on 2006-09-17
Najand, I still get the same error when I use sudo right
> fer@sdd:~$ sudo gpg --keyserver-option honor-http-proxy --keyserver subkeys.pgp.net --recv 437D05B5
gpg: WARNING: unsafe ownership on configuration file `/home/fer/.gnupg/gpg.conf'gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

Without using sudo I get this
> fer@sdd:~$ gpg --keyserver-option honor-http-proxy --keyserver subkeys.pgp.net --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpgkeys: HKP fetch error: eof
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
fer@sdd:~$

What can I do next??

---

### Post by Najand on 2006-09-17
Oh, yeah.... Gpg does not need any "sudo", because you must import it as your own username.
There s no GPG key available in that server... Look to find some other servers to find the right key...

---

### Post by scotte on 2006-09-25
I was having this same problem, and it turns out to be some weird behavior on our corporate proxy, but I was able to get around it by using the "broken-http-proxy" option, like this:

gpg --keyserver hkp://subkeys.pgp.net --keyserver-options http_proxy=http://MY_PROXY:MY_PORT,honor-http-proxy,broken-http-proxy --recv THE_KEY

Hope this helps!

---

### Post by ChoMar on 2006-10-30
Am having the same problem here. The server has the key 
(you can just enter the key in the extraxt option at [http://subkeys.pgp.net/](http://subkeys.pgp.net/) (dont forget 0x before key in search field)
but the system keeps telling me about an eof error, wich means End of File, if i remember correctly. Thats STUPID, because the file is ok and all.
Oh, and im not using proxies.

---

