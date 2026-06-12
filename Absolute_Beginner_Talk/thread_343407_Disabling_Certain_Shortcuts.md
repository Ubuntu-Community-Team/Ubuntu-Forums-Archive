---
title: "Disabling Certain Shortcuts"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by w116tjb on 2007-01-21
So I'm relatively new to Ubuntu and I've noticed one feature that is really annoying. It's the shortcut where you hold Shift + Backspace and it logs you out and takes you back to the login screen. I looked in the Menu > System > Preferences > Keyboard Shortcuts, but it says the Logout shortcut is disabled. I know this is not true because of the 15 times I've logged myself out. Any other ways to disable this?

---

### Post by zerhacke on 2007-01-21
You must be hitting Control as well.  Control+Alt+Backspace is an X shortcut, not a Gnome one.

The easy solution is to stop hitting those keys.

---

### Post by aysiu on 2007-01-21
Do you mean Control-Shift-Backspace? Doesn't that reset the X server? That's not the same as just logging out.

Also, are you using a special window manager like Beryl or Compiz? If so, that overrides the regular "Keyboard Shortcuts" that might otherwise govern how your system operates.

---

### Post by zerhacke on 2007-01-21
> **aysiu said:**
> Do you mean Control-Shift-Backspace? Doesn't that reset the X server? That's not the same as just logging out.

To a newbie, it would look like a logout.  It would return them to the GDM/KDM screen, which the user would assume has been a logout.

---

### Post by w116tjb on 2007-01-21
Nope, it's definitely just Shift + Backspace. I actually did it like 3 times while typing this.

I dunno if it's logging me out, but it takes me to the login screen and I have to enter my username and password again. One would assume that's logging me out.

I'm also using Beryl, but I don't imagine that it'd be a shortcut in Beryl.

---

### Post by aysiu on 2007-01-21
> **w116tjb said:**
> 
I dunno if it's logging me out, but it takes me to the login screen and I have to enter my username and password again. One would assume that's logging me out. As we tried to explain before, even when you reset the X server, it *appears* you are logging out because it brings you back to the login screen. It's doing much more than logging out, though.
> 
I'm also using Beryl, but I don't imagine that it'd be a shortcut in Beryl. Actually, I think it is a shortcut in Beryl. You should look at your Beryl shortcuts. Beryl is your new window manager now. The other keyboard shortcuts get overridden by Beryl.

---

### Post by w116tjb on 2007-01-21
Okay, so I found this command through Google, but I keep getting an error message.

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

I then read something about changing the keyboard layout, so I decided to give that a try. I switched my keyboard layout from Generic 101-key PC to Generic 105-key (Intl) PC and I no longer have the problem. Thanks for your help!

And you were right, it restarts the X server, and not just logs you out.

---

