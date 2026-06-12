---
title: "How do I get unrar"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Chaoswarrior100 on 2006-07-02
How do I get unrar? Can I download it off of apt-get or do I have to download it from a website?

---

### Post by 23meg on 2006-07-02
```
sudo apt-get install unrar-free
```or```
sudo apt-get install unrar
```for the non-free version. To find out yourself you could have done ```
apt-cache search unrar
```

---

### Post by aysiu on 2006-07-02
Step 1. Extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Step 2. Install unrar:
```
sudo aptitude update
sudo aptitude install unrar
```

---

### Post by aysiu on 2006-07-02
**Edit**: Never mind. I'm an idiot and read 23meg's post incorrectly.

---

### Post by Chaoswarrior100 on 2006-07-02
When I type it in it says it cant find the package.

---

### Post by aysiu on 2006-07-02
[QUOTE=Chaoswarrior100]When I type it in it says it cant find the package.[/QUOTE]
That's because you missed Step 1, which was enabling extra repositories.

---

### Post by patrick295767 on 2006-07-03
also, to make use of it:
to unrar  a rar package, cmd line:
```
unrar e thispackagetounrar.rar
```

---

### Post by _simon_ on 2006-07-03
I used this method:

[http://www.ubuntuforums.org/showpost.php?p=1074222&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1074222&postcount=8)

> 
If you want the best rar support in linux, get the original rar form rarlabs.com, here:

[http://www.rarlabs.com/rar/rarlinux-3.6.b4.tar.gz](http://www.rarlabs.com/rar/rarlinux-3.6.b4.tar.gz)

In this archive you only need the file "rar"; copy it to /usr/bin

You can then handle all rar files up to the lastest versions with the archive manager.


---

### Post by jethro10 on 2006-07-03
[QUOTE=23meg]```
sudo apt-get install unrar-free
```or```
sudo apt-get install unrar
```for the non-free version. To find out yourself you could have done ```
apt-cache search unrar
```[/QUOTE]

Im a little stuck on this. The non free version IS free, surley?

Jeff

---

### Post by aysiu on 2006-07-03
*non-free* means it's proprietary. You still don't have to pay  money for it.

---

### Post by patrick295767 on 2006-07-05
I did thsi to get everthg workign fine for me & my daily needs:
 
```

### packing
apt-get -f -y install 
apt-get -f -y install unzip
apt-get -f -y install bzip2
apt-get -f -y install gzip
 apt-get -f -y install unrar rar zip 
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install arj
apt-get -f -y install lha
# to unpack tar xvzf file.tar.gz
apt-get -f -y install 


```

---

### Post by lzfy on 2006-07-15
> **_simon_ said:**
> I used this method:

[http://www.ubuntuforums.org/showpost.php?p=1074222&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1074222&postcount=8)

Finally I got it working :eek:   Thanks a lot...

---

