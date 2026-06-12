---
title: "Firewall in Ubuntu?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by bolognese on 2006-11-15
Hello,

Could anyone tell me if tehre is a firewall in Ubuntu and how I can enable (or disable) it.

Thanks. B

---

### Post by doh224 on 2006-11-15
don't care for firewall. just get a antispyware and a antivirus. but I can't help you find.I have trouble my self and can't get an answer..

-doh

---

### Post by nickpaton on 2006-11-15
iptables is the firewall application which is installed by default.

A GUI called Firestarter is available which can be installed via Synaptic or Automatix2.

From within Firestarter you can enable or disable the firewall.

---

### Post by nickpaton on 2006-11-15
> **doh224 said:**
> don't care for firewall. just get a antispyware and a antivirus. but I can't help you find.I have trouble my self and can't get an answer..

-doh

It is not necessary to get antispyware or antivirus for Linux, since the file structure makes it almost impossible for the OS to be attacked.  There are many more detailed posts about this.

The only reason you may want to get antivirus is if you receive emails from a Windows PC and you then pass it onto another Windows PC.  What you are doing is to simply clean any Windows based virus's.

---

### Post by wieman01 on 2006-11-15
Try Firestarter as mentioned:
> sudo apt-get install firestarter
To run the GUI for it type:
> sudo firestarter
Bear in mind: It will block all traffic (including DHCP and port 80 - Internet) by default, so don't be surprised if you get disconnected in the first place. It runs at system startup.

Firestarter is basically a daemon with a nice little GUI that configures IP tables. 

[http://www.fs-security.com/docs/introduction.php]("http://www.fs-security.com/docs/introduction.php")

---

### Post by jd65pl on 2006-11-15
To run guis as root from CLI shouldn't the command below be used?

```
gksudo *command*
```

---

### Post by wieman01 on 2006-11-15
> **jd65pl said:**
> To run guis as root from CLI shouldn't the command below be used?

```
gksudo *command*
```
Does not really matter. If you run it from command line, use "sudo". If you create a desktop/menu shortcut, use "gksudo" or "kdesu".

---

### Post by jd65pl on 2006-11-15
> **wieman01 said:**
> Does not really matter. If you run it from command line, use "sudo". If you create a desktop/menu shortcut, use "gksudo" or "kdesu".

I have seen many posts which advise the opposite. These links also explain why.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://www.ubuntuforums.org/showthread.php?t=201488](http://www.ubuntuforums.org/showthread.php?t=201488)

---

### Post by nickpaton on 2006-11-15
It's getting off the original topic, but could either of you tell me (& I think many others!) the chapter and verse on sudo versus gksudo.

The only thing I have been told is that if you use gedit or a similar (but not actually specified as to what "similar" means), then it's gksudo.

Thanks!

EDIT: OK it's answered whilst I was posting this!!

---

### Post by jd65pl on 2006-11-15
> **nickpaton said:**
> It's getting off the original topic, but could either of you tell me (& I think many others!) the chapter and verse on sudo versus gksudo.

The only thing I have been told is that if you use gedit or a similar (but not actually specified as to what "similar" means), then it's gksudo.

Thanks!

See above

---

### Post by skymt on 2006-11-15
> **wieman01 said:**
> Bear in mind: It will block all traffic (including DHCP and port 80 - Internet) by default, so don't be surprised if you get disconnected in the first place.

No, not really. Firestarter only blocks incoming traffic by default. Outgoing connections (including web surfing) will still work.

---

### Post by bolognese on 2006-11-15
The reason for my question was that I couldn't get a good connection in aMule and Azureus. But the problem was my modem/router. I also deselected this iptables thing. Downloads are a good now.
It's a good thing to hear that spam might have no chance in Linux.

Thanks for the replies. B.

---

