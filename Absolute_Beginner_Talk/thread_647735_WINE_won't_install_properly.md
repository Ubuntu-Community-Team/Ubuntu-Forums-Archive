---
title: "WINE won't install properly"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by medicatedlain on 2007-12-22
I tried a few things here, I just managed to fix up everything on linux from a few problems I was having before due to korean/japanese installations, but I think maybe wine may have been the cause after all.  I tried installing wine a week or so ago, and got an error message, and it didn't install correctly.  Well after just fixing up a problem today:

```
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

with:
```
sudo dpkg --configure -a
sudo apt-get update
```

I tried reinstalling wine from package manager, and got:
```
E: msttcorefonts: subprocess post-installation script returned error exit status 1
```

So I found something suggesting:
```
sudo apt-get install wine

```

But still I got:
```
mv: accessing `/usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf': Too many levels of symbolic links
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by dcstar on 2007-12-22
> **medicatedlain said:**
> I tried a few things here, I just managed to fix up everything on linux from a few problems I was having before due to korean/japanese installations, but I think maybe wine may have been the cause after all.  I tried installing wine a week or so ago, and got an error message, and it didn't install correctly.  Well after just fixing up a problem today:

```
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
........
[/CODE]

Any ideas?

Remove the msttcorefonts package and try again.

---

### Post by medicatedlain on 2007-12-23
yep, that worked.

---

