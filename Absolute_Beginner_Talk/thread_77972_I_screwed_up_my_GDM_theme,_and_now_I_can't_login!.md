---
title: "I screwed up my GDM theme, and now I can't login!"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by rskovacs on 2005-10-17
Hi everyone-

I have recently tried to start making my own GDM theme.  Everything was going fine, until I screwed up the XML.  Now when I try to start Ubuntu (with the GDM) I get an error box notifying me of the XML error, and then it loads some form of the "Circle with Flower" GDM theme, with one problem - I can't actually login; the username box is, well, inactive, I can click on it all day and nothing will happen.  So as far I'm concerned I can't login to Ubuntu, which is a major problem!!!

I'm sure there is some way to boot in recovery mode, and switch GDM themes via the command line, but I have no idea what that would be.  If anyone can offer some advice, it would be GREATLY appreciated!!!!

---

### Post by daveisadork on 2005-10-17
Probably the easiest thing would be to hit Ctrl+Alt+F1 which will drop you to a command line where you can login and then issue startx to get into GNOME and change the GDM theme.

---

### Post by erikpiper on 2005-10-17
Or ctrl-alt-backspace which should kill the xserver, login, and type startx.

(In case the above method says X is already running)

---

### Post by patrick295767 on 2005-10-17
[QUOTE=daveisadork]Probably the easiest thing would be to hit Ctrl+Alt+F1 which will drop you to a command line where you can login and then issue startx to get into GNOME and change the GDM theme.[/QUOTE]

Ctrl+Alt+F1 
then enter : 
startx -- :3 

(take care with spaces !)

then u can have X gui !!

Courage !!

Pat'

---

### Post by rskovacs on 2005-10-17
Well I tried Ctrl+Alt+F1, and yes X was already running.  But when I would use Ctrl+Alt+Bksp, it just restarted the GDM, apparently.  But don't worry, I've decided to reinstall Ubuntu 5.10 over my entire hard drive (and get rid of Windows) so I guess that works too :smile:

(Of course, there's probably an easy way to do that, but oh well...thanks for your input though.  I was surprised to see responses so quickly!)

---

### Post by Murgle on 2005-10-17
the quick way to disable gdm is to type 

sudo /etc/init.d/gdm stop

and when you want to restart type

sudo /etc/init.d/gdm start

---

