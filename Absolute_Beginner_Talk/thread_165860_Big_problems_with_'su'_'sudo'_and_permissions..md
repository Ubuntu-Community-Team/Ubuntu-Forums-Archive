---
title: "Big problems with 'su' 'sudo' and permissions."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by xc_xtc on 2006-04-25
Hi there; id like to set grub to boot XP by default but i cant edit the file.

  Somehow i dont have permissions and just get errors with su and sudo....

  can anyone help please? I know the root pw is mine but it rejects it anyways. ](*,)

---

### Post by mostwanted on 2006-04-25
Please provide what error messages you get, we're not all psychic :)

---

### Post by _simon_ on 2006-04-25
Can you confirm that you have tried the following:

```

sudo gedit /boot/grub/menu.lst

```

The password it asks for is the one you login with normally.

---

### Post by xc_xtc on 2006-04-25
no i hadnt but when i tried i got:

 sudo: unable to lookup  via gethostbyname()

---

### Post by prezbedard on 2006-04-25
sounds like a problem I had.

You may need to edit your hostname file.

You will need to boot into rescue mode to do this.

---

### Post by xc_xtc on 2006-04-25
ok i booted in rescue mode; entered the root pw and now....

 root@:"#


  dir shows dbootstrap_settings


  Ok well i dir ..

 and up to boot/grub

  Gedit menu.lst gives:

(gedit:6283): Gtk-WARNING **: cannot open display:

---

### Post by pbaehr on 2006-04-25
Use:
```
nano menu.lst
```

---

### Post by xc_xtc on 2006-04-25
Thanks alot, that worked perfectly.

---

### Post by pbaehr on 2006-04-25
Glad that worked, but you should still be concerned about the fact that you can't use sudo as it will cause you nothing but grief down the road. I don't know enough about it to help you fix it, but I'd suggest that you figure that out next. It is very important to be able to run things with sudo when you need to.

---

### Post by prezbedard on 2006-04-25
When it happened to me it was because the hostname file got messed up.

Make sure the hostname file has the name of your computer listed.

type hostname and that will tell you what your computer name is.

---

