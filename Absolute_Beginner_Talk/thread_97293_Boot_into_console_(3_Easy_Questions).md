---
title: "Boot into console (3 Easy Questions)"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by willhurt on 2005-11-30
Hi,
Ive been trying to sort out my screen resolution but have messed up my xorg.conf so i cant boot into ubuntu proper, only the console[forgive my terminolgy ive only had linux a few days!].

I have a backup which i named ORIGINIAL xorg.conf sitting on the Desktop which i can navigate to, and which i need to rename and move to /etc/x11

Could someone please what i have to type into the console, ive tried to navigate back to the filesystem so i can then get to etc but i cant go back any further than my Home folder, i think i have to be logged in as root but i didnt set a password for this and can only log in as a "normal" user.

So to simpify could you please tell me.
1. how to log in as a super-user without a passoword ( or navigate to the root folders)
2. how to rename a file ( cant figure the rename command out)
3. how to move a file ( cant figure mv out)

Thankyou everso much
I wont play with things i dont understand in the future

Will

---

### Post by polpak on 2005-11-30
[QUOTE=willhurt]
So to simpify could you please tell me.
1. how to log in as a super-user without a passoword ( or navigate to the root folders)
[/QUOTE]

Log into the console as your own user.

[QUOTE=willhurt]
2. how to rename a file ( cant figure the rename command out)
[/QUOTE]

You use the mv command to rename or relocate(move) files.

[QUOTE=willhurt]
3. how to move a file ( cant figure mv out)
[/QUOTE]

mv source_file destination_file

The problem you're running into is that there's a space in the file name. If this happens you should wrap the file name with quotes or ticks like "source_file" or 'source_file'

If you need super user priviliges to overwrite the destination you must prefix the command with sudo and it will prompt you for your password (the one you log in with)

For example :
```

sudo mv '/home/willhurt/Desktop/ORIGINIAL xorg.conf' /etc/X11/xorg.conf

```

Will most likely do what you want (assuming willhurt is your username).

---

### Post by willhurt on 2005-12-01
Thanks Polpak, that worked just fine

---

