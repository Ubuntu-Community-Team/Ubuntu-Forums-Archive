---
title: "help - services have disappeared!!"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Dwood108 on 2008-03-13
Help!

All the services have dissappered. Under system>services the dialogue box appears but there are no services listed to add or remove, just a big empty white space.

Where have they gone and how can I get them back?

Everything works OK they just dont appear in the dialogue box

I have been trying to get skype to work and uninstalled and reinstalled a few times using synapitc and aptitude and now the services have gone. They were there before.

I am using Xubuntu 7.04

Re-booting does not bring them back.

---

### Post by bswilson on 2008-03-13
Do you have the same problem when running the following command?

```
gksudo /usr/bin/services-admin
```

---

### Post by Oldsoldier2003 on 2008-03-13
try this:
```
sudo /etc/init.d/dbus start
```

then you should be able to go in an check your services...

---

### Post by Dwood108 on 2008-03-13
Thanks for your replies.

BSWilson:
when I run that command I get the following message:

```
(services-admin:6318): Liboobs-WARNING **: There was an unknown error communicating with the backends: Message did not receive a reply (timeout by message bus)
Fontconfig error: Cannot load default config file
```

OldSoldier2003:
when I run your command I get this message:

```
* system message bus already started; not starting.
```

Still the box is empty.

No joy I am afraid. Any other advice would be most welcome.
Thank you.

---

### Post by bswilson on 2008-03-19
OK, from the terminal window or a command prompt, type these 2 commands:

```
$ export FONTCONFIG_FILE=/etc/fonts
$ sudo /etc/init.d/gdm restart
```

And see if you're all set after that.

---

