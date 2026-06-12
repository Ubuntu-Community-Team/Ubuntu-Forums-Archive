---
title: "Newbie..Network Problem.."
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by asyraf on 2008-02-07
Hello they..i'm new here..
1 Q to ask..i just installed Ubuntu on VMware..my primary OS is Windows Xp..i've been following all the steps to carefully configured the Ubuntu on that VMware..but one big problem occured when finished the installation which is "I cannot get into the internet from Ubuntu which is my secondary OS"...does anyone know what happen..sometime i able to get into the internet.but it only for a few seconds..then the connection failed..this error appear.."The server take too long to respon"..can anyone help me????..please??...:(

---

### Post by jan quark on 2008-02-07
what is your network card?

run and post the output pls
```

iwconfig
```
```
ifconfig
```
```
sudo iwlist scan
```

```
lshw -C network
```

---

