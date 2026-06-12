---
title: "Root / cPanel"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by jorijn on 2005-07-22
Hello People..

Looks like i didnt get my answer on other forums so ill try it here.

I installed cPanel using the root terminal (It did start up first time)
then after the setup i could acces localhost:2082 and :2086 but i figured out that i need the root account to access WHM..

So i went to search for activation of the root account found it by now...
Its sudo passwd

But if  enter it as jorijn@ubuntu it says: 

Sorry, sudo must be setuid root.

when i start the root terminal again it says:

[[IMG]http://img72.imageshack.us/img72/2106/schermafdruk12yz.png[/IMG]](http://www.imageshack.us)

so i enter my password and i get:

[[IMG]http://img335.imageshack.us/img335/4347/schermafdruk27rs.png[/IMG]](http://www.imageshack.us)

So, no root access for me, So how do i fix this so i can activate the root account?

and sice i restarted my PC cPanel and Apache stopped. So how do i restart them?

Hope to get a answer soon, cPanel license ends in 15 days.. lol

---

### Post by damonw5 on 2005-07-22
This may help: [http://ubuntuguide.org/#usersadministration](http://ubuntuguide.org/#usersadministration)

Any other ideas?

---

### Post by poofyhairguy on 2005-07-22
You can use sudo before every line in the regular terminal to get the same effect.

---

### Post by jorijn on 2005-07-22
that was the problem actualy.. i couldt use sudo anymore

I guess cpanel changed my system configuration before i could do it.. lol

I resetted linux by deleting it and reinstall, Its fine now :)

---

