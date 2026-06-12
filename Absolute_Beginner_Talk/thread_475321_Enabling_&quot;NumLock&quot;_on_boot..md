---
title: "Enabling &quot;NumLock&quot; on boot."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-16
Hello!

Thanks again Ubuntu Community, I know I ask a lot of questions, I'm just getting used to Iinux.

My password I use for my Ubuntu Login has numbers in it, and I usually use the numpad. It might seem like something small, but I hate clicking "Num Lock" every time I boot. Further, after I login, it turns off once more!

Especially when typing it passwords throughout the net, I type it in, press enter, and realize Num Lock was off.

Is there a way to permanently enable this or something?

Thanks Ubuntu Community!

---

### Post by jimrz on 2007-06-16
> **alecwh said:**
> Hello!

Thanks again Ubuntu Community, I know I ask a lot of questions, I'm just getting used to Iinux.

My password I use for my Ubuntu Login has numbers in it, and I usually use the numpad. It might seem like something small, but I hate clicking "Num Lock" every time I boot. Further, after I login, it turns off once more!

Especially when typing it passwords throughout the net, I type it in, press enter, and realize Num Lock was off.

Is there a way to permanently enable this or something?

Thanks Ubuntu Community!

install "numlockx" which is available in Synaptic. you will need to have the universe repo enabled

---

### Post by alecwh on 2007-06-16
Ok, I downloaded it. I just restarted X and it didn't work. :(

Do I have to do something else?

---

### Post by jimrz on 2007-06-16
> **alecwh said:**
> Ok, I downloaded it. I just restarted X and it didn't work. :(

Do I have to do something else?

i think you need to reboot, rather than just restarting X, in order to get it working the first time. after that it should be there all the time.

---

### Post by alecwh on 2007-06-16
No go after reboot. ;(

---

### Post by alecwh on 2007-06-16
bump?

---

### Post by Nikron on 2007-06-16
> **alecwh said:**
> bump?

You have to add numlockx to your .xinitrc  (I assume you want to use want to use in GDM)

```

echo "numlockx" >> .xinitrc

```

And then pressing CTRL+ATL+DEL (restart X) should be fine

---

### Post by alecwh on 2007-06-16
Nope, didn't work. I have no ide awhat's wrong.

How do I show you the contents of that?

---

### Post by Outrunner on 2007-06-16
> **alecwh said:**
> Nope, didn't work. I have no ide awhat's wrong.

How do I show you the contents of that?

```
cat .xinitrc
```

I'm guessing this is what you meant?

---

### Post by alecwh on 2007-06-16
```

numlockx

```

That's all the file has. :P

---

### Post by Nikron on 2007-06-16
Hmm, I tested numlockx out on my computer, and it turned on the numlock key.  The key here is to run numlockx when X starts.  I'd suggest just trying to run "numlockx" by itself and see if it works.  And if it does, add it to the bottom of the /etc/X11/xinit/xinitrc file

Also add "/usr/bin/numlockx"  just incase it needs the full path.  (I'm not sure if that's the full path though, you better to check what it is on Ubuntu

---

### Post by alecwh on 2007-06-16
It does work. by itself, I'll try your the other thing.

---

### Post by alecwh on 2007-06-16
I don't know what the full path is. :(

That single line didn't work though.

---

### Post by Nikron on 2007-06-16
Okay, I'm an idiot.  Anyway, the correct place for the line "numlockx" (assuming you have the same setup as me) would be the "/etc/gdm/Init/Default" file.  Remember to add it just before where it reads "exit 0"

---

### Post by alecwh on 2007-06-16
Ok, I went to the file, and I added it right before the line, but I can't save it. It says "read-only"

---

### Post by Nikron on 2007-06-16
> **alecwh said:**
> Ok, I went to the file, and I added it right before the line, but I can't save it. It says "read-only"

you have to open the file as a super user, (ALT+F2) gksudo gedit /etc/gdm/Init/Default

---

### Post by Ifaistos on 2007-06-17
Had the same problem.  This fixed it on the first try : 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup)

Hope it helps :-)

---

