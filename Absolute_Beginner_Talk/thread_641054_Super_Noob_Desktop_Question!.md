---
title: "Super Noob Desktop Question!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by doomsdaydave11 on 2007-12-14
This will probably sound like the noobiest question ever, and you will probably think I'm retarded, but how do you remove icons from your desktop? I don't want icon's of all my hard drives, and DVD drives on my desktop.:confused:
Thanks.

---

### Post by Dark_Stang on 2007-12-14
You delete them... Right click > Move to trash or just select it and delete it.

---

### Post by jflaker on 2007-12-14
> **Dark_Stang said:**
> You delete them... Right click > Move to trash or just select it and delete it.

Careful in doing so.....make sure the icons are NOT programs or file you want.  Unlike Windows which has shortcuts all over the place (you can do the same with links in Linux), your icons are not always a link/shortcut.

use caution.

---

### Post by doomsdaydave11 on 2007-12-14
nope, I would of thought of that from using Windows.
You can't move Hard Drive Icons to the trash

---

### Post by thelatinist on 2007-12-14
> **doomsdaydave11 said:**
> This will probably sound like the noobiest question ever, and you will probably think I'm retarded, but how do you remove icons from your desktop? I don't want icon's of all my hard drives, and DVD drives on my desktop.:confused:
Thanks.

Not at all.  That actually is a little hard to find. This link should help: [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by siciliancasanova on 2007-12-14
> **jflaker said:**
> Careful in doing so.....make sure the icons are NOT programs or file you want.  Unlike Windows which has shortcuts all over the place (you can do the same with links in Linux), your icons are not always a link/shortcut.

use caution.

I agree, if these are partition icons, I'm assuming it's going to unmount anything you move to the trash.

---

### Post by thelatinist on 2007-12-14
> **siciliancasanova said:**
> I agree, if these are partition icons, I'm assuming it's going to unmount anything you move to the trash.

Yeah, moving such things to the trash is not the way to go.  See my link, above.

---

### Post by doomsdaydave11 on 2007-12-14
Sweet, the config-editor worked. Thanks man, I can go to bed now :)

---

### Post by Dark_Stang on 2007-12-14
I thought he just had them as links. If you don't want them mounted to your desktop you'll have to change where they mount in /etc/fstab

---

### Post by thelatinist on 2007-12-14
> **Dark_Stang said:**
> I thought he just had them as links. If you don't want them mounted to your desktop you'll have to change where they mount in /etc/fstab

He had them mounted fine, but Ubuntu puts icons for all mounted partitions on the desktop by default.  To remove them you have to change a key in gconf-editor.

---

