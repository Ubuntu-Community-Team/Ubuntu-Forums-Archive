---
title: "[SOLVED] Updating DeVeDe"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-23
I wanted to upgrade to a newer build as it has fixed the[COLOR="Red"] 'low cpu priority' [/COLOR]problem with the older version, so now it should take less time :)

[IMG]http://img452.imageshack.us/img452/521/devedepz9.jpg[/IMG]

[IMG]http://img177.imageshack.us/img177/6572/samplega2.jpg[/IMG]

---

### Post by tzulberti on 2007-08-23
To install it you should use:
./install.sh 
or
sh install.sh

---

### Post by chrome307 on 2007-08-24
Unfortunately this did not work for me :?

```


user@user-ubuntu:~/devede-3.01$ ./install.sh
rm: cannot remove `/usr/share/locale/cs/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/de_DE/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/es/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/fr/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/gl/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/it/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/nb_NO/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/pt_BR/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/pt_PT/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/share/locale/sk/LC_MESSAGES/devede.mo': Permission denied
rm: cannot remove `/usr/local/bin/devede': Permission denied
rm: cannot remove `/usr/local/lib/devede/devede_other.py': Permission denied
rm: cannot remove `/usr/local/lib/devede/devede_gtk_helper.py': Permission denied
rm: cannot remove `/usr/local/lib/devede/devede_convert.py': Permission denied
rm: cannot remove `/usr/local/share/devede/estira.png': Permission denied
rm: cannot remove `/usr/local/share/devede/silence.wav': Permission denied
rm: cannot remove `/usr/local/share/devede/ntsc_wide_active.png': Permission denied
rm: cannot remove `/usr/local/share/devede/pal_active.png': Permission denied
rm: cannot remove `/usr/local/share/devede/devedesans.ttf': Permission denied
rm: cannot remove `/usr/local/share/devede/barras.png': Permission denied
rm: cannot remove `/usr/local/share/devede/devede.glade': Permission denied
rm: cannot remove `/usr/local/share/devede/ntsc_active.png': Permission denied
rm: cannot remove `/usr/local/share/devede/background.png': Permission denied
rm: cannot remove `/usr/local/share/devede/pal_wide_active.png': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie6.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/choose.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/psf.html': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/main2.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie3.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/create.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/menu_opts.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie1.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/devede.html': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/title_prop.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie2.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/faq.html': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/gpl.html': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/menu_bad.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie5.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/menu.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/main.jpg': Permission denied
rm: cannot remove `/usr/local/share/doc/devede/html/movie4.jpg': Permission denied
rm: cannot remove `/usr/local/share/pixmaps/devede.png': Permission denied
rm: cannot remove `/usr/local/share/applications/devede.desktop': Permission denied
install: cannot remove `/usr/share/locale/cs/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/de_DE/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/es/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/fr/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/gl/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/it/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/nb_NO/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/pt_BR/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/pt_PT/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/share/locale/sk/LC_MESSAGES/devede.mo': Permission denied
install: cannot remove `/usr/local/bin/devede': Permission denied
install: cannot remove `/usr/local/lib/devede/devede_convert.py': Permission denied
install: cannot remove `/usr/local/lib/devede/devede_gtk_helper.py': Permission denied
install: cannot remove `/usr/local/lib/devede/devede_other.py': Permission denied
install: cannot remove `/usr/local/share/devede/devede.glade': Permission denied
install: cannot remove `/usr/local/share/devede/devedesans.ttf': Permission denied
install: cannot remove `/usr/local/share/devede/background.png': Permission denied
install: cannot remove `/usr/local/share/devede/barras.png': Permission denied
install: cannot remove `/usr/local/share/devede/estira.png': Permission denied
install: cannot remove `/usr/local/share/devede/ntsc_active.png': Permission denied
install: cannot remove `/usr/local/share/devede/ntsc_wide_active.png': Permission denied
install: cannot remove `/usr/local/share/devede/pal_active.png': Permission denied
install: cannot remove `/usr/local/share/devede/pal_wide_active.png': Permission denied
install: cannot remove `/usr/local/share/devede/silence.wav': Permission denied
install: cannot remove `/usr/local/share/pixmaps/devede.png': Permission denied
install: cannot remove `/usr/local/share/applications/devede.desktop': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/choose.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/create.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/devede.html': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/faq.html': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/gpl.html': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/main2.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/main.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/menu_bad.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/menu.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/menu_opts.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie1.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie2.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie3.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie4.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie5.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/movie6.jpg': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/psf.html': Permission denied
install: cannot remove `/usr/local/share/doc/devede/html/title_prop.jpg': Permission denied


```

---

### Post by WakkiTabakki on 2007-08-24
You need to run it with root permissions...
```
sudo ./install.sh
```

/N

---

### Post by chrome307 on 2007-08-24
Thank you all for helping me install this package.

Just in case anyone needs to do the same

Use Synaptic to download the older version as it contains additional packages ie Mencoder.

Then go to the DeVeDe Homepage to download the latest build and extract

Then carry out the steps outlined above :)

[img]http://img368.imageshack.us/img368/9893/devedepd8.jpg[/img]

---

