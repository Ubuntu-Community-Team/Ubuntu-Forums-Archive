---
title: "Permissions on a mac drive"
date: 2011-02-21
forum: Apple Hardware Users
---

### Post by Djalmahal on 2011-02-21
Hi everybody,

so I'm going to visit my Mac friends again tonight, I myslef run Ubuntu, and before I numerous times into problems with permissions when trying to WRITE on mac-peoples hard drives. I tried sudo nautilus but that didn't help. What do I need to do to have proper permissions to write on those external hard drives.
I'm tired of snobby looks from my Mac friends :-/

Thanks

---

### Post by Hatsune Miku on 2011-02-23
> **Djalmahal said:**
> Hi everybody,

so I'm going to visit my Mac friends again tonight, I myslef run Ubuntu, and before I numerous times into problems with permissions when trying to WRITE on mac-peoples hard drives. I tried sudo nautilus but that didn't help. What do I need to do to have proper permissions to write on those external hard drives.
I'm tired of snobby looks from my Mac friends :-/

Thanks

Its not worth it in the end lol, you need to change your group and User Ids to match Mac OS X. Also HFS+(Journaled) the default FS format cannot be wrote to on Linux without causing HUGE permission errors on both ends. So yea, dnt do it xD!

---

### Post by Djalmahal on 2011-02-28
Alright thanks for the answer, sad though.

---

