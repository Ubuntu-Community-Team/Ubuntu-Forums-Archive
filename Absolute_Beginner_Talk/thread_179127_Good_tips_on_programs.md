---
title: "Good tips on programs"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-05-19
Anyone have some good tips for these programms? (for Dapper Drake)

1. C++ compiler/editor
2. Java compiler/editer
3. Direct Connect
4. Bittorrent client

Well that was all I can think of now :) (I am going to try to have Linux only on my laptop, soon.)

---

### Post by Sef on 2006-05-19
> 1. C++ compiler/editor

to download that, you need build-essential.

sudo apt-get update

sudo apt-get install build-essential


> 4. Bittorrent client

Applications > Add/Remove

---

### Post by S{yndrom}e on 2006-05-19
Anjuta is a good c++ compilier/editor. I still miss Dev++ though. Or another way to compile is doing the sudo apt-get install buid-essential and doing 

gcc *thingyouwantcompilied.c* -o *towhatyouwant*

---

### Post by Tortanick on 2006-05-19
If you're compiling source tarballs with GNU make. I would serously recomend getting checkinstall from the universe. just replace 

```
sudo make install
``` 
with 
```
sudo checkinstall
```

And you'll be able to unistall your new program from synaptic

---

### Post by EdThaSlayer on 2006-05-19
Download automatix

you can get azarious[excuse my spelling] and bittorent and not to mention a C++ IDE

---

### Post by mostwanted on 2006-05-19
[QUOTE=S{yndrom}e]Anjuta is a good c++ compilier/editor. I still miss Dev++ though. Or another way to compile is doing the sudo apt-get install buid-essential and doing 

gcc *thingyouwantcompilied.c* -o *towhatyouwant*[/QUOTE]

Anjuta isn't a compiler, neither is DevC++; they're both IDEs that use GCC under the hood. GCC is installed when you install the build-essential package.

---

### Post by it.henrik on 2006-05-19
for bittorrent I recommend Azureus. Its THE bittorrent app out there.

---

### Post by IsKall on 2006-05-19
Wow, many replies, I will try all your recommendations ;)


Thanks!

---

### Post by joshrobinson on 2006-05-19
yeah azureus kicks butt!

[http://azureus.sourceforge.net/]("http://azureus.sourceforge.net/")

---

