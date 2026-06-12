---
title: "GUI for Samba"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2005-10-07
I have already installed Samba on my Ubuntu system.  Wondering if and where the GUI was to create user and file premissions.  Any help would be appreciated.

---

### Post by Ampersand on 2005-10-07
Open nautilus, and right click on the folder you want to share. By going to the 'share folder' option, you can set the options for samba.

---

### Post by KingBahamut on 2005-10-07
Uh...yeah...what he said.....and stuff.....

---

### Post by patrick295767 on 2005-10-07
[QUOTE=Ampersand]Open nautilus, and right click on the folder you want to share. By going to the 'share folder' option, you can set the options for samba.[/QUOTE]

Would you know eventually if it works too with rox-filer ??

thx

---

### Post by snowjunkie on 2005-10-07
Is there any GUI for configuring other SAMBA features - like PDC functionality?

---

### Post by KingBahamut on 2005-10-07
snowjunkie, youll have to edit the confs for that. 

/etc/samba

smb.conf more specifically

---

### Post by snowjunkie on 2005-10-07
[QUOTE=KingBahamut]snowjunkie, youll have to edit the confs for that. 

/etc/samba

smb.conf more specifically[/QUOTE]

Yeah I know.  I was trying to avoid that!  ;-)

---

### Post by Ampersand on 2005-10-07
You could install webmin and its samba plugin, although it tends to have a few problems with sudo so you'd have to set up the root password.

---

### Post by John.Michael.Kane on 2005-10-07
[http://www.samba.org/samba/GUI/](http://www.samba.org/samba/GUI/)
[http://linuxdesktop.kn.vutbr.cz/old/index.php?link=107](http://linuxdesktop.kn.vutbr.cz/old/index.php?link=107)

Hope this helps

---

