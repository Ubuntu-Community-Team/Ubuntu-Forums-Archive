---
title: "Gnomad2"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by superskunk on 2006-04-14
I have recently changed to Ubuntu from XP, and I can't get Gnomad2 to recognize my Creative Zen Micro.

```
sudo:~$  wget http://prdownloads.sourceforge.net/libnjb/libnjb-2.0.tar.gz?download
--00:08:55--  http://prdownloads.sourceforge.net/libnjb/libnjb-2.0.tar.gz?download
           => `libnjb-2.0.tar.gz?download'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                ] 12,619        27.84K/s

00:08:57 (27.80 KB/s) - `libnjb-2.0.tar.gz?download' saved [12619]

sudo:~$ ./configure && make && make install && ldconfig
bash: ./configure: No such file or directory
```

Can anyone help me fix this?
Thanks.

---

### Post by ubernoob on 2006-04-14
you need to extract the archive first. Then cd into that before running those commands
```

tar xvzf libnjb-2.0.tar.gz
cd libnjb
./configure
make
sudo make install
ldconfig
```

---

### Post by jimbren on 2006-04-14
In addition to the comment above, there's a good howto on installing gnomad2 here:
[http://ubuntuforums.org/showthread.php?t=33040](http://ubuntuforums.org/showthread.php?t=33040)

---

