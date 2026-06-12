---
title: "Compile error: checking for crypto++ version &gt;= 5.1... configure: error:"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-02-19
Hi,

And compile aMule like this:
./configure --enable-ccache --with-denoise-level=3 --enable-debug --disable-optimize --enable-verbose --enable-geoip --enable-cas --enable-wxcas --enable-amule-gui --enable-webserver --enable-amulecmd --enable-amule-daemon --with-wx-config=/home/firebox/usr/local/wxWidgets-2.8.7/bin/wx-config --prefix=/home/firebox/usr/local/amule && LD_LIBRARY_PATH=/home/firebox/usr/local/wxWidgets-2.8.7/lib/ make && LD_LIBRARY_PATH=/home/firebox/usr/local/wxWidgets-2.8.7/lib/ make instal

checking for crypto++ version >= 5.1... configure: error:
        Could not find cryptopp header file "cryptlib.h".
        Please check if the path "/usr" is valid.
firebox@firebox-desktop:~/amule-cvs$ 

what does this mean and how do i fix it??

Synaptic says:libcrypto++6  5.5-3

thanks...!!

---

### Post by Crooksey on 2008-02-20
```

$ sudo apt-cache search crypto 
```

There may be a "crypto-dev" package, or something like that you require.

---

### Post by ruy_lopez on 2008-02-20
This is what you are looking for:

```
sudo apt-get install libcrypto++-dev
```

---

