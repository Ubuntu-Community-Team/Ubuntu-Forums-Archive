---
title: "ThinkLinux Usplash Theme Request"
date: 2006-12-15
forum: Art &amp; Design
---

### Post by Jonathan2007 on 2006-12-15
I found [this]("http://www.kde-look.org/content/show.php?content=26495") ThinkLinux bootsplash and thought it would be great to use. But it is not in Usplash form and thus I can't install it. If someone would be so kind as to convert it for me I would really appreciate it. They could upload the result to Kde-look.org or I could upload it (if they didn't want to upload it) and give them credit. I think this is a great image that would be really good as a Usplash theme. Thanks :)

---

### Post by napo on 2006-12-16
I made an usplash  theme for you. I hope it is what you want.

[[IMG]http://img521.imageshack.us/img521/6233/usplashthemethinklinuxsx1.th.jpg[/IMG]](http://img521.imageshack.us/my.php?image=usplashthemethinklinuxsx1.jpg)

You can download it here: [download](http://mitglied.lycos.de/atoth/ubuntuusers/usplash-theme-thinklinux_0.1_i386.deb)

Or do you like this more?


[[img]http://img342.imageshack.us/img342/4356/screenshotba7.th.jpg[/img]](http://img342.imageshack.us/my.php?image=screenshotba7.jpg)
[download](http://mitglied.lycos.de/atoth/ubuntuusers/usplash-theme-blue-napo_0.1_i386.deb)

Or this?
[[img]http://img155.imageshack.us/img155/6868/screenshot2cl4.th.jpg[/img]](http://img155.imageshack.us/my.php?image=screenshot2cl4.jpg)

[download](http://mitglied.lycos.de/atoth/ubuntuusers/usplash-theme-blue-knapo_0.1_i386.deb)

---

### Post by xopher on 2006-12-16
Nice work!

What is the maximum amount of colors in a usplash theme?

The (k)ubuntu themes are nice, but a bit too plastic for my eye. :)

---

### Post by napo on 2006-12-16
only 256 colors :(

---

### Post by Jonathan2007 on 2006-12-16
> **napo said:**
> I made an usplash  theme for you. I hope it is what you want.

[[IMG]http://img521.imageshack.us/img521/6233/usplashthemethinklinuxsx1.th.jpg[/IMG]](http://img521.imageshack.us/my.php?image=usplashthemethinklinuxsx1.jpg)

You can download it here: [download](http://mitglied.lycos.de/atoth/ubuntuusers/usplash-theme-thinklinux_0.1_i386.deb)
That is awesome. That is exactly what I wanted. Thanks a lot. I will try this out later today. I will upload it to Kde-look.org if you haven't already and I will give you credit for making the Usplash file (not the image of course but you still deserve some credit). :mrgreen:

---

### Post by nbayiha on 2006-12-17
can you tell us how to install it..cause it look really nice.

---

### Post by Jonathan2007 on 2006-12-17
It is just a deb file so I would assume just install that and it would replace/take over your old Usplash theme but I could be wrong. I still haven't gotten around to trying it. I hope to do so soon.

---

### Post by napo on 2006-12-18
First you install the deb file with dpkg -i xxx.deb
After that you must choose the new theme with sudo update-alternatives --config usplash-artwork.so
And then you must do sudo dpkg-reconfigure usplash to write the theme into your initrd

---

### Post by nbayiha on 2006-12-18
thanks i tried and it work fine. but when i restarted my computer i get a smth really nasty i think is because i'm using gnome instead of kde. 
but thanks for the help.

---

