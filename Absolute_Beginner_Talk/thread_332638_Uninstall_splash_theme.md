---
title: "Uninstall splash theme"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-06
I installed a splash theme and since them my boot time on my laptop has more than doubled. How would I go about removing the theme?

---

### Post by teaker1s on 2007-01-06
[COLOR="Red"]gksudo synaptic[/COLOR]
search 
[COLOR="Red"]usplash[/COLOR] 
with description and name

you can then change between them

---

### Post by rbhigday on 2007-01-06
Thanks but I did not use synaptic to install it. I used the following

```
sudo cp usplash-theme-gray.so /usr/lib/usplash/
```

then

```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-gray.so 10
```

and finally

```
sudo update-alternatives --config usplash-artwork.so
```

Then I updated the booting process

```
sudo update-initramfs -u
```

The theme is [COLOR="Navy"][ Usplash Theme - Fingerprint  ]("http://www.gnome-look.org/content/show.php?content=50468")[/COLOR]

---

### Post by rbhigday on 2007-01-08
still looking for way to remove this without reinstalling, or suffer thru window like bootup and down times lol

---

