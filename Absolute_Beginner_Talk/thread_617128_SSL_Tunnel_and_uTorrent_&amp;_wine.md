---
title: "SSL Tunnel and uTorrent &amp; wine"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by bubbalouie on 2007-11-19
Hi all,

I am having a bit of trouble setting up Stunnel with uTorrent on Kubuntu Gutsy. Essentially I have uTorrent running under wine, I want to run the WebUI through SSL as plaintext just bugs me. I have instaled Stunnel, but I can't seem to make it work, here is the command I used:

```
  sudo stunnel -o /home/bubbalouie/Temp/stunnel.log -p utorrent.pem  -c -d 4080 -r localhost:2111
```

I created the utorrent.pem file with the followin command:

```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout utorrent.pem -out utorrent.pem
```

But every time I try to connect there is an error, my stunnel log reports the following:

```
2007.11.19 15:14:25 LOG5[8133:3082890128]: localhost.2111 connected from 192.168.1.69:44754
2007.11.19 15:14:25 LOG3[8133:3082890128]: SSL_connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number

```

What is causing this, my version of openSSL is fully up to date, and I don't seem to have any better luck when I use stunnel4, or stunnel and no *.pem* file.

Any help or advice would be great :)

Thanks in advance...

Ryan

---

### Post by bubbalouie on 2007-11-22
Anyone?

---

