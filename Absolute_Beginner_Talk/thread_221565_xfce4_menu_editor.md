---
title: "xfce4 menu editor"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2006-07-23
to fix if the applications and or right click menu no longer work

cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml

the ~/.config/xfce4/desktop/menu.xml is a hidden folder in your /home/username folder where username is your user name just to be claer. to edit the menu list i had to do it by hand becuse the menu editor would not work for me and looking around the forms i was unable to find any one that said if worked to them either. to edit it by hand open 
/home/yourUserName/.config/xfce4/desktop right click on the file called menu.xml and open with a text editor like mousepad or gedit just to name a few

---

### Post by lance bermudez on 2006-07-23
found out that the xfce4 menu editor will work for you if you update the xfdeskop4
[http://ubuntu.mirrors.tds.net/ubuntu/pool/main/x/xfdesktop4/xfdesktop4_4.3.90.1svn+r21874-0ubuntu2_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/main/x/xfdesktop4/xfdesktop4_4.3.90.1svn+r21874-0ubuntu2_i386.deb)

---

