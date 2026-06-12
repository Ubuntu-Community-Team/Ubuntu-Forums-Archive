---
title: "HOWTO's"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by newbee on 2005-12-08
Sorry for another newbee question.  Can somebody point me to a howto on how to get apache working and installed?  Also MySQL and PHP support for it...
Thanks

---

### Post by cyaconi on 2005-12-08
try with
```

sudo apt-get install apache2

```

---

### Post by ssam on 2005-12-08
i just installed apache from synaptic. put your html files in /var/www/ and it works. have a search in synaptic for php and mysql. should all be fairly simple.

---

### Post by newbee on 2005-12-08
Thanks, all.....
But how do I actually start apache?

I should state also, that this will be only a development platform and will not serve anything "for real"......

---

### Post by MonsterBox on 2005-12-08
Here are a couple of links that you might find worth your while:

[http://www.lamphowto.com/]("http://www.lamphowto.com/")

[http://www.onlamp.com/]("http://www.onlamp.com/")

If you search some of your favorite Books/Tutorial sites for the acronym "LAMP" you're bound to find some more good information as well.

LAMP stands for **L**inux **A**pache **M**ySQL **P**HP (or **P**erl or **P**ython)

I've browsed a book or two at Barnes and Noble (love that store) and other places. I haven't set one up myself yet, so I don't have any hands-on to share, but hopefully those help as a place to start.

-EDIT-
Of note: in the lamphowto directions it says "log in as root". Ubuntu doesn't give you a root account so you can either process the commands with sudo or you can enter the command "sudo -s" to become root for that terminal session. Always remember, being root is dangerous and should only be used if doing sudo for a command fails first. It is possible to make a grand mess of things if you're root and forget and start doing commands. (not that i've done that or anything.... *walks away whistling*)

---

### Post by KingBahamut on 2005-12-08
[http://doc.gwos.org](http://doc.gwos.org) 

there are a number of howtos there, more than one that points to the Offiicial documentation on a LAMP build.

---

### Post by ssam on 2005-12-08
you can start services with

```
sudo /etc/init.d/apache2 start
```

replace start with stop or restart to do those.

---

### Post by rwabel on 2005-12-08
[quote=newbee]Sorry for another newbee question.  Can somebody point me to a howto on how to get apache working and installed?  Also MySQL and PHP support for it...
Thanks[/quote]

We have many howto's on the ubuntu wiki. Here is the one for the [apache stuff]("https://wiki.ubuntu.com/ApacheMySQLPHP")

It's worth checking them out

---

