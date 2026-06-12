---
title: "Changing file permissions using &quot;sudo&quot;"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2005-07-22
Hey,

I can't change the file permissions for /etc/hosts without using sudo... how do i go about that... and is there anyway to log into the root account... the account i log into at the startup is kris...

---

### Post by Knome_fan on 2005-07-22
sudo -s and then giving your users password logs you into a root account-

sudo chmod whatever let's you change permissions.

However, why do you want to change the permissions of /etc/hosts?

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=Knome_fan]sudo -s and then giving your users password logs you into a root account-

sudo chmod whatever let's you change permissions.

However, why do you want to change the permissions of /etc/hosts?[/QUOTE]
 > sudo -s and then giving your users password logs you into a root account-

sudo chmod whatever let's you change permissions.

However, why do you want to change the permissions of /etc/hosts?

because I need to add dwyernpayne 127.0.0.1 to it so i can fix the problem in the following screenshot
[IMG]http://members.dodo.net.au/~kausten/screensh.PNG[/IMG]

---

### Post by Knome_fan on 2005-07-22
Ah, found your other thread.

1. You don't need to change the permissions of this file to edit is, as root is allowed to edit it, so using sudo gedit (or your favorite editor) /etc/hosts should also do the trick.

2. I'm not really sure that adding this to your hosts file will solve the problem. I'm not an expert when it comes to modems, but you could try to set up your modem using the graphical interface under System -> System Administration -> Network (I think that's how it's called, I'm not on an english system so I can't be certain). There you'll find a nice graphical environement to set up your dialup connection.

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=Knome_fan]Ah, found your other thread.

1. You don't need to change the permissions of this file to edit is, as root is allowed to edit it, so using sudo gedit (or your favorite editor) /etc/hosts should also do the trick.

2. I'm not really sure that adding this to your hosts file will solve the problem. I'm not an expert when it comes to modems, but you could try to set up your modem using the graphical interface under System -> System Administration -> Network (I think that's how it's called, I'm not on an english system so I can't be certain). There you'll find a nice graphical environement to set up your dialup connection.[/QUOTE]
 OK, i am trying to install my modem driver right... and then wham! I get this... how do i install my driver? =(

[IMG]http://members.dodo.net.au/~kausten/ERROR1.PNG[/IMG]
[IMG]http://members.dodo.net.au/~kausten/ERROR2.PNG[/IMG]
[IMG]http://members.dodo.net.au/~kausten/ERROR3.PNG[/IMG]

---

### Post by Knome_fan on 2005-07-22
Puh, as I said I'm far from being an expert when it comes to modems, but I noticed that the driver seems to be made for an other kernel version, so I doubt it will work.

However, searching the forum it seems that ubuntu already provides these drivers with the restricted-modules.

Just following these instructions should be the easiest way:
[http://www.ubuntuforums.org/showthread.php?t=21312&highlight=ltmodem](http://www.ubuntuforums.org/showthread.php?t=21312&highlight=ltmodem)
[http://www.ubuntuforums.org/showpost.php?p=103634&postcount=4](http://www.ubuntuforums.org/showpost.php?p=103634&postcount=4)

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

Hope this helps.  :grin:

---

### Post by KrisDwyer on 2005-07-22
[QUOTE=Knome_fan]Puh, as I said I'm far from being an expert when it comes to modems, but I noticed that the driver seems to be made for an other kernel version, so I doubt it will work.

However, searching the forum it seems that ubuntu already provides these drivers with the restricted-modules.

Just following these instructions should be the easiest way:
[http://www.ubuntuforums.org/showthread.php?t=21312&highlight=ltmodem](http://www.ubuntuforums.org/showthread.php?t=21312&highlight=ltmodem)
[http://www.ubuntuforums.org/showpost.php?p=103634&postcount=4](http://www.ubuntuforums.org/showpost.php?p=103634&postcount=4)

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

Hope this helps.  :grin:[/QUOTE]
 thank you

---

### Post by aruna chandu on 2007-12-28
Hey, I have some what similar issue.
can some one look into this problem?

I edited  /etc/hosts file usig sudo.
I have commented local host and then pointed to other server(which is a dummy server).
But next time when i tried to edit the hosts file it is giving problem.
It throws up an error saying gethostname not found.

Thanks
Aruna Chandu

---

### Post by scxtt on 2007-12-28
you shouldn't comment out "localhost", ever.  you'll probably have to boot into "recovery mode" and uncomment it.

---

### Post by aruna chandu on 2007-12-29
Hey thanks for the reply.
But is there any other way.
I am into QA and i need to test by pointing to other server and commenting local host.
I did the same thing in Win and Mac. It worked without any issues.
problem is only with ubuntu.

Thanks
Aruna Chandu

---

### Post by scxtt on 2007-12-29
you shouldn't be commenting out "localhost", period.  it's how the computer refers to itself - and you're already noticing adverse effects from doing it ...

if you want to set a host name, there are better ways and if you want FILES DNS definitions, just add them - don't remove.

are you saying you can't connect to the host (ssh?) and don't have physical access?

---

### Post by nwpuliuhs on 2007-12-29
hi, I'm a newbie too,and ever have the same problem, do you know how I solve this?

---

