---
title: "[SOLVED] nothing happens after pswrd entered - FROZEN and STUCK on the orange screen"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-06
still trying to get this taken care of.

After entering my password and hitting ENTER The launch begins but freezes at the organe/brownis screen.


Ctrl + Alt + F1 or F2 works.

What is the next step?

What is behind this error?

Xserver?

maybe installing ubuntu-desktop?

what is going on?


thanks

Robi

ps. As a temporary work around I know I can install lynx for browsing, but what word processors are there that are text based?

---

### Post by finer recliner on 2007-11-06
text based text editors include emacs, nano, and vi.

for emacs you may need to call it as "emacs -nw" since it usually launches a gui version by default in ubuntu. 

if you go ctrl + alt + f1 and log in through there, and then type "startx" what happens? if there's an error, please post.

---

### Post by beanco on 2007-11-06
furner, thanks i will take care of it when i get home


robi

---

### Post by dbott67 on 2007-11-06
It could be a corrupt Gnome session (i.e. something munged in the .gconf, .gnome directories, etc.).  Try this:

    * When at the login screen, press CTRL+ALT+F2 to open a terminal
    * Log in 
    * Type cd ~
    * Type mv .gconf .gconf.old
    * Type mv .gconfd .gconfd.old
    * Type mv .gnome .gnome.old
    * Type mv .gnome2 .gnome2.old
    * Type mv .gnome2_private .gnome2_private.old
    * Type mv .metacity .metacity.old
    * Type mv .nautilus .nautilus.old
    * Type mv .gtkrc-1.2-gnome2 .gtkrc-1.2-gnome.old
    * Switch back to the login screen by pressing CTRL+ALT+F7.
    * Press CTRL+ALT+BACKSPACE to get back to the graphical login
    * Log in.

Let us know.

-Dave

PS - if you can't login at all, try using failsafe mode.

---

### Post by Dr Small on 2007-11-06
And, in a single command:
```
cd ~ && mv .gconf .gconf.old ; mv .gconfd .gconfd.old ; mv .gnome .gnome.old ; mv .gnome2 .gnome2.old ; mv .gnome2_private .gnome2_private.old ; mv .metacity .metacity.old ; mv .nautilus .nautilus.old ; mv .gtkrc-1.2-gnome2 .gtkrc-1.2-gnome.old
```

---

### Post by Pinocheckio on 2007-11-06
> **finer recliner said:**
> text based text editors include emacs, nano, and vi.

for emacs you may need to call it as "emacs -nw" since it usually launches a gui version by default in ubuntu. 

if you go ctrl + alt + f1 and log in through there, and then type "startx" what happens? if there's an error, please post.

i 've got same problem
when entering startx :
invalid MIT-MAGIC-Cookie-1 keygivingup
xinit: resource temporarily unavalailable (errno 11) : unable to connect to X server
xinit: No such process (errrno 3) :server error

---

### Post by twiceasworn on 2007-11-06
> **Pinocheckio said:**
> i 've got same problem
when entering startx :
invalid MIT-MAGIC-Cookie-1 keygivingup
xinit: resource temporarily unavalailable (errno 11) : unable to connect to X server
xinit: No such process (errrno 3) :server error

That sounds like a driver issue.  What driver and video card are you running?

---

### Post by beanco on 2007-11-06
> **finer recliner said:**
> text based text editors include emacs, nano, and vi.

for emacs you may need to call it as "emacs -nw" since it usually launches a gui version by default in ubuntu. 

if you go ctrl + alt + f1 and log in through there, and then type "startx" what happens? if there's an error, please post.

I got

```
xauth: creating auhtority file /home/rob/ .serverauth.4881
xauth: creating auhtority file /home/rob/ .Xauthority
xauth: creating auhtority file /home/rob/ .Xauthority


Fatal server error:

Server is already active for display 0

If this server is no longer running, remove /tmp/ .X0-lock and start again


Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key giving up

xinit: unable to connect to X server
xinit: No such process (errno 3): Server error.
```


I will see what the other tips in the thread are.... but what does the above mean?

Robi

---

### Post by beanco on 2007-11-06
OK so I checked, sounds like a driver issue then


How to check what driver I am using?

How to check for what video card?

What causes this to happen?

My son was trying to edit some video on his account and the problem logging in stated there..... then I added some torrent prgs to my account and when I tried to log back on got the error.

robi

---

### Post by beanco on 2007-11-06
fuddling round with sg I found on an other thread earlier today i tried this



sudo aptitude update

sudo aptitude install ubuntu-desktop



then sudo /etc/init.d/gdm start



I waited and nothing happened so I tried


sudo dpkg-reconfiure xserver-org

there was some error msg i think sg about not having xserver so, if I remember correctly i tpyed in

sudo install xserver-org

then ctr + alt F7

then ctrl + alt + backspace


OK. I am sure none fo this makes sense. but somehow I got logged back onto my account.

now what I am wondering is if I will be able to log of and then back on.

robi

---

### Post by beanco on 2007-11-06
ok, i wante dto send some emails in evolution but it did not want to start. seems i have to set it up all again.

I can do that, easy enough... what I cannot do is see all old emails... so where do I find them?


Robi

---

### Post by Pinocheckio on 2007-11-06
> **twiceasworn said:**
> That sounds like a driver issue.  What driver and video card are you running?

nvidia geforce 5200 with 100.14.19 driver.
it's weird because envy and xserver detect my card as a 6200

---

