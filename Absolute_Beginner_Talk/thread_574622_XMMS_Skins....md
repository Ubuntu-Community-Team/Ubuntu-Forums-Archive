---
title: "XMMS Skins..."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Codix121 on 2007-10-13
I installed XMMS fine,
but im having some issues installing Themes.

I have 2 WSZ files..

and when i tried going to 

/home/*your username*/.xmms/skins/

(yes, i changed my username to what it should be, codix)

It said, No such path.

and then i searched and found

/usr/share/xmms/skins

but when i try putting the skins in their it says,
YOU DO NOT HAVE PERMISSION TO WRITE IN THIS FILE.

or something like that,
can anyone help.
I'd appreciate it.
thanks =]]

---

### Post by CowzRule on 2007-10-13
Place your skin files on your desktop. Now hit "ALT-F2" and type "gksudo nautilus" (w/o quotes), enter password when prompted. Browse to and open the /usr/share/xmms/skins folder. Now just drag and drop your skin files into the folder.

---

### Post by bodhi.zazen on 2007-10-13
/usr/share/xmms/skins is a system file. Put skins in there for all users to share.

Use /home/*your username*/.xmms/skins/ for personal skins.

Best to use /home/*your username*/.xmms/skins/ ;)

In a terminal :

```
mkdir -P /home/*your username*/.xmms/skins/
```

the -P flag will make parent directories if needed. Now put your skins in ~/.xmms/skins

If you want to use /usr/share/xmms/skins you need root access.

either :```
sudo cp <skin> /usr/share/xmms/skins
```

Or :```
gksu nautilus /usr/share/xmms/skins
``` and drag and drop ...

---

