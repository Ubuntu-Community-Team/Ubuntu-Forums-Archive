---
title: "Opera for another user, not administrator?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by chubbiecanuk on 2007-06-12
Hi.. I'm just starting out, but I got dapper (6.06 LTS) up and running on a Compaq.. and am pretty happy so far..  Now I"m reading docs, trying to get a hold on the terminology, and kind of having fun..

I've run into my first snag tho...  I have a friend who wants to play with Ubuntu as well, and since this is an extra / exploring machine for me, I'm happy to give him access to it as well..

I created a new user id for him and his own password..

he prefers Opera while I love Firefox..

I'd like to install Opera for him so that it only appears on his desktop..

I tried to do that today and can't quite find the correct path though the security stuff..

I downloaded the Opera/Linux distribution, then tried to drag it in his folder, but of course it wouldn't let me do that..  I had thought that, as an administrator I had access to everything..   I read the section on users in the docs but it doesn't really explain all the implications of being / or not being an administrator..

so, I switched users, and downloaded the package as him..  but of course, since he's not an administrator then I could not install it..           ..   also, now I don't know where that copy of the distribution went when I downloaded it..  because it didn't end up on his desktop, like the one I downloaded ended up on my desktop...  any ideas??  or is Linux smart enough to know I already have one and not keep another copy?

I don't want to make my friend an administrator because he can be a bit impulsive..    but it would be OK if he had installation rights just in his folder..  is that possible??

also would appreciate any good links folks have to really understanding this administrative privilege stuff..

with thanks
Helen

---

### Post by Inxsible on 2007-06-12
You can create a user first. Then assign privileges to him/her. To do that go to System --> Administration --> Users and Groups.
 
or is it System --> Preferences --> Users and Groups ?
I always forget. Sorry I am not on my Ubuntu machine right now !
 
If you edit the properties of a user, you can assign privileges to the user, like accessing drives or installing software and such.

---

### Post by lazyart on 2007-06-12
Just install the app as yourself.  He can set it as his preferred browser while you leave yours set to firefox.  Create a launcher (shortcut in Windows vernacular) for it on his desktop.

---

### Post by Joseaa on 2007-06-13
The best possible option for you is to download Opera as tarball. It can save you from the hassle of installing the application.  Download the tarball, extract the contents and copy the extracted folder to the appropriate location under the user account in which you want to run it and simply run the executable.

---

