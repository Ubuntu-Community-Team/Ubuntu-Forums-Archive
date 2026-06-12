---
title: "Software Upgrades Problem (Overwrote .mozilla/firefox, oops)"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Davey526 on 2006-06-10
E: /var/cache/apt/archives/app-install-data_0.1.33_all.deb: failed in buffer_read(fd)

There's the error I get when I try to update my software or use the add/remove programs function.

I read in the wiki at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) that (and it says this in big caps) > **do not remove the Ubuntu version of Firefox.** Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the gecko rendering engine.

Ok, before reading that since I'm a n00b that doesn't know how to install things on ubuntu, I just decided to throw the firefox folder from the tar.gz (tarball is the lingo, right?) file over the .mozilla/firefox folder. ](*,)   That's what caused the problem (I'm certain).  

My question:  Is there any way to recover this?  How can I revert the firefox back to the ubuntu version of it?  Let me know what can be done here.  So far I've tried looking around the CD for the files I need but, I have no clue where to begin on there.

Other than that, everything else has been working out real slick.

Thanks,
Dave

---

### Post by r3st on 2006-06-10
go into the synaptic package manager and re-add it

---

### Post by aysiu on 2006-06-10
Are you saying you followed *all* of the Wiki instructions, except you installed it to /home/davey/.mozilla/firefox instead of /opt/firefox?

Or did you just untar it to /home/davey/.mozilla/firefox and not follow the other instructions that symlink it to the plugins folder and the /usr/bin folder?

If it's the former, just do these commands: ```
mv .mozilla .mozilla_backup
sudo aptitude update
sudo aptitude install firefox
firefox
```

---

### Post by Davey526 on 2006-06-10
> go into the synaptic package manager and re-add it

I've been trying to see if that's possible, but it would seem as if the package manager still "thinks" that the program is installed.  I tried uninstalling the package but I get the same error.

Here's what the terminal spits out at me:
> do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the gecko rendering engine.

Maybe I'm wrong, maybe this is an unrelated problem?

> Are you saying you followed all of the Wiki instructions, except you installed it to /home/davey/.mozilla/firefox instead of /opt/firefox?

Or did you just untar it to /home/davey/.mozilla/firefox and not follow the other instructions that symlink it to the plugins folder and the /usr/bin folder?

I untarred the file and put the "firefox" folder from the tar into .mozilla.  Like I said, I did this before I encountered any kind of instructions.  Guessing kind of gives me a more indepth experience, not only will I know how to properly install stuff (because god help me if I do it wrong again) but I'll also know how to go about troubleshooting problems ;).

---

### Post by u.b.u.n.t.u on 2006-06-10
You have two gui options to install software:

1
Applications > Add/Remove

2
System > Administration > Synpatic Package Manager

* In Synaptic, click

Settings > Repositories

and put a tick in all the boxes if you want access to all that synaptic has to offer.

___

Synaptic has more software and the Add/Remove will refer to it for "advanced" tasks.

---

### Post by u.b.u.n.t.u on 2006-06-10
You can use Synaptic to unistall programs. Do a search for the program and click it if installed and you will see an uninstall option.

---

### Post by aysiu on 2006-06-10
[QUOTE=Davey526]
I untarred the file and put the "firefox" folder from the tar into .mozilla.  Like I said, I did this before I encountered any kind of instructions.  Guessing kind of gives me a more indepth experience, not only will I know how to properly install stuff (because god help me if I do it wrong again) but I'll also know how to go about troubleshooting problems ;).[/QUOTE] If that's all you did, just paste the commands I gave you before into the terminal, and you should be good.

---

### Post by Davey526 on 2006-06-10
[QUOTE=aysiu]If that's all you did, just paste the commands I gave you before into the terminal, and you should be good.[/QUOTE]

after executing "sudo aptitude install firefox" I get the same error as before.  Now I'm thinking that there's a different problem here.


> Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  app-install-data binutils-static deskbar-applet evince file-roller gdm
  gedit gedit-common gnome-app-install libfreetype6 libglib2.0-0
  libglib2.0-data libpq4 libtiff4 pcmcia-cs zenity
The following packages will be upgraded:
  firefox firefox-gnome-support libnspr4 libnss3
4 packages upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/8801kB of archives. After unpacking 32.8kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... dpkg: error processing /var/cache/apt/archives/firefox-gnome-support_1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb (--unpack):
 [b]failed in buffer_read(fd): files list for package `libglu1-mesa': Input/output error
Errors were encountered while processing:[/b]
 /var/cache/apt/archives/firefox-gnome-support_1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


---

### Post by aysiu on 2006-06-10
I did [a Google search on your error](http://www.google.com/search?hl=en&q=failed+in+buffer_read%28fd%29%3A+files+list+for+package&btnG=Google+Search), and there were only 29 results, one of which was from the Ubuntu Forums, and it didn't have a resolution.

Um, it's not looking good, but I think you're right--the error doesn't have to do with Firefox.

---

### Post by Davey526 on 2006-06-10
[QUOTE=aysiu]I did [a Google search on your error](http://www.google.com/search?hl=en&q=failed+in+buffer_read%28fd%29%3A+files+list+for+package&btnG=Google+Search), and there were only 29 results, one of which was from the Ubuntu Forums, and it didn't have a resolution.

Um, it's not looking good, but I think you're right--the error doesn't have to do with Firefox.[/QUOTE]

Anyone able to change the thread title to something like "failed in buffer_read(fd)"

Thanks for the help, I'll try futzing around with it some more, otherwise I'll just reinstall and see how that works out.

---

