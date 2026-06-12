---
title: "booting into terminal (low resource) to run as server"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by JeffN on 2007-11-29
I am setting up a server.
I want to use the GUI to do much of the setup but then boot to command line (or unload gnome or something) so that I can release resources.

I want to be able to go back and forth easily.  It'd be nice if it were a boot option or a "boot next time to command line, but then go back" type of option.

Any ideas?

Thanks,
JeffN

---

### Post by bjarneh on 2007-11-29
this is decided by the runlevel you start up, and what programs are started for each runlevel.

ls /etc/rc2/ | grep gdm
S13gdm

tells you that gdm will start when you boot up runlevel 2 (which is the default), so X and all the window stuff will start up as well.

you can create your own runlevel if you like and have that as your default such that the server does not start up X and so on..

or start in a runlevel which does not start up X, and then just start it whenever you feel like seeing some windows

/etc/init.d/gdm start

/etc/init.d/gdm stop 

to kill it again

---

### Post by JeffN on 2007-11-30
Thanks, a couple questions...

Mine is rc2.d not rc2     same thing right?
What does the s19, s20 etc mean?  Is that a sub ordering in which they are run?

Can terrible bad things happen if I move things around from one level to the next?  I really don't want to break anything (apache2, php5, etc.)

I have a server app that I want to have run automatically.  Is this were a put the entry?

Where is the best place to learn about this kind of stuff?  Internet or book recommendations?

So do I move gdm higher rc3 or lower rc1?

How do I choose what run level it will start up to?

Thanks,
JeffN

---

### Post by bodhi.zazen on 2007-11-30
See this thread : [http://ubuntuforums.org/showthread.php?t=89491&highlight=boot](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot)

I will try to give you a *brief* overview of booting.

You boot scripts are primarily in init.d

The contents of /etc/rcX.d are links

S = start
K = kill (stop)

In ubuntu run levels 2,3,4,and 5 are all = and the default is 2

You can change the boot scripts such that level 2 = gui and level 5 = gui.

The "standard" way is with update-rc.d : 

[http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

But that assumes you know what the various services are and how you want to manage them (se my first link).

=================

In your case you can "cheat"

Since *nix is case sensitive you can disable a service by changing the S to s

so :

```
cd /etc/rc2.d
sudo mv S20GDM s20GDM
```

You could also change the S to a K ...

This allows you to track the default number.

HTH

---

### Post by hyper_ch on 2007-11-30
just out of curiosity: What do you need a gui for to setup the server services?

---

