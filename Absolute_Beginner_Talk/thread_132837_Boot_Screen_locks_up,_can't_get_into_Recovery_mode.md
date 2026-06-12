---
title: "Boot Screen locks up, can't get into Recovery mode to fix it."
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by jjn1056 on 2006-02-19
Hi,

This is somewhat of a crosspost from a thread I created elsewhere, but I was given the feeling from someone on IRC that it would be better for me to ask in this forum instead, so apologies for the crosspost.

Here's the orginal post for reference: [http://ubuntuforums.org/showthread.php?t=132809](http://ubuntuforums.org/showthread.php?t=132809)

Basically I messed up my Kubuntu 5.10 by trying to install Postgresql 8.1.  After I did that with Adept I found that during the boot process whenever it tried to start the postmaster, it would lock up at that point with a message like, "Starting Postgresql 8.1".  It's not a total lock because I can Cntl-Alt-Del to get the machine to restart.  But I can't get it to skip that line.  I tried Control-C already, as well as a couple of other things.  Also I tried waited like 2-3 hours while stuck at that point to see if it would eventually timeout, but that never happened.

As I mentioned in the other posting I thought I could go into recovery mode from the grub menu and uninstall the offending package.  However I can't since I keep getting prompted for a root password that I never created.  I understand this is not supposed to happen, that the kernal is supposedly patched around this.  I guess I must have done something in the week I have been playing with Kubuntu to screw this up.  What I did I am not sure.  However a few other people have reported it but no one seemed to have an answer.

So basically I am trying to either:

1) Get around the root password issue so I can try to uninstall postgresql 8.1
2) Figure out how to control the startup so I can skip the part where the kernel trys to start Postgresql.
3) solve the postgresql problem without having to boot.

All I can get to is the grub console.  I have searched and search for help on how to use this to edit the startup files but I can't seem to make progress.  I would appreciate some help.  I'll be happy to write up something on the WIKI about this afterward, since I think it's a problem newbies like me have a lot.

I would really hate to have to reinstall Kubuntu. 

Thanks for all help/suggestions

---

### Post by cronholio on 2006-02-19
You could boot from a live CD like Knoppix, mount your hard drive and manually edit your init scripts so postgresql doesn't start. Supposedly you'll have to delete the link in "/etc/rc5.d".

---

### Post by jjn1056 on 2006-02-19
I found that I could start into a recovery mode by typing 'recovery' at the prompt for the install disk.  That opened a command prompt mode where I was able to muck around with the files in init.d and stop postgresql from trying to load.  

Now I can get back into my computer :)  and try to figure out why Postgresql couldn't start in the first place.

thanks for help from everyone.

---

### Post by kont.raen on 2006-02-19
[QUOTE=cronholio]You could boot from a live CD like Knoppix, mount your hard drive and manually edit your init scripts so postgresql doesn't start. Supposedly you'll have to delete the link in "/etc/rc5.d".[/QUOTE]

Booting your system with a live CD is a superb idea - but to make sure that you are removing the correct softlink, you should take a look into your /etc/inittab and find the line, where the default runlevel for your machine is defined. The best way to do this would presumably be as follows :

1.) boot the system with a live CD
2.) mount your ubuntu root-partition for write-access (if necessary)
3.) open a terminal and cd to the etc directory of the ubuntu's root-partition
4.) type the following command :
```
grep ":initdefault:" ./inittab
```

This command's output should be something like
```
id:2:initdefault:
```

So in this example, the default runlevel of the machine would be 2 - which means that PostgreSQL most definitely is started by a link in /etc/rc2.d 

5.) cd into the respective rcX.d directory and find the link that starts PostgreSQL
```
cd rc2.d
ls -la ./*postgres*
```

which should bring up output like this
```
lrwxrwxrwx  1 root root 24 2005-10-17 19:52 /etc/rc2.d/S20postgresql-8.1 -> ../init.d/postgresql-8.1
```

6.) disable the link by changing it's name from S... into s... (the bootprocesses only look for links starting with an uppercase S).
```
mv ./S20postgresql-8.1 ./s20postgresql-8.1
```

You could delete the link with rm as well, but i don't think this makes too much sense as you might want to use the link later to start PostgreSQL manually, after your system is working again.

7.) reboot your machine.

Alright - I think that should do the trick and "revive" your system :)

---

### Post by kont.raen on 2006-02-19
Ok - seems you figured it out faster than I could tye my message :) Good to hear that your system is back in business.

---

### Post by jjn1056 on 2006-02-19
I am still glad you posted such details, because I can see that other people have had similar problems and didn't seem to find an answer.  Now if they search on the forums they have a good chance of finding it.

I also solved the problem about postgresql 8.1 not booting, it seems the default password for the postgres role is set so when my box got to the line about starting it it just hung there waiting for a password.  I changed my pg_hba.conf file to trust all local users so I could start the database and then do an 'alter role postgres' to sync the database password with the local password.

Now I feel like I got a lot done, maybe I can graduate up from beginner :) Thanks again for the help.

---

### Post by nalmeth on 2006-02-19
great job figuring that out

---

