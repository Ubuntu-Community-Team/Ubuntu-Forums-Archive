---
title: "Changed the keyboard layout for the login screen"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-04
I mistakenly changed it to US keyboard layout.

Setting the keyboard from the Preferences now doesn't do anything. I still can't type my password as easy as I once could.

But once I am in X everything runs ok. Odd thing.

I don't know how to fix this. I googled but didn't get interesting results. Anyone can help?

---

### Post by expatCM on 2007-07-04
You appear to be based in Turkey.  Were you using the Turkish layout?

If that is the case, were you using scim as the input editor?

If that is the case have you checked that your language support is still selected for Turkish and that scim is still working?

---

### Post by Majorix on 2007-07-05
Yes I was using the Turkish layout. And no, I wasn't using scim. Thanks for the reply :)

I guess I found a way to fix my problem... When I change the keyboard layout under dkpg-reconfigure xserver-xorg it seems to change the keyboard layout for the login screen too.

But now I don't know what I have to enter in there for it to correctly recognize my keyboard. Is there like a list where I can check and pick my layout and enter it in there?

Thanks.

---

### Post by AndyCooll on 2007-07-05
```
sudo gedit /etc/X11/xorg.conf
```

In there there is a line for your keyboard default settings (can't remember exactly where, at work at the moment and not at my Linux box) and one of the settings is the default language. You need to edit that and replace it with your particular keyboard language code as appropriate. I'm in the UK so mine is "en-gb" for instance, I think "tr" is Turkish.

:cool:

---

### Post by Majorix on 2007-07-05
Wow thanks a lot, it works now :)

I was worried about all those nodeadkeys and stuff like that that the configuration tool asked, but simply changing that line to "tr" worked.

And it also asked me one question after restart: "The X and the Gnome keyboard layouts differ, which would you like to use?" I chose "Use the X settings" and now it is ok. Hope this helps other people who have the same problem.

---

