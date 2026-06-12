---
title: "Where is my new app after doing a sudo apt-get install &quot;whatever&quot;"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-11
I just did a sudo apt-get install checkgmail and i have no idea where CheckGmail is now.  I was hoping it would go into my Applications menu up top, but no such luck.

Thanks.

Ubuntu Noob, trying to learn.

---

### Post by philinux on 2007-09-11
Not got it but I would Applications > Terminal and type in checkgmail

not all  apps install in the menu by default

---

### Post by dmber on 2007-09-11
ok, so typing "checkgmail" in the terminal got it to run, but when i close the terminal, the program closes as well.

is there an applications folder or something i just don't know about?

thanks for the help.

---

### Post by philinux on 2007-09-11
Ok but like i said I dont use it. From synaptic it says.
CheckGmail is an alternative Gmail  Notifier for Linux and other *nix
systems. It is fast, secure and uses minimal bandwidth via the use of
Atom feeds.

CheckGmail is a  system tray application that checks  a Gmail account
for new  mail.  When new  mail is present  the tray icon  changes, an
optional  animated popup  is  displayed and  a  tooltip displays  the
number and  details of new messages.  Configuration  is GUI-based and
the application is designed to be simple, elegant and unobtrusive.

 Homepage: [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Its free but you'll have do do some research

---

### Post by odiseo77 on 2007-09-11
> **dmber said:**
> ok, so typing "checkgmail" in the terminal got it to run, but when i close the terminal, the program closes as well.

is there an applications folder or something i just don't know about?

thanks for the help.

I haven't used it either, but try the following:

```
checkgmail &
```

then press enter twice, then type 'exit' on the terminal, and the app should detach from it.
By the way, I don't know if this app puts a menu entry, but if it does, maybe you have to restart your session or type 'killall gnome-panel' in a terminal in order to get it in the apps menu.

---

### Post by dmber on 2007-09-11
the ampersand did it!

thanks.  

now, how do i add it to my startup items?  is there a folder that the terminal installs new apps into?

---

### Post by odiseo77 on 2007-09-11
Sorry to ask you with another question, but by 'startup items' you mean you want checkgmail to start automatically when you start your user session? If so, are you on Gnome, or KDE? (I'm not sure how to do this on KDE, but on Gnome you can go to 'System>Preferences>Sessions' and on the first tab of the window, press 'New', then put the name of the program, and the command to launch it).

Regards.

---

### Post by philinux on 2007-09-11
system >preferences > sessions > startup programs.

Add your app in there. 

Bit like START Programs startup. And I've only been using ubuntu 4 weeks. not going back to windoze

---

