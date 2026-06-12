---
title: "EasyUbuntu Problem"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-22
I am having trouble installing easyubuntu.

i have downloaded it and selecteted the packages that i want to install, it downloads them.

but them i get a warning box with this message:

> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


then i get an error box with this message:

> Could not apply changes!
Fix broken packages first.


then a diolog box called somthing like "easyubuntu.in" i forget sorry, saying:

> /bin/sh: update-flashplugin: command not found
fc-cache: "/usr/share/fonts": caching, 0 fonts, 2 dirs
fc-cache: "/usr/share/fonts/truetype": caching, 0 fonts, 21 dirs
fc-cache: "/usr/share/fonts/truetype/arphic": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/baekmuk": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/freefont": caching, 12 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/kochi": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/openoffice": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/thai": caching, 23 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-arabeyes": caching, 39 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bengali-fonts": caching, 7 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-bitstream-vera": caching, 10 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-dejavu": caching, 21 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-devanagari-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gentium": caching, 4 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-gujarati-fonts": caching, 5 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-kannada-fonts": caching, 8 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-lao": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-malayalam-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-mgopen": caching, 16 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-oriya-fonts": caching, 1 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-punjabi-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-tamil-fonts": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/fonts/truetype/ttf-telugu-fonts": caching, 2 fonts, 0 dirs
fc-cache: "/usr/share/fonts/type1": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/fonts/type1/gsfonts": caching, 35 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts": caching, 0 fonts, 5 dirs
fc-cache: "/usr/share/X11/fonts/100dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/75dpi": caching, 397 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/Type1": caching, 9 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/encodings": caching, 0 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/encodings/large": caching, 0 fonts, 0 dirs
fc-cache: "/usr/share/X11/fonts/misc": caching, 55 fonts, 1 dirs
fc-cache: "/usr/share/X11/fonts/misc/misc": caching, 0 fonts, 0 dirs
fc-cache: "/usr/local/share/fonts": caching, 0 fonts, 0 dirs
fc-cache: "/root/.fonts": skipping, no such directory
fc-cache: succeeded


could anyone help me with this?

---

### Post by Kateikyoushi on 2006-10-22
Copy these commands to the terminal.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

### Post by Jamesbowden on 2006-10-22
hmmm, i still get exactly the same problem.

any other advice?

---

### Post by Kateikyoushi on 2006-10-22
That should have solved the gpg key error.

---

### Post by Nytram on 2006-10-22
not a fix but a workaround

i had the same problem with easyubuntu and couldn't find a working solution to it

instead i used "automatix" which has similiar functionality to easyubuntu, and worked for me with no problems

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by redDEADresolve on 2006-10-22
> **Nytram said:**
> not a fix but a workaround

i had the same problem with easyubuntu and couldn't find a working solution to it

instead i used "automatix" which has similiar functionality to easyubuntu, and worked for me with no problems

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

Nytram is right EasyUbunyu hasn't worked right in weeks. Use automatrix, offers more stuff, more fonts and works.

---

### Post by Jamesbowden on 2006-10-23
Thanks guys ill use automatix.

---

