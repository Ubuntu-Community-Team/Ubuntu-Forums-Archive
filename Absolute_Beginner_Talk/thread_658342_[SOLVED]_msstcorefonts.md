---
title: "[SOLVED] msstcorefonts"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by nagla on 2008-01-04
i installed ubuntu restricted extras and not every time i try and install something it says mssttcore fonts has an error or something like that

i also got this error

E: msttcorefonts: subprocess pre-removal script returned error exit status 1

i got that when i tried to remove it from synaptic

can someone help me... i dont want to reinstall ubuntu again...:(

---

### Post by milton1 on 2008-01-04
try reinstalling msttcorefonts

---

### Post by nagla on 2008-01-04
when i type install it says i have the newest pachage...
when i type "sudo apt-get remove msttcorefonts" it says this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93091 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

All fonts downloaded and installed.
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
nitel@nitel-desktop:~$ 

 
```

---

### Post by forestpixie on 2008-01-04
if that doesn't help try

sudo apt-get install -f  
or
sudo dpkg --configure -a

---

### Post by nagla on 2008-01-04
im not sure what did it but i dont get the error everytime i try to install something
thanks to the both of you and thank for the super quick reply's
i love this forum...:)

---

