---
title: "[SOLVED] Problems installing Pidgin"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-21
I've tried to install Pidgin on 2 seperate Ubuntu 7.04 (Gnome) machines and keep running into trouble.  I am following the directions here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.0_.28former_GAIM.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.0_.28former_GAIM.29)

Right now, this is the error I get after running WGET, (it downloads fine) and then this command:
```
sudo dpkg -i pidgin_2.0.2-1_i386.deb
```

```

jason@SAMSON:~$ sudo dpkg -i pidgin_2.0.2-1_i386.deb
Password:
Selecting previously deselected package pidgin.
dpkg: regarding pidgin_2.0.2-1_i386.deb containing pidgin:
 pidgin conflicts with gaim
  gaim (version 1:2.0.0+beta6-1ubuntu4) is installed.
dpkg: error processing pidgin_2.0.2-1_i386.deb (--install):
 conflicting packages - not installing pidgin
Errors were encountered while processing:
 pidgin_2.0.2-1_i386.deb
jason@SAMSON:~$ 
```

I tried uninstalling GAIM and GAIM DATA through Synaptic, and then I ran that same cmd again and got this...

```
jason@SAMSON:~$ sudo dpkg -i pidgin_2.0.2-1_i386.deb
(Reading database ... 116843 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.0.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on tcl8.4 (>= 8.4.5); however:
  Package tcl8.4 is not installed.
 pidgin depends on tk8.4 (>= 8.4.5); however:
  Package tk8.4 is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
```

This is the same error that I get when trying on my Ubuntu 7.04 Laptop also.  I guess that I need to install something else, but the How-To guide never mentions anything.  Suggestions?

---

### Post by Majorix on 2007-07-21
Did you install the missing dependencies mentioned in the second code block?
```
sudo aptitude install tcl8.4 tk8.4
```

It is a pity that the guide doesn't do any troubleshooting :(

---

### Post by DBStevens on 2007-07-21
Yes install tcl using Synaptic and retry the Pidgin.

The reason the how-to didn't mention this stuff is that the folks who did the install never ran into the issue because their system already had the other parts installed.

Every time you do an install you can run into this kind of situation.

That is why folks keep harping on using Synaptic and its base system  to do installs.

---

### Post by kc5hwb on 2007-07-21
No, thats what I was kinda wondering, if that was the way to install them.  I couldn't find any reference to them in the guide.  :(

---

### Post by kc5hwb on 2007-07-21
> **DBStevens said:**
> Yes install tcl using Synaptic and retry the Pidgin.

The reason the how-to didn't mention this stuff is that the folks who did the install never ran into the issue because their system already had the other parts installed.

Every time you do an install you can run into this kind of situation.

That is why folks keep harping on using Synaptic and its base system  to do installs.

That makes sense, I am trying that now

---

### Post by kc5hwb on 2007-07-21
oh sweet, when I reloaded Synaptic after this installed failed, it told me I had a Broken Package.  So I tried the fix and it automatically checked TCL8.4 and TK8.4

---

### Post by Majorix on 2007-07-21
I bet it also checked gaim?

---

### Post by kc5hwb on 2007-07-21
> **Majorix said:**
> I bet it also checked gaim?

Nope.  I am now logged into Pidgin... it put it in my Apps menu, under Internet.  GAIM isn't in that menu anymore after I removed it.


What are these Ubuntu PLugin Packs for?

```
wget http://www.kalpiknigam.com/blog/uploads/purple-plugin-pack_1.0-1_i386.deb
```

---

### Post by DBStevens on 2007-07-21
"What are these Ubuntu PLugin Packs for?"

Don't know, maybe they'll have additional unresolved dependances so you can practice installing things ;-).

Enjoy.

---

### Post by fakie_flip on 2007-08-01
How can you get off the record compiled for pidgin? It seems impossible. I've tried a lot.

---

