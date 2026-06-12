---
title: "telnet"
date: 2011-09-27
forum: Any Other OS
---

### Post by kumarsai on 2011-09-27
my frnds want to use my os(mint) in windos(telnet) environmnt is it posble..
plz hlp me am new to linx platfrm :)

---

### Post by 2F4U on 2011-09-27
Telnet is considered insecure and I would suggest that you use ssh instead.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Perfect Storm on 2011-09-27
Moved to Other OS/Distro Talk.

---

### Post by Dangertux on 2011-09-27
To echo the response earlier SSH would be much preferable. However if you wish you can install telnet on either Ubuntu or Mint (and most other debian based distros) by doing the following.

```

sudo apt-get install telnetd

```Once you install it you would telnet to it from the Windows machine. 

```

telnet 192.168.1.2 

```*192.168.1.2 represents the ip of the linux box

You will then have to provide authentication credentials for the account you wish to authenticate as.

Again telnet is rather insecure, and easily brute forced but it is the direct answer to your question.

---

