---
title: "Keyboard suddenly not mapped correctly, Macbook 4.1"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by theverant on 2008-06-08
Everything was going fine.  Now, my Macbook keyboard is no longer mapped correctly I can only get numbers and some symbols, no letters.  An external USB keyboard (windows) works just fine.  Login works fine, so it must be something with a user keyboard config file.  

No idea where to start with this.  Anyone have ideas?

---

### Post by _alex_ on 2008-06-08
I ran into that at one point. I think I somehow managed to activate the numlock key. I just randomly pressed keys on the keyboard, and it went back to normal (not sure what button did it though, maybe you'll get lucky too :))

---

### Post by theverant on 2008-06-08
> **_alex_ said:**
> I ran into that at one point. I think I somehow managed to activate the numlock key. I just randomly pressed keys on the keyboard, and it went back to normal (not sure what button did it though, maybe you'll get lucky too :))

Whoooooaaaa.  I think you are right!  I've switched it back and forth twice now.  I can't seem to find what key does it though.  Does anyone know for sure what key combo accomplishes this?

---

### Post by _alex_ on 2008-06-08
> **theverant said:**
> Whoooooaaaa.  I think you are right!  I've switched it back and forth twice now.  I can't seem to find what key does it though.  Does anyone know for sure what key combo accomplishes this?

xmodmap lists the following for the numlock key:
```
mod2        Num_Lock (0x4d)
```

Not sure what key combination produces that key code...  In any case, the new macbooks do not have a numlock key, so this is wrong to begin with.

What keyboard model do you have selected in Keyboard Preferences?

---

### Post by theverant on 2008-06-08
> ...In any case, the new macbooks do not have a numlock key, so this is wrong to begin with.

What keyboard model do you have selected in Keyboard Preferences?

Correct about there being no numlock key, however now that I think about it, the key layout was definitely a numpad layout.  That would indicate that Macbooks still have a hotkey combo to enable numpad.... wouldn't it?

I have generic 104 in keyboard layout.  BUT, in my panic, I set up the keyboard based on the [Gentoo Apple hardware help page]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Apple_Keyboard").  Does this override the Gnome keyboard setup?

xorg.conf:
```
Section "InputDevice"
        Identifier  "Keyboard1"
        Driver      "keyboard"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
#        Option      "XkbVariant" "intl"
        Option      "XkbOption" "numpad:mac"
EndSection 

```

---

### Post by _alex_ on 2008-06-08
> **theverant said:**
> That would indicate that Macbooks still have a hotkey combo to enable numpad.... wouldn't it?

Well a lot of PC laptops have the numeric keypad accessible through the function/numlock key, so all this means is that the keyboard layout you use is the wrong one.

> **theverant said:**
> I have generic 104 in keyboard layout.

Try using "Macbook/Macbook Pro (Intl)" setting for the vendor Apple in Keyboard Preferences.

---

### Post by theverant on 2008-06-08
> **_alex_ said:**
> Well a lot of PC laptops have the numeric keypad accessible through the function/numlock key, so all this means is that the keyboard layout you use is the wrong one.



Try using "Macbook/Macbook Pro (Intl)" setting for the vendor Apple in Keyboard Preferences.

I only switched it to 104 key AFTER I started having problems with numberpad being switched on.  It was Macbook before, and I've since switched it back.  Doesn't seem to really do much of anything, really.

So now I'm really just wondering what switched the keyboard?  I've done it twice in the last couple weeks.  The first time I had no idea what happened, and I had no idea about a fix, and so I did a reinstall (was a fresh install anyway, it was no big deal).  Second time was today.  I wanna find out what that key combo is for next time.

It is something hardware on the Macbook that does the switch, right?  It has nothing to do with Gnome?

---

### Post by cyberdork33 on 2008-06-08
Hit F6 twice (or likely in your case, Fn+F6).

---

### Post by theverant on 2008-06-08
> **cyberdork33 said:**
> Hit F6 twice (or likely in your case, Fn+F6).

I found the F6 switch in some other places online.  This key combo does nothing on my Macbook (2.4GHz Penryn).  I can't seem to find some new key combo, but it seems like there is one.  Either that or there is a bug?

Now that I think about it, login worked fine.  It was only once Gnome had loaded that the numberpad started.  So that would indicate it was something Gnome did, right?

---

### Post by cyberdork33 on 2008-06-08
It may be that gnome is set to turn on numlock by default on startup. (Not neccesarily a bug). The penryn machines seem to have a bug that requires fixing to enable the Fn key, and this is needed, because the F6 key is actually Fn+F6 on the portables' keyboards.

[https://bugs.edge.launchpad.net/mactel-support/+bug/207127](https://bugs.edge.launchpad.net/mactel-support/+bug/207127)

---

