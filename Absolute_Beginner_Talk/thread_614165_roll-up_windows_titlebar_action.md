---
title: "roll-up windows titlebar action"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by skiwithpete on 2007-11-15
Hi,

I'd really like my windows to roll-up when I right click on them (as this is what I'm used to).

If I go to System>Preferences>Window Preferences  I can select "titlebar action" and roll-up on double click, but I can't choose roll-up on right click.

Is there a way to change this?

Thanks,

P

---

### Post by kelbizzle on 2007-11-15
First you want to open gconf-editor. 

Hit ALT+F2 and type:
> gconf-editor 

 Next you want to navigate to apps/metacity/general/action_right_click_titlebar and Change the value to 'toggle_shade'.
Now you shall be able to right click the titlebar and it should shade and unshade

!note this will not work if you use any other window manager such as compiz or beryl..etc.

---

### Post by skiwithpete on 2007-11-15
I punched this in, and it worked straight away, thanks.

But I have to tell you that I'm using compiz.  And it still works.

Cheers,

P

---

### Post by skiwithpete on 2007-11-16
ok,

For some weird reason, I was in Metacity windows using compiz.  

But now I'm using compiz windows decorations and the right click has stopped working.  Is there a way for compiz to see the right click as the reason to roll up the window?

Cheers

---

### Post by chenhsun on 2008-05-24
install ubuntu tweak, it is under Desktop/metacity

---

