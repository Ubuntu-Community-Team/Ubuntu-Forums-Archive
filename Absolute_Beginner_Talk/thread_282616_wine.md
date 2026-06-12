---
title: "wine"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-23
If I want to run internet explorer from wine, how do I launch it? I tried going into the command line and typing sudo wine internet explorer and it didn't work.... I'm just trying to use shockwave web sites. I have heard VMWARE can do this but I don't know squat about it either....:rolleyes:

---

### Post by bodhi.zazen on 2006-10-23
> **saintj0n said:**
> If I want to run internet explorer from wine, how do I launch it? I tried going into the command line and typing sudo wine internet explorer and it didn't work.... I'm just trying to use shockwave web sites. I have heard VMWARE can do this but I don't know squat about it either....:rolleyes:

```
wine /home/user_name/.wine/c/Program\ Files/Internet\ Explorer/iexplore.exe
```

---

### Post by jorn on 2006-10-23
I have just installed ie from here:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
but that's not through wine.

---

### Post by hyper_ch on 2006-10-23
There's a wine howto in the howto section.

If you want MSIE you can - as you have pointed out - also use vmware. But those two are totally different. With vmware you create a virtual OS within your ubuntu distro. You will be running like two computers on one. If you have a dual processor then I probably advice you to go for vmware. I use it myself on a 1.6 ghz amd athlon with 1 gb dd ram.

However if you have lower specs on your computer you may want to go for wine.

---

