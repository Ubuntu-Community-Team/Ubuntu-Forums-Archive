---
title: "[SOLVED] Adding SU programs to startup"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-07-25
Basically, i use Firestarter to set up internet connection sharing. I need the firewall running at all times, otherwise all ports i use for other programs (eg torrents) are closed. But its a pain to start it all the time. It, however, requires the su password to start. i know this is for my security, but i would love to get firestarter open without having to enter a password, ideally when i start the gnome session. I looked around, but couldn't find a solution anywhere.

SuperAndy

---

### Post by doomster on 2007-07-25
you will have to edit the  /etc/sudoers by typing in command line

```
sudo gedit /etc/sudoers 
```

and add the following line to the end of file

```
username ALL= NOPASSWD:/usr/sbin/firestarter
```

just  replace username with whatever your login is
. this should work :D

P.S. working firestarter without password should compromise your security .. :)

---

### Post by doomster on 2007-07-25
after doing this you can edit your command at System>Preferences>Session  like this 
```
sudo firestarter --start-hidden
```

to start firestarter minimised to system tray:)

---

### Post by SuperAndy on 2007-07-25
legend! thankyou!

---

### Post by SuperAndy on 2007-07-26
doesn't work...

when i make the change to sudoers, firestarter wont start at all. manually or at login.

---

### Post by por100pre1 on 2007-07-26
Open again the sudoers file:

```
sudo gedit /etc/sudoers
```

and replace this line:

Defaults !lecture,tty_tickets,!fqdn

with this:

Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

---

### Post by SuperAndy on 2007-07-26
what will that do?

---

### Post by por100pre1 on 2007-07-26
> **SuperAndy said:**
> what will that do?

That should fix a bug that prevents Firestarter to start with the method described by Doomster.

---

### Post by SuperAndy on 2007-07-26
awesome

---

### Post by por100pre1 on 2007-07-26
> **SuperAndy said:**
> awesome

Did it work?

---

### Post by SuperAndy on 2007-07-26
just to clarify, making those two changes. should firestarter now not promt for a password when i start it? becuase it still wants root privelages

---

### Post by bodhi.zazen on 2007-07-26
> **SuperAndy said:**
> what will that do?

I think that should be : ```
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME XAUTHORIZATION"
```

*but I am no expert, so feel free to correct me if I am wrong ;)

See this post for an explanation :

[http://ubuntuforums.org/showpost.php?p=3066782&postcount=41](http://ubuntuforums.org/showpost.php?p=3066782&postcount=41)

[color=blue]Thanks ddrichardson[/color]

You may need to lo-out and back in or reboot for the changes to take effect.

You should also note this is considered a minor security compromise.

---

### Post by por100pre1 on 2007-07-26
> **SuperAndy said:**
> just to clarify, making those two changes. should firestarter now not promt for a password when i start it? becuase it still wants root privelages

Yes. That's necessary because Firestarter needs root privileges.

---

### Post by SuperAndy on 2007-07-26
aye, but i need it to stop prompting for root privelages so it starts up when i login.

---

### Post by por100pre1 on 2007-07-26
> **bodhi.zazen said:**
> I think that should be : ```
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME XAUTHORIZATION"
```

*but I am no expert, so feel free to correct me if I am wrong ;)

See this post for an explanation :

[http://ubuntuforums.org/showpost.php?p=3066782&postcount=41](http://ubuntuforums.org/showpost.php?p=3066782&postcount=41)

[color=blue]Thanks ddrichardson[/color]

No argument from me, the method I posted worked for me (I had the same issue), but I rather bet to your method anyway. :)

---

### Post by SuperAndy on 2007-07-26
firestarter from the system->admin menu no longer works. but sudo firestarter from terminal does. is this right?

---

### Post by bodhi.zazen on 2007-07-26
Well, for graphical applications you should use gksudo

```
gksudo firestarter
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As far as your menu, what is the command listed to start firestarter ?

---

### Post by por100pre1 on 2007-07-26
> **SuperAndy said:**
> firestarter from the system->admin menu no longer works. but sudo firestarter from terminal does. is this right?

I'm not so sure if that's normal but... does it ask for password?

---

### Post by SuperAndy on 2007-07-26
i use sudo nano anyway. and it doesn't ask for anything. it just does nothing

and its ```

gksu /usr/sbin/firestarter

```

---

### Post by por100pre1 on 2007-07-26
> **bodhi.zazen said:**
> Well, for graphical applications you should use gksudo

```
gksudo firestarter
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As far as your menu, what is the command listed to start firestarter ?

I remember that I changed mine to: 

```
sudo /usr/sbin/firestarter
```

because the other command stopped working. Is this OK?

---

### Post by SuperAndy on 2007-07-26
ok, that one works...

---

### Post by por100pre1 on 2007-07-26
> **SuperAndy said:**
> ok, that one works...

Fine. Now you can add that command to System> Preferences> Sessions for adding Firestarter to startup.

---

### Post by bodhi.zazen on 2007-07-26
> **por100pre1 said:**
> I remember that I changed mine to: 

```
sudo /usr/sbin/firestarter
```

because the other command stopped working. Is this OK?

Yes. You *should* use the full path when evoking commands in scripts or menus.

No. I would change that to gksu, but to be honest I do not think it matters much.

> **SuperAndy said:**
> ok, that one works...

\o/

Posting the exact solution will help others. Would you clarify what worked (I assume using the full path in your menu) ?

---

### Post by SuperAndy on 2007-07-26
having sudo /etc/usr/firestarter in the sessions menu

to clarify, gksu won't work.

thank you everyone for your help!

---

