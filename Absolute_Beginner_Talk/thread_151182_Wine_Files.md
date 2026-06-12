---
title: "Wine Files"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by RedKnight on 2006-03-27
HI all,

Hopefully this should be a great first post
I've been using Ubuntu for just under 48hrs now :)

Ref: **Installing and using WIne**

I have managed to locate and tar.gz the following files require by most wine programs "Including Steam"

Microsoft Core True Type Fonts
TahomaTTF
InstMsiA
vbrun60sp5

All files are provided in .exe format and ready to be used with wine.
I have install the "Tahoma.exe" and now my steam account works :)

```
http://www.uklan.net/mscorettfonts.tar.gz
```
```
http://www.uklan.net/InstMsiA.tar.gz
```
```
http://www.uklan.net/TahomaFont.tar.gz
```
```
http://www.uklan.net/vbrun60sp5.tar.gz
```

I will continue to add files on hear when and as I am prompted for them :)

---

### Post by gaberade on 2006-03-27
So... exactly how do I extract it? :]

---

### Post by Kryptizzle on 2006-03-28
You should be able to open it by double-clicking on it.

---

### Post by gaberade on 2006-03-28
I get an error when trying to open these...


gzip: stdin: invalid compressed data--format violated
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by belikralj on 2006-03-28
The error looks to me like your defauld compressor/decompressor is not farmiliar with the extention. Try have a look on the net for the extention and programs that could possibly open it. (I'm probably just saying what you were already thinking).

either that or the format doesn't match the extention which should be unlikely, but possible.

Please anyone, if I'm wrong correct me.

---

### Post by RedKnight on 2006-03-28
If needed I can provide just the plain .exe  files but the tar.gz files seem fine.

Try:

```
tar -tzf filename.tgz
```

This should extract it fine.

---

