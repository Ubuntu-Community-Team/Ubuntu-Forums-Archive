---
title: "How to change volume applet stock icons?"
date: 2005-04-10
forum: Art &amp; Design
---

### Post by wolovids on 2005-04-10
This has been annoying me with versions of Gnome later than 2.8.x.  I am wondering if anyone can help me out with this question.  

With the Gnome previous versions of Gnome, I was able to change my volume applet stock icons with a change of theme (if the theme specified new icons).  Now, the icons NEVER seem to change.  I am using the same versions of the Crystal and Nuolva themes for Gnome that I did with Gnome 2.8 and now they now longer change these icons.  

Anyone else noticing this?  If so, how can I fix this?  I have no problem editing iconrc or gtkrc files manually since I am sort of a perfectionist and I have gone far too long with this not working! 

Thanks for your help.

---

### Post by bvc on 2005-04-10
yes, I've noticed the same. I'm not sure why except that I know panel applets have been under a lot of devel recently, I guess in an attempt to make them more appealing to the eye?

Your Icon Theme has to have a stock icon dir, usually like this
```
ls .icons/Human2b/scalable
apps  devices  emblems  filesystems  gtk  stock
```

with these volume icon names```
ls .icons/Human2b/scalable/stock
stock_volume-0.svg    stock_volume-med.svg  stock_volume-mute.svg
stock_volume-max.svg  stock_volume-min.svg
```

and don't forget to make sure the index.theme has the stock dir in it
```
Directories=scalable/apps,scalable/filesystems,scalable/devices,scalable/gtk,scalable/emblems,scalable/stock

[scalable/stock]
MinSize=1
Size=128
MaxSize=128
Context=Emblems
Type=scalable

```

then they'll change
[http://www.kernow-webhosting.com/~bvc/theme/screenshots/Earth.jpg](http://www.kernow-webhosting.com/~bvc/theme/screenshots/Earth.jpg)

---

### Post by wolovids on 2005-04-11
Thanks!  That worked perfectly.

---

