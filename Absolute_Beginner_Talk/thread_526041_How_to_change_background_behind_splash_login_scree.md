---
title: "How to change background behind splash login screen"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by crsd36 on 2007-08-15
I've seen a few threads about this but none have helped me, so I suppose I've missed something.  Can someone post a basic guide to changing the background which is behind the splash screen after login?  Thanks!

---

### Post by cawill on 2007-08-15
In terminal type:
```
sudo apt-get install gnome-splashscreen-manager
```

then either run gnome-splashsceen-manager using alt+f2 or open it from System > Preferences > Splash Screen.

---

### Post by wolfen69 on 2007-08-15
you should spend more time learning about linux instead of BS. just a heads up.

---

### Post by p_quarles on 2007-08-15
> **crsd36 said:**
> I've seen a few threads about this but none have helped me, so I suppose I've missed something.  Can someone post a basic guide to changing the background which is behind the splash screen after login?  Thanks!
You can change the background color very easily, by going to to System >> Administration >> Login Window. Then, click on the "local" tab, and you'll see an option to change the background. 

@wolfen69: Care for some coffee? It's fresh brewed.

---

### Post by jordanmthomas on 2007-08-15
You can change the color of the background in gdmsetup 
```
system --> administration --> login window
```
If you want to put a picture back there I believe it is more complicated, and you may have to edit the way you start gnome.  (though it is certainly possible)

*edit* boo, beaten twice.

---

### Post by crsd36 on 2007-08-15
> **cawill said:**
> In terminal type:
```
sudo apt-get install gnome-splashscreen-manager
```

then either run gnome-splashsceen-manager using alt+f2 or open it from System > Preferences > Splash Screen.

I knew how to change the screen itself, I'm actually wanting to change the brown/orange defalut that is behind it if thats possible?



> **wolfen69 said:**
> you should spend more time learning about linux instead of BS. just a heads up.

Sorry if I offended you, but I don't know how you expect one to learn without asking questions?


EDIT:  Ahh, many thanks all, it was a stupid mistake of mine, I was trying to change it through System > Background instead of through the login window.  Again, many thanks!

---

### Post by SeanBlader on 2007-08-15
Well I wanna know where Jordan got his list of login themes.

---

### Post by jordanmthomas on 2007-08-15
I got most of them in a package for Archlinux called gdm-themes.  The ones you see (arch underlight) I got from [gnome-look.org]("http://gnome-look.org/content/show.php/Arch+Underlight+(3+Colours)?content=62007")

I am not sure if I'm allowed to redistribute the rest, so I won't.

---

### Post by cyneuron on 2007-12-22
hey were u able to change the color of screen which comes after login ? i also have same problem....please tell me if you have got the answer...

---

### Post by gll on 2008-04-11
It doesn't seems to be possible to change the background 'AFTER' the logon screen...

I was trying to change the sudo theme, but I've failed on this too.
Is it embedded inside the splashScreen Theme? Where is defined this background?

---

### Post by spiderbatdad on 2008-04-11
> **gll said:**
> It doesn't seems to be possible to change the background 'AFTER' the logon screen...

I was trying to change the sudo theme, but I've failed on this too.
Is it embedded inside the splashScreen Theme? Where is defined this background?

[http://ubuntuforums.org/showthread.php?t=745869&highlight=change+background+after+login+screen](http://ubuntuforums.org/showthread.php?t=745869&highlight=change+background+after+login+screen)

---

### Post by gll on 2008-04-11
aha... Cool, thanks..

---

