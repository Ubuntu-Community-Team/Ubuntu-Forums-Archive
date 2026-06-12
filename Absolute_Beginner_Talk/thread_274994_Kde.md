---
title: "Kde"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-10
Hello!

I installed (or at least, I think I did) the KDE desktop yesterday.
I went through all of the installation for it using: 

```


sudo aptitude update
sudo aptitude install kubuntu-desktop


```

after it had finished installing, and during the "precompiling..." part of the program where it asks you questions on what you would like to do with the desktop, I clicked cancel (as I didn't know what it meant by one of its questions, and I wanted to find out about it before continuing), and it exited the "precompiling" setup. Now I don't know what to do, because when I restart the computer, and go to Ubuntu, it doesn't ask which desktop to use like it's supposed to. Is there anyway that I could "reenter" the setup for it (a command maybe)?

Thank you!

---

### Post by taurus on 2006-10-10
You can remove it and install it again.  And when you are at the login screen, look at the bottom left corner for the Options.  In there, pick whichever window manager you want to use.

---

### Post by blendmaster on 2006-10-10
Okay. So would:

```


sudo purge kubuntu-desktop


```

remove it? I've never removed anything before, so I'm not entirely sure on this.

---

### Post by taurus on 2006-10-10
```

sudo aptitude remove kubuntu-desktop
sudo aptitude install kubuntu-desktop

```
probably would do.

---

### Post by blendmaster on 2006-10-10
Okay, thanks!

I'll try this and see the results!

---

### Post by blendmaster on 2006-10-10
I used:

```


sudo aptitude remove kubuntu-desktop


```

and it told me that nothing was removed. Anyway to check to make sure the system installed it, but just isn't recognizing it? I know I downloaded it, because it took about 15 minutes. And I'm pretty sure it didn't automatically uninstall it, as the terminal said nothing about that. Plus, I'm pretty sure (though not 100%) that there's a lot of free space gone on my system now. Any file directories on where it should have downloaded?

Thanks!

---

### Post by taurus on 2006-10-10
And if everything goes okay, you can pick either KDE or Gnome from the Options at the log in screen, bottom left corner.

Good luck.

---

### Post by taurus on 2006-10-10
> **blendmaster said:**
> I used:

```


sudo aptitude remove kubuntu-desktop


```

and it told me that nothing was removed. Anyway to check to make sure the system installed it, but just isn't recognizing it? I know I downloaded it, because it took about 15 minutes. And I'm pretty sure it didn't automatically uninstall it, as the terminal said nothing about that. Plus, I'm pretty sure (though not 100%) that there's a lot of free space gone on my system now. Any file directories on where it should have downloaded?

Thanks!

Maybe you have downloaded it but haven't actually installed it on your system when you click "Cancel".  So, try install it again and if the files already on your machine, it won't download them again...

```

sudo aptitude install kubuntu-desktop

```

---

### Post by blendmaster on 2006-10-10
Okay, sorry I didn't simply try that!

It was downloaded, but needed to be installed.

Thank you Taurus for all of your help!

---

### Post by taurus on 2006-10-10
It will download whatever left that needed to be downloaded to install KDE.  All the download files are in /var/cache/apt/archives in case you want to look at them...

Good luck.

---

### Post by blendmaster on 2006-10-10
Wow!

Running it right now, and I have to say that both KDE and GNOME are beautiful desktops!

---

### Post by taurus on 2006-10-10
I see that everything is working fine for you now, eh!  

Good job.  =D>

---

### Post by SkyNet2029 on 2006-10-10
the simplest way would be to do this:

```
$sudo dpkg-reconfigure kdm
```

which takes you back to that part you skipped..'Please choose your default display manager'.. you would need to use the options at the login menu (GUI) to switch between Gnome/KDE GUI's at login.

---

