---
title: "problem installing proftpd"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by kilbamo on 2006-09-14
when I want to install proftpd in terminal (sudo apt-get install proftpd gproftpd) I get this error:
"E: could not find packet proftpd"

---

### Post by Najand on 2006-09-14
Then it might be avaiable to download, use synaptic or the following in terminal to see if they are available or not:
```

sudo aptitude search <keyword>

```
like:
sudo aptitude search proftpd

---

### Post by kilbamo on 2006-09-14
It doesn't do anything when I type that in terminal.

---

### Post by Najand on 2006-09-14
then it is not avaiiable inside the source websites you are using.
It uses Universe Repository. have you enabled universe Repository in your sources.list?

---

### Post by kilbamo on 2006-09-14
where can I find sources.list? 
yes I'm new with linux

---

### Post by Najand on 2006-09-14
Click on:
System -> Administration -> Software Properties
Then Check the box beside all repositories listed there. (Some of them are unchecked) 
When you are finished, Close it and try:
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install proftpd gproftpd

```

---

### Post by kilbamo on 2006-09-14
Ok it works thx for support

---

### Post by Najand on 2006-09-14
No Problem... We are all here to help, because there is always a situation you need someone to help you too.

---

### Post by kilbamo on 2006-09-14
The ftp server runs but only intern. I can access the server using the [ftp://192.168.XXX.XXX](ftp://192.168.XXX.XXX) adress, but when I fill in the external ip I can't login.
(I can fill in my login details but after a while i get a time-out)

I use an adsl modem with a router, so I forwarded the internal ip.

To configure the server I used the info on [this site (click)]("http://ubuntuforums.org/showthread.php?t=79588").

---

### Post by kilbamo on 2006-09-14
Anyone?

---

