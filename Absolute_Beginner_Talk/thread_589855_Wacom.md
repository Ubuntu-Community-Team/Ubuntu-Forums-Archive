---
title: "Wacom"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-10-24
Here goes:
I have look at my xconf.  and saw at the very bottom that if you have a Wacom tablet
to remove # <-------
I have done so but can not save the change.
Permission denied or what ever.
It said this
 #Uncomment if you have a wacom tablet
   #      InputDevice     "Stylus"      "SendCoreEvents"
   #      InputDevice     "cursor"      "SendCoreEvents"
   #      InputDevice     "eraser"      "SendCoreEvents"

These are the 3 comments I have to take care off.... but when I do and go to save change
it will tell me that I am not the Admin
Help please.

---

### Post by danm-koder on 2007-10-24
To get the Admin permissions, browse to the file, and the right-click it and "Edit as root" then you can save the changes...

On the other hand if you are using a terminal you should type:

```
$ sudo gedit /pathToFile/xconf
```

---

### Post by burt_57 on 2007-10-24
> **danm-koder said:**
> To get the Admin permissions, browse to the file, and the right-click it and "Edit as root" then you can save the changes...

On the other hand if you are using a terminal you should type:

```
$ sudo gedit /pathToFile/xconf
```

Thank for the help, but it just will not work.
All is gray out and right click will not work either.
When I do it in terminal it open an empty page !
Just keep telling me that I am not the owner......... can not edit the file.
And I can see that it said root at the top but all tabs are gray out.Use the following command to edit your xorg.conf file:

This way work for me

sudo nano /etc/X11/xorg.conf

replace 'nano' with other text editor, if you prefer.

---

