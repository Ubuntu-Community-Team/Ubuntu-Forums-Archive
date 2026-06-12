---
title: "How do I change my default desktop?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by nickle on 2006-04-22
I am currently running Dapper. KDE is my default desktop, but I would like to change the default to GNOME. How do I do it?

---

### Post by xXx 0wn3d xXx on 2006-04-22
[QUOTE=nickle]I am currently running Dapper. KDE is my default desktop, but I would like to change the default to GNOME. How do I do it?[/QUOTE]
Log out then you will be at the login screen. Then click Sessions and select Gnome. Then enter your username and password. After that a dialogue box will ask wether you want Gnome as your default Desktop Enviroment. Click the choice that says "Make is my default session."

---

### Post by nickle on 2006-04-22
[quote=MasterChief1234]Log out then you will be at the login screen. Then click Sessions and select Gnome. Then enter your username and password. After that a dialogue box will ask wether you want Gnome as your default Desktop Enviroment. Click the choice that says "Make is my default session."[/quote]

I am afraid that when I log out, choose gonme and enter my details, no dialogue box appears...

---

### Post by mostwanted on 2006-04-22
[QUOTE=nickle]I am afraid that when I log out, choose gonme and enter my details, no dialogue box appears...[/QUOTE]

Hm, it must be different because you're using KDM, not GDM. If you install GDM and use that instead, the option should be there.

---

### Post by aysiu on 2006-04-22
In KDM, once you pick a desktop environment, that'll remain your default until you change it again.

---

### Post by nickle on 2006-04-22
[quote=aysiu]In KDM, once you pick a desktop environment, that'll remain your default until you change it again.[/quote]

Yes that is my question... How do I change it again....

---

### Post by aysiu on 2006-04-22
[QUOTE=nickle]Yes that is my question... How do I change it again....[/QUOTE] Log out. Click on **Session**. Pick the session you want. Log back in again.

---

### Post by nickle on 2006-04-22
Not meaning to be picky, but that doesn't change the default...

---

### Post by aysiu on 2006-04-22
[QUOTE=nickle]Not meaning to be picky, but that doesn't change the default...[/QUOTE] Are you using KDM or GDM?

What happens in GDM--if you pick a different session, it will always ask whether you want it to be the default or just changed for that session.

What happens in KDM--if you pick a different session, you will keep logging into that session until you pick another session.

Maybe you're using XDM or something...?

---

### Post by nickle on 2006-04-22
I installed the Dapper Kububtu beta release. I assume that uses KDM. How can I check?

---

### Post by aysiu on 2006-04-22
[QUOTE=nickle]I installed the Dapper Kububtu beta release. I assume that uses KDM. How can I check?[/QUOTE] When you're logged in, press Control-Alt-F1. Above the text login, you'll see something like ```
Starting K display manager: KDM
``` Once you've checked, press Control-Alt-F7 to get back.

---

### Post by nickle on 2006-04-22
It says: 
Ubuntu 6.06 " Dapper Drake" Development branch Setanta tty1

Setanta is my system name

---

### Post by aysiu on 2006-04-22
[QUOTE=nickle]It says: 
Ubuntu 6.06 " Dapper Drake" Development branch Setanta tty1

Setanta is my system name[/QUOTE] It doesn't say anything *above* that...?

---

### Post by nickle on 2006-04-22
No or at least nothing else was visible

---

### Post by aysiu on 2006-04-22
[QUOTE=nickle]No or at least nothing else was visible[/QUOTE] Well, we could always force it to use KDM, I suppose.

Press Control-Alt-F1.
Log in.
Type ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/xdm stop
sudo apt-get update && sudo apt-get install kdm
sudo /etc/init.d/kdm restart
``` If KDM is the only display manager installed, the first two commands should just tell you there's nothing to stop and the third command will tell you KDM is already the newest version.

---

### Post by nickle on 2006-04-22
aysiu

Igot so annoyed with the immaturity of KDE in Dapper that I deleted it completely...

Thanks for your help in any case

---

### Post by chaumurky on 2006-06-29
If I'm at a remote (ssh) terminal, what config file do I need to access to change my default session? I'm tunneling x11vnc that runs inside the session so I can't access the login screen.
 
**EDIT: found it in *~.dmrc***

---

