---
title: "To make a hi-res screenshot with Imagemagick"
date: 2021-08-25
forum: Art &amp; Design
---

### Post by shantiq on 2021-08-25
Used Gnome-screenshot a lot but it only provides a low-res png; so reading around found there is functionality on Gimp to produce a tiff screenshot but it is clumsy as it cannot be used from command line and there is need to open the full GUI first; so reading further there is Imagemagick

```
sudo apt install imagemagick
```


Now then I want it to produce an image in tiff in the 10MB range so I have detail on it; something I can then work with
Thing is if you use it from command line with no time delay it will also shoot your terminal ....   NOT optimal; so there use the sleep program

Set on desktop what you want shot then give yourself time to get terminal out of the way; anytime you want it back enter CTRL+R in terminal and type screen or sl if you have not got anything else starting with that ...   and there a fairly supple hi-res screenshot easily obtained


```
[COLOR=#800000]sleep 5s &&  import -window root Desktop/Screenshot.tiff #screen[/COLOR]
```

---

