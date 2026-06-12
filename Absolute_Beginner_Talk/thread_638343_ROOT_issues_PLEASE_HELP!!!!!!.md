---
title: "ROOT issues PLEASE HELP!!!!!!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-12-11
im personally having trouble installing tar because i do not have root access, ive tried the 777 method, my groups menu dosnt open, sudo is useless, i dont know the password to my root, and my C compilier cannot create executables.  Please help!!!

---

### Post by nikoPSK on 2007-12-11
why would you not know the root passwaord? Are you not the system admin? It is the same as the main users password. You can ebter root termianl by going like this (if it helps)

```
sudo su
```
or
```
sudo -i
```
or
```
sudo -s
```

---

### Post by Rocket2DMn on 2007-12-11
You will need to boot from the LiveCD and mount your existing partition.  You will then be able to change the root password (since you need root privileges to do that - using the live session allows for this)
Here's a reference to help you out [http://wiki.clug.org.za/wiki/How_do_I_reset_my_root_password%3F#Changing_your_root_password_from_bootable_media](http://wiki.clug.org.za/wiki/How_do_I_reset_my_root_password%3F#Changing_your_root_password_from_bootable_media)
Be sure to mount the correct partition.

---

### Post by bodhi.zazen on 2007-12-11
Ubuntu uses sudo. The password is the same as you log in password.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

It takes a little adjustment if you come from a system that uses su (for root access).

---

### Post by chips24 on 2007-12-11
ok thanks, the liveCD might help

---

### Post by chips24 on 2007-12-13
i reinstalled ubuntu and i got everything back, i was able to install blender, celestia and stellarium, but they run very slow, my C compilier cannot create executables still.i now have all root privileges.and is ready for 150 updates.

---

### Post by Rocket2DMn on 2007-12-13
I'm not sure what is wrong with your C compiler, but to get everything you need to building programs from source (which requires the compiler), you need to install build-essential.  Hopefully this can fix the problem
```
sudo apt-get install build-essential
```

---

