---
title: "Login screen problem in Edgy"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by xor.be on 2006-10-30
Hi all,

I installed a nice login theme for my gnome desktop under ubuntu edgy.
After that i downloaded the KDE desktop environment, and to my surprise the login screen is this awful blue Kubuntu thing.

I wanted to change this back, so in gnome i went to the login screen program in Administrator, but this won't open up anymore :s

It asks for my password,put it in,and then it does nothing.
I found no such program in Kde, so i'm kinda stuck with this screen.
Are there maybe commands i can use to put my theme back,or at least unlock the login screen program.

Could somebody please point me in the right direction ? :(

---

### Post by jd65pl on 2006-10-30
Try doing this command in terminal, do you note any errors?

```
gksu gdmsetup
```

---

### Post by xor.be on 2006-10-30
Hi JD65PL,

Thanks for your help.
When i try that i get the following.

> 
xor@xor-dell:~$ gksu gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.


Socket in this context ? :-S

---

### Post by xor.be on 2006-10-30
It seems i was able to isolate the faulty code using "sudo ltrace gdmsetup"

and it gives me 

> glade_init(0x8066e98, 0, 0, 0, 0)                = 0
socket(1, 1, 0)                                  = 4
connect(4, 0xbf8b4f3a, 110, 0xb773e7a8, 0)       = -1
g_strdup_vprintf(0x8068ac0, 0xbf8b4ee4, 0, 5, 0xbf8b4fb8) = 0x809b9e0
g_printf(0x80692ed, 0x809b9e0, 0, 5, 0xbf8b4fb8  Failed to connect to socket, sleep 1 second and retry
) = 56
g_free(0x809b9e0, 0x809b9e0, 0, 5, 0xbf8b4fb8)   = 0
sleep(1)                                         = 0
__errno_location()                               = 0xb74efa60
close(4)                                         = 0
g_strdup_vprintf(0x8068a90, 0xbf8b4e04, 0xb74f0020, 1, 0) = 0x8095b28
g_printf(0x80692ed, 0x8095b28, 0xb74f0020, 1, 0  Trying failed command again.  Try 2 of 5.


---

### Post by BigWillyT on 2006-10-30
I would try reinstalling the GDM/GNOME desktop.  It sounds to me like after installing the KDE desktop, somehow, your GNOME desktop got removed/misplaced/corrupted.  Check out this thread here, it may give answers to your question. [http://www.ubuntuforums.org/showthread.php?t=95275&highlight=changing+login+screen+in+KDE](http://www.ubuntuforums.org/showthread.php?t=95275&highlight=changing+login+screen+in+KDE)

---

### Post by xor.be on 2006-10-30
i'm glad to say i didn't have to reinstall anything

i tried to change it using
> sudo update-alternatives --config usplash-artwork.so

I manually deleted the kubuntu usplash file in usr/lib/usplash. This didn't do it either.

I got some errors doing
> sudo dpkg-reconfigure gdm 
But it seems to have done the trick :)

I have a few additional noob questions.
Is there no way to have a splash screen in gnome (like the one in kde,between the login and desktop).
Also, different wallpapers for each different desktop don't seem to be possible either ? 

Thx you guys :)

---

