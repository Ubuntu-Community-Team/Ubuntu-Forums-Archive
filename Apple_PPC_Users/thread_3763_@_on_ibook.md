---
title: "@ on ibook"
date: 2004-11-09
forum: Apple PPC Users
---

### Post by moly82 on 2004-11-09
hi all, i'm a pretty new user of ubuntu, which i installed in my ibook g4... it's very great this distribution! :)


i'm having some problems trying to type the @, i can't do that on my ibook, do you know how i can do that?

my keyboard is the italian one, almost all the others symbols work, for example the # and the others symbols...

thanx in advance bye! :)

---

### Post by sumanjay on 2004-11-10
Just a suggestion - edit the XF86Config-4 file and change the XkbLayout option to "it". If you need steps to go about this - 
1) Open a terminal and type in ** sudo nano /etc/X11/XF86Config-4** to edit the file.
2) Press Ctrl+W and type in "xkblayout" to search. Change the option there from "us" to "it".
3) Press Ctrl+X to quit and save the file as you go.
4) Now restart X11 using any technique or by Pressing Ctrl+Alt+Delete.

HTH

---

### Post by patrickallo on 2004-11-10
I'm having more or less the same problem: I've installed Ubuntu on an old iMac (Bondi Blue - slot-loading G3), and a few specialcharacters are missing.
Essentially: @, but also backslash and several kinds of braces.

Changing the keyboard-layout doesn't do the job: the characters I need are still missing. Looks like those small iMac keyboards don't match with the normal keyboard layout. Moreover there's no way to access characters which are usually obtained with 'alt'.

Looks like it'll have to be configured manually.
But how?

---

### Post by sumanjay on 2004-11-10
I came upon this link which should be of some help - 
[Creating custom keyboard layouts](http://www.linux.com/article.pl?sid=04/06/03/1558258) 

I haven't had time to try it out yet. Good luck!

---

### Post by moly82 on 2004-11-10
I have already tried several it layouts, but also us, fr etc but I can't type in the @ character...

i will try with the link you posted thank you! :)


why i didn't but the ibook with us layout?  :-k  :(

---

### Post by gilgamesh on 2004-11-11
on my ibooki have to go to poste de travail (i think workspace (the second menu item on top) then preferneces du bureau the seventh item, then keyboard
choose the second tab and in the upper scroll choice choose -macintosh no-description-

the @ works fine as the delete but i can't still get the braces 

G

---

### Post by moly82 on 2004-11-11
thanx i'll try :)

bye!|

---

### Post by malmjako on 2004-11-16
If you are running Gnome or KDE, go to the Keyboard preferences -> Layout options -> Third level choosers and select Win keys. On my swedish keyboard, the Cmd-keys on the keyboard are interpreted as Win-keys and by pressing Cmd-2 (Win-2) I can type @. {[]}\$¡£?¥±~ all work fine as well, by pressing Cmd-{something}.

Hope this works for you.

--
Jakob Malm

---

### Post by patrickallo on 2004-11-17
thanks,
it works for me.
@ etc. are not where they used to be, but they're there nevertheless

---

### Post by reda on 2005-06-28
Hello Everyone,

I have an Ibook G3 12', and I just changed my keyboard for a 'macintosh' one and that works fine... I am more than happy.

You need to go to 'system' tab (third menu on the top bar), then preferences, keyboard 
on the 2nd tab you should find Keyboard model which should be set to 'Macintosh'.

Thanks

Enjoy
R

---

