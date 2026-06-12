---
title: "Edit sourcelist"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by sod on 2006-02-10
Having a problem with my sourcelist for Synaptic. Got info previus to edit it at sudo gedit /etc/resolv.conf. with:
nameserver 61.1.96.69
nameserver 61.1.96.71
nameserver 192.168.1.1

Then it works. but not permanently. I have to edit it again and again.
Tryed to saved it in all ways I can but no progress.

Idea's anyone?:confused:

---

### Post by TrendyDark on 2006-02-10
That's not your source list, your source list should be at /etc/apt/source.list i believe, try editing that file.

What problem are you having exactly?

---

### Post by Tiede on 2006-02-10
ther right file is source**s**.list. just copy this to a terminal
```
sudo gedit /etc/apt/sources.list


```
and plug in your password and your good to go!

---

### Post by TrendyDark on 2006-02-10
Yeah, soures.list, sorry. I'm not good with remembering that stuff off the top of my head. lol

---

### Post by sod on 2006-02-10
Sorry I dnt descibe it propably. My problem is that Synaptic cannot uppdate and it seems not to be the problem with the source list in it self. In the terninal I can see that the IPs for down loading is not right, think it was 1.0.0.0..port 80 something but when I edit /etc/resolv.conf file it works but not for long

---

### Post by TrendyDark on 2006-02-10
That has something to do with your internet connection. See:

```

search carolina.rr.com
nameserver 192.168.0.1

```

That's the information in my resolv.conf file, I believe the reason it resets the information you enter is because you're connected via DHCP. I'm guessing though, but that is what it looks like.

---

### Post by sod on 2006-02-10
Im using a router with DHCP, is there an other way to edit the file then?

---

### Post by TrendyDark on 2006-02-10
You can connect to the internet, you should be able to update your source lists. I'm not sure what the problem could be (sort of a noob myself, but learning).

---

