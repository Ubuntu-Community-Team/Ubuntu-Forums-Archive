---
title: "How to get the @ and other special keys on G4 iBook"
date: 2007-06-06
forum: Apple PPC Users
---

### Post by FischersFritz on 2007-06-06
I have just installed Ubuntu and it works quite smoothly. One thing that does not work are the special characters. I am particularly missing the @ key. Additionally I have not found out how i can switch from control the "apple" key.
Also I wanted to know, whether it is possible to have the function keys like in OSX enabled.

In the keyboard preference pane, I used the "Apple laptop" keyboard with a "Swiss-German(Macintosh)" configuration.

How do I get my keyboard working? Thanks.

---

### Post by stmiller on 2007-06-06
Which version of Ubuntu did you install? In Feisty, the keyboard volume, brightness, eject, etc should work out of the box.

Fn+brightness
Fn+volume
Fn+eject

If this is missing for some reason, type

$ sudo apt-get install gtkpbbuttons

> Swiss-German(Macintosh)" configuration.

This may be the problem with the missing '@' button. Try different configurations, or just try a standard PC swiss-german choice. (not mac)

---

### Post by FischersFritz on 2007-06-06
Thanks for the prompt reply. The special keys now just work fine. By changing the keyboard layout to "Swiss German, eliminate dead keys" I was able to locate the @ key - it is somewhat hidden by pressing function + alt + q. Not particularly elegant, but it works, thanks.

Are there any possibilities to use the "apple" key instead of the control key?

---

