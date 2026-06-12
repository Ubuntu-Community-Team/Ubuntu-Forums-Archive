---
title: "Wireless does not work MacBook Pro 15"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by hjel on 2007-06-25
hello to all I bought a macbook pro 15" and I cannot make work the wireless if some one  knows pleace tell me. 
Another thing how can i know if my computer is  32 or 64 bits

specs
intel core 2 duo  2.33 Ghz
120 hd
2GB ram

thanks

---

### Post by david_edmundson on 2007-06-25
Core Duos are 32
Core 2 Duos are 64bit.

It's not the most clear naming convention. As for wireless, search this forum there are loads of topics which help.

---

### Post by ronocdh on 2007-06-25
> **david_edmundson said:**
> Core Duos are 32
Core 2 Duos are 64bit.

It's not the most clear naming convention. As for wireless, search this forum there are loads of topics which help.
Try MadWiFi first, in case that's not clear from the threads you find. There was a time when ndiswrapper was used a lot, but I think MWF is so strong now, that it'll serve your needs completely. You'll have to compile it from source, but as david said, there are plenty of threads on that here. Post if you need additional help.

---

### Post by joselin on 2007-06-25
I wrote [this little howto]("http://tech.kedesfase.com/2007/06/15/configurando-el-wifi-de-mi-nuevo-imac-de-24/") for this (is for my iMac, but i use a MBP howto as reference).

The only thing, is that I wrote it in spanish.

Regards

---

### Post by kzm. on 2007-06-25
worked for me:
```

    sudo apt-get install gcc g++ libc6-dev linux-headers-2.6.20-16-generic build-essential debhelper
    tip: uname -r > kernel versio
    wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
    tar -zxvf madwifi-hal-0.9.30.13-current.tar.gz
    cd madwifi <tab>
    make
    sudo make install
    sudo make clean
    reboot

```

---

### Post by hjel on 2007-06-25
> **kzm. said:**
> worked for me:
```

    sudo apt-get install gcc g++ libc6-dev linux-headers-2.6.20-16-generic build-essential debhelper
    tip: uname -r > kernel versio
    wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
    tar -zxvf madwifi-hal-0.9.30.13-current.tar.gz
    cd madwifi <tab>
    make
    sudo make install
    sudo make clean
    reboot

```

:D:D:D it work great, thank's pall

---

### Post by david_edmundson on 2007-08-19
If you are running Gutsy (Kernel 2.6.22), and find you get errors when running "make", you will need to apply this patch to the source.

[http://madwifi.org/attachment/ticket/1315/141-Madwifi-fixes.patch](http://madwifi.org/attachment/ticket/1315/141-Madwifi-fixes.patch)

---

