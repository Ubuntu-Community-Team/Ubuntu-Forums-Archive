---
title: "Plz help an absolute noob"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by velvet_undies on 2006-10-06
After months of waivering on the idea I finally decided to give linux a try. I chose Ubuntu 6, all seems fine at first glance, it installed really easy (unlike a certain os i'm using now:cool: ) 

One problem i've come across at the moment is trying to get my wifi to work. It seems to recognize that I have a pci wifi card installed as it listed in the network devices bit. I've input things like ip address, gateway ip address, dns info from my router and i've activated it as well but I still cannot get it to work :( 

I've also downloaded what I believe to be the correct drivers for my card incase they weren't installed when I loaded ubuntu, which brings me too my next problem. Just how do I install them? Please, please, please help me out so I can stop doing this ](*,) :-D 

Thanks

---

### Post by Ben Sprinkle on 2006-10-06
Are the drivers .tar, .tar.gz, .bin .exe or what?
To execute .bin or .exe:
```

sudo su
./driverpackage.bin

```

---

### Post by Echo35 on 2006-10-06
lol, just to let you know, wifi support is quite sketchy. What brand and model card is it? Also, what kind of drivers do you have?

---

### Post by velvet_undies on 2006-10-06
> **Goat Spirit said:**
> Are the drivers .tar, .tar.gz, .bin .exe or what?
To execute .bin or .exe:
```

sudo su
./driverpackage.bin

```

The drivers are a tar.gz format

> **Echo35 said:**
> lol, just to let you know, wifi support is quite sketchy. What brand and model card is it? Also, what kind of drivers do you have?

My card is a belkin f5d7000. The drivers I have got are called rt2500-1.1.0-b4.tar.gz.

---

### Post by Ben Sprinkle on 2006-10-06
I need a picture here, what kind of files are in the tar.gz?

---

### Post by velvet_undies on 2006-10-06
Theres a folder inside it. Inside that there are two more folder one called *MODULE* and another called *UTILITYS*. Inside both of these there are various other files.

---

### Post by phido on 2006-10-06
[Perhaps this helps]("http://www.ubuntuforums.org/showthread.php?t=241565&highlight=rt2500-1.1.0-b4.tar.gz")

---

### Post by Ben Sprinkle on 2006-10-06
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi)
Read that for some good info also.

---

### Post by jd65pl on 2006-10-06
You may wish to consider your thread titles a little more in the future. The Stickies at the top of the forum explain this but [here is]("http://ubuntuforums.org/showthread.php?t=259445") a link.

---

### Post by blx_286 on 2006-10-06
This [thread]("http://www.ubuntuforums.org/showthread.php?t=240669") might be helpful also.

---

