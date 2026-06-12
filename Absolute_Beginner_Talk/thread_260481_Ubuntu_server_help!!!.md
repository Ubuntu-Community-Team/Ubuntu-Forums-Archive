---
title: "Ubuntu server help!!!"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Th3N@tive on 2006-09-18
Hey guys well i am trying to install ubuntu server i get throught the install and all goes well. After i install the gui so i can have the desktop seein as how im a n00b at it i wanted a familiar enviroment. While installing it it gives me a few errors abotu fonrts but  than it installs ok. I am than brought to the commanc prompt at which point i restart the pc. Booting seems to go well and when i get to the login screen i cannot move the cursor or type than after a few seconds it freezes. can anyone please help me.

---

### Post by bodhi.zazen on 2006-09-18
sudo aptitude install ubuntu-desktop.

---

### Post by Th3N@tive on 2006-09-18
No i know the command i can install it fine.but when i reboot and i am brought to my logon screen it freezez

---

### Post by croak77 on 2006-09-18
If you don't want the entire ubuntu-desktop, which I assume that you don't otherwise why do a server install, sudo aptitude install x-window-system-core xserver-xorg gnome-core gdm. That will get you a very basic GNOME install. Then you can install what you want, synaptic, alacarte (GNOME menu editor), evolution, gimp, etc. If you want a KDE desktop. Install kde-core kdm instead of gnome-core gdm.

---

### Post by bodhi.zazen on 2006-09-18
Change to tty1:

Ctrl-Alt-F1.

---

### Post by Th3N@tive on 2006-09-18
wow oyu guys are quite helpful ill try these things now thanks

---

### Post by Th3N@tive on 2006-09-18
one question im know im such a n00b but what is a kde desktop and what is a gnome desktop?

---

### Post by Kilz on 2006-09-18
> **Th3N@tive said:**
> one question im know im such a n00b but what is a kde desktop and what is a gnome desktop?

[http://www.psychocats.net/essays/kdevsgnome.php](http://www.psychocats.net/essays/kdevsgnome.php)

Personaly I would use fluxbox or icewm on a server. Gnome and kde use way to much resources. My server uses icewm. Its a lightweight desktop that has packages in the repositories.

---

### Post by Th3N@tive on 2006-09-18
ok well what is the command for using those

---

### Post by Kilz on 2006-09-18
> **Th3N@tive said:**
> ok well what is the command for using those

I did it from inside Gnome then uninstalled Gnome. But there are pages on how to install them in the wiki. [Icewm ]("https://help.ubuntu.com/community/IceWM") or [Fluxbox]("https://help.ubuntu.com/community/Fluxbox"). I tried both and found icewm easier to setup. Fluxbox is done with files. Icewm has setup applications caller iceme and icepref.

---

### Post by Th3N@tive on 2006-09-18
oh no i tries rebooting into kdm and now i have a cannot open theme error and it froze
:frown:

---

### Post by croak77 on 2006-09-18
Just hit the OK button. The error does not prevent you from using KDE.

---

### Post by Th3N@tive on 2006-09-19
well see thats just it the cursor wont move at all so see i cannot hit ok

---

### Post by bluefrog on 2006-09-20
in my opinion you install a server with no gui if your machine is low at RAM otherwise don't bother and just install "normal" ubuntu and server packages on top of it.

James

---

### Post by Th3N@tive on 2006-09-21
> **bluefrog said:**
> in my opinion you install a server with no gui if your machine is low at RAM otherwise don't bother and just install "normal" ubuntu and server packages on top of it.

James

ok do you mean juist install ubuntu desktop and add stuff on to it if so how do i do that

---

