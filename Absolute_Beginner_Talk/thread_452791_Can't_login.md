---
title: "Can't login"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Simran on 2007-05-23
Hi,

I seem to be posting here every day the amount of times i break things :S but i guess thats the best way to learn ;)

anyways, i downloaded and installed a GDM login theme from gnome-look. and every time it gets to it as soon as i hit a keystroke it seems to reset the x server (like CTRL + ALT + BACKSPACE) or shows the same kind of messages then before it loads up again i just get a black screen with the little round loading cursor.

Then if i reset the X server the GDM login appears as normal then as soon as i type it goes black again and the cycle resets D:

Thanks 

Simran

---

### Post by paparucino on 2007-05-23
> **Simran said:**
> 
Then if i reset the X server the GDM login appears as normal then as soon as i type it goes black again and the cycle resets D:

Try to get a terminal with Ctrl-Alt-F2 then check it the links between /etc/alternatives/usplash-artwork.so points to the correct file in /usr/lib/usplash.
If it's correct, try to restore the old usplash. May the one you got is broken

---

### Post by Simran on 2007-05-23
ok i'm a bit of a noob, in the /usr/lib/usplash directory is 

 - usplash-artwork.so      usplash-theme-ubuntu.so

Where should i proceed from here?

---

### Post by paparucino on 2007-05-23
> **Simran said:**
> ok i'm a bit of a noob, in the /usr/lib/usplash directory is 

 - usplash-artwork.so      usplash-theme-ubuntu.so

Where should i proceed from here?
1) /usr/lib/usplash/usplash-theme.so is your theme
2) /usr/lib/usplash/usplash-artowork.so is the link to /etc alternatives
3) /etc/alternatives/usplash-artwork.so is the link to 1)

You must check if these link are OK. If no, correct the problem, If yes, restore the old theme.
To create the symlinks

```

ln -s /usr/lib/usplash/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so
ln -s /usr/lib/usplash/usplah.artwork.so /etc/alternatives/usplash-artwork.so

```

---

### Post by Simran on 2007-05-23
> ln -s /usr/lib/usplash/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so
ln -s /usr/lib/usplash/usplah.artwork.so /etc/alternatives/usplash-artwork.so

ok i did these commands and both came back with "file exists" so i'm assuming the links work ok.

So how would i restore the old GDM login to replace this one ?

---

### Post by paparucino on 2007-05-24
> **Simran said:**
> ok i did these commands and both came back with "file exists" so i'm assuming the links work ok.

So how would i restore the old GDM login to replace this one ?
Hold on! :-)
You get the above mentioned answer, but this doesn't mean the link is correct. The machine informs you that there is already a link with that name.

To replace the file try this:
Goto /usr/share/themes look for the directory/folder with the name of your login screen, rename the dir, select the dir with name Default and copy it giving the name of the old dir.
Suppose your theme is "Foofoo":
```

mv Foofoo XXXX_foofoo
cp Default Foofoo

```

it should work

---

