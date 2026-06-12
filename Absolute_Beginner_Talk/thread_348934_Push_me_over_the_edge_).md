---
title: "Push me over the edge :)"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Sugar on 2007-01-29
Hi all

After being a casual linux user since redhat 5.1(which took about 3 weeksto get working on an old ibm laptop). And using debian, fedora, ubuntu for server stuff. Im finally feel im ready to take the plunge with my worklaptop, and go full desktop linux(ubuntu), since all my hardware know works pretty much out of the box, well aint taking 3 weeks anymore :). Since its for work, they require me to do some stuff. support some .net apps, ill do that in a virtual machine, only happens like once a month. 

My other cant live without app is SecureCRT, im a server/network admin. For those that dont know SecureCRT, it does ssh/telnet/serial stuff etc. And lets me organise all my +500 switches/server/routers/accesspoints etc into logical groups. And attach Macros so fx with 10 mouse clicks it log into 10 switches, sets them in enable mode, turns on monitoring etc etc. 
I also sometimes have to use a serial cable, to conf an accesspoint/switch which i do via an usb/serial converter.

Anyone have an idea that either replaces SecureCRT with likewise functionality on the linux desktop(and no i dont want to write 500 shell scripts :) ) with one or more apps. Have google a bit, but not really found anything, or im using the wrong keywords.

Thx Very much for any suggestions

/Sugar

---

### Post by benuski on 2007-01-29
I'm not an expert at this sort of thing, but I did find an old mailing list post that suggested the program Putty.  Have you tried that?

---

### Post by Tomosaur on 2007-01-29
Not aware of anything like SecureCRT, but that's probably because I haven't tried looking for it :P

You can set up stuff like that fairly easy by writing some simple scripts (perhaps with Zenity, which gives you some very basic GUI functionality). I personally have a whole load of alias' which allow me to ssh into different accounts and stuff. You can add different alias' to your .bashrc (in your home dir), by appending a line like this:

```

alias <command>=<commands to run>

```

For example, if you wanted to log into your work computer using ssh:
```

alias work='ssh sugar@my.work.com'

```
You can then just use the 'work' command to run the ssh command.

There may well be a GUI app which allows all this kind of stuff to be organised like SecureCRT, but I personally am not aware of one - but I find the command line is very extensible and I can organise a whole bunch of different tasks very easily with a few scripts.

EDIT: Woops, ignore me, just re-read your post and saw the bit about shell scripts :P

---

### Post by dougfractal on 2007-01-29
You could give **wine** a try. 
It would save you rewriting all those scripts.  What language are your scripts in?

[http://appdb.winehq.org/appview.php?iAppId=492&sRating=Gold]("http://appdb.winehq.org/appview.php?iAppId=492&sRating=Gold")

---

### Post by steve.horsley on 2007-01-29
It is worth trying wine. I know that the serial port works in wine because I used a windows program to load new sw into a PVR from wine hte other week. And of course, networking works in wine.

I'm not aware of any Linux progs matching the description you give for Secure CRT, although you might be able to rustle something up with netcat and some scripts eventually.

---

### Post by Sugar on 2007-02-10
Thx for all the replies. And i might just try out the shell scripts, (just after i tried it with Wine)

/Sugar

---

