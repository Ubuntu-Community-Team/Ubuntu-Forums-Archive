---
title: "No graphics driver or wifi..."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by richiboy on 2008-03-01
It wont enable my ATI accelaration drivers but it knows my GFX card is there but wont enable?

Plus I have no WIFI, although i know there is a big problem with WIFI with Ubuntu.

Is there any one that could help me on this as im totally new to Linux and Ubuntu and im not going to give up on the move to this OS, going back to shitty Vista would be to easy to do. Thanks all.

---

### Post by mikeyphi on 2008-03-01
> **richiboy said:**
> It wont enable my ATI accelaration drivers but it knows my GFX card is there but wont enable?

Plus I have no WIFI, although i know there is a big problem with WIFI with Ubuntu.

Is there any one that could help me on this as im totally new to Linux and Ubuntu and im not going to give up on the move to this OS, going back to shitty Vista would be to easy to do. Thanks all.

Do you have a working Internet connection?

Have you enabled all the repos under System/Administration/Software Sources?

What do you see when you open System/Administration/Restricted Drivers Manager?

What wifi card do you have?

---

### Post by jan quark on 2008-03-01
please post the outgput from these terminal commands
```

lspci
```

```
sudo lshw -C network
```
```

iwconfig
```

```
sudo iwlist scan
```
```

cat /etc/network/interfaces
```

---

