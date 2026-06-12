---
title: "themes in XUBUNTU"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by tim_tim on 2007-06-28
hi, i made a topic like this hours ago  and i got a few replies, but i don' think anyone was understanding what i was saying so lets try this again. First off I'm running XUBUNTU and i downloaded some themes. The thing about Xubuntu is that there is no "theme manger" unlike Ubuntu i know there has to be some way to install them, I'm just having trouble finding out how or were to install them, and if i need to extract them or not. please help. Thanks.

---

### Post by IusedTObeSOMEONEelse on 2007-06-28
Sorry I can't help, but just wanted to say that was one of the reasons I gave up on Xubuntu:(

---

### Post by tim_tim on 2007-06-28
there has got to be way,

---

### Post by scxtt on 2007-06-28
extract the downloaded theme into /usr/share/themes and it should show up in the theme browser ...

---

### Post by tim_tim on 2007-06-28
alright. i did that and i get a error that said i don't have permission to extract to /usr/share/theme. I'm the only one who uses this comp, so im not understanding why im getting that. do i have to be logged in as "root" or something??? because i don't know anything about that.

---

### Post by scxtt on 2007-06-28
use sudo, it lets you "pretend" to be root for a while (this is default for the originating install user).

cd /usr/share/themes/
sudo tar zxvf <theme_name>.tar.gz

---

### Post by ubuntu27 on 2007-06-28
```
gksu thunar
```

Thunar is the File Manager in Xfce (Xubuntu). 

With that command you will be able to open Thunar as a Root. Carefull with what you do though.

---

### Post by scxtt on 2007-06-28
that's only if an xubuntu install comes w/ gksu(do)/kdesu, etc. - or if XFCE was installed over a ubuntu/kubuntu install ... i have XFCE installed in gentoo and have no gk* anything ...

---

### Post by tim_tim on 2007-06-28
oh man!!! thanks so much!!! this forum has never failed me.

---

### Post by scxtt on 2007-06-28
the same thing goes for **/usr/share/icons** as well, if you ever want to do that :)

---

### Post by ubuntu27 on 2007-06-28
> **scxtt said:**
> that's only if an xubuntu install comes w/ gksu(do)/kdesu, etc. - or if XFCE was installed over a ubuntu/kubuntu install ... i have XFCE installed in gentoo and have no gk* anything ...

I use Xubuntu and I have gksu. I don't remember installing it ( I always pay attention to what I install), so it must have come by default install I believe.  

So you have Xfce in Gentoo and dont' have gksu.  It must be Xubuntu then.

---

### Post by mkquist on 2007-08-04
.

---

### Post by crimesaucer on 2007-08-04
> **tim_tim said:**
> alright. i did that and i get a error that said i don't have permission to extract to /usr/share/theme. I'm the only one who uses this comp, so im not understanding why im getting that. do i have to be logged in as "root" or something??? because i don't know anything about that.

for the graphical way type "alt+f2", then:

```
gksudo thunar
```


Also, the gtk-2.0 themes using the xfce4 engine are very easy to make, and edit with your own colors and widgets.


Just read the gtkrc file in /usr/share/themes/Xfce-4.2/gtk-2.0/gtkrc


...or any other Xfce-theme like "Xfce-winter".

---

### Post by ubuntu27 on 2007-08-05
> **tim_tim said:**
> alright. i did that and i get a error that said i don't have permission to extract to /usr/share/theme. I'm the only one who uses this comp, so im not understanding why im getting that. do i have to be logged in as "root" or something??? because i don't know anything about that.

Read the following link, it would explain about Sudo, Root, and Security in Ubuntu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ugm6hr on 2007-08-05
> **tim_tim said:**
> hi, i made a topic like this hours ago  and i got a few replies, but i don' think anyone was understanding what i was saying so lets try this again. First off I'm running XUBUNTU and i downloaded some themes. The thing about Xubuntu is that there is no "theme manger" unlike Ubuntu i know there has to be some way to install them, I'm just having trouble finding out how or were to install them, and if i need to extract them or not. please help. Thanks.

If you are still looking to make changes - everything is modifiable: GDM login, icons, window manager theme...

[http://ubuntuforums.org/showpost.php?p=3080736&postcount=6](http://ubuntuforums.org/showpost.php?p=3080736&postcount=6)

---

