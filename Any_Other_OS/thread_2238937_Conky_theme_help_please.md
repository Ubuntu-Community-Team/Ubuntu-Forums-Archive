---
title: "Conky theme help please"
date: 2014-08-11
forum: Any Other OS
---

### Post by firas2 on 2014-08-11
Good day 

I have installed the Conky manager V2.1 and it is running and every thing is ok

But it only comes with 2 theam's ,, and when I look at the conky screen shots here   many of then Look WOW 

so I would Like to know how can I import them to the manager ?? all I see is the codes 

many thanks

---

### Post by firas2 on 2014-08-11
Ok so I fallowed the tutorial that is on here for the conky     but now all i get is this little black screen as u see in the Picture , can any one help please 

thank u


[http://i58.tinypic.com/2hcevjc.jpg](http://i58.tinypic.com/2hcevjc.jpg)

---

### Post by firas2 on 2014-08-11
ok almost there 

Still need  help im almost there  ,,,    First does this look right to u conky -c /home/to/cronkyrc ???

My rc file is named .cronkyrc and it is in home/mint I just dont know how to use the / to /      command

---

### Post by coffeecat on 2014-08-11
Your thread was unlikely to be seen in Art & Design which is for:

> Discuss various aspects of Ubuntu and Art here.


Yours is an application configuration problem. And you appear to be running Linux Mint. So...

*Thread moved to **Other Operating Systems and Projects**.*

---

### Post by CantankRus on 2014-08-11
> **firas2 said:**
> ok almost there 

Still need  help im almost there  ,,,    First does this look right to u conky -c /home/to/cronkyrc ???

My rc file is named .cronkyrc and it is in home/mint I just dont know how to use the / to /      command

There are two ways to run a conky config.
**1) **Place a config in your home folder named [B].conkyrc 
[/B]When you run just "conky" it will look for and use this config.

**2) **Alternatively you can name and save a config whatever you like, wherever you like 
and specify the config with the -c option.
conky -c [COLOR=#808080]/full/path/to/config[/COLOR] 
eg for me the command would look something like this
conky -c /home/glen/conky/configs/fav-conky


If you want more configs for Conky Manager,
go to the home page.... [http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html)
and scroll down to the Theme Packs section and download "Official Theme Pack #1 (15 MB)"
Conky Manager has an import theme button.
Conky Manager is just an application to easily run a select set of conky configs.

PS: The conky you see running in your #2 post is using the default config from /etc/conky/conky.conf 
If you run "conky" it will use this config if there is no **.conkyrc** config in your home folder or it is malformed/misnamed.
Running conky in terminal will show any errors.

---

### Post by Habitual on 2014-08-11
looks "[familar]("http://forums.linuxmint.com/viewtopic.php?f=212&t=175442")"

---

### Post by CantankRus on 2014-08-11
Exposed by a double agent. :p

---

### Post by Habitual on 2014-08-12
> **CantankRus said:**
> Exposed by a double agent. :p
It's all good.

---

### Post by firas2 on 2014-08-24
> **CantankRus said:**
> There are two ways to run a conky config.
**1) **Place a config in your home folder named [B].conkyrc 
[/B]When you run just "conky" it will look for and use this config.

**2) **Alternatively you can name and save a config whatever you like, wherever you like 
and specify the config with the -c option.
conky -c [COLOR=#808080]/full/path/to/config[/COLOR] 
eg for me the command would look something like this
conky -c /home/glen/conky/configs/fav-conky


If you want more configs for Conky Manager,
go to the home page.... [http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html)
and scroll down to the Theme Packs section and download "Official Theme Pack #1 (15 MB)"
Conky Manager has an import theme button.
Conky Manager is just an application to easily run a select set of conky configs.

PS: The conky you see running in your #2 post is using the default config from /etc/conky/conky.conf 
If you run "conky" it will use this config if there is no **.conkyrc** config in your home folder or it is malformed/misnamed.
Running conky in terminal will show any errors.

thank u very Much sir 

Just Now got the time to read ur post ,,,   sorry  i was working on  installin every thing  on a new ssd  and a few more upgrades 

many thanks :smile:

---

