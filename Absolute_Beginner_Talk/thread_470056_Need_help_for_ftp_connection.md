---
title: "Need help for ftp connection"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by speedygeo on 2007-06-10
I can't acces a site with FireFTP in Firefox, neider in gFTP.
It mean don't depend on the client.
Can anyone help me?

---

### Post by aktiwers on 2007-06-10
can you ping it typing:
```
ping serveraddress
```in terminal?

I always use Places => Connect to server
to do all my FTP stuff.

---

### Post by taurus on 2007-06-10
Make sure the other machine has ftp server running first.

---

### Post by Jimmyfj on 2007-06-10
Are you behind a firewalled router?

One possible reason for ftp not connecting to server is that you forgot open port 21 in your router. Without port 21 open you cant get responce while any answer will be cut of by the router. In order to connect to my remote ftp-site through my Linksys wireless router (On cable though) I have to have port 21 opened.

---

### Post by speedygeo on 2007-06-10
I have only a default Kubuntu installation without another firewall.
I closed the kNetworkManager too.
The ping result in good, like the browsing of the page.

---

