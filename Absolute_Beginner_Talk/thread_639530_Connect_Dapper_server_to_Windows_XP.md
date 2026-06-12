---
title: "Connect Dapper server to Windows XP"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by scaredinjuly on 2007-12-13
Hello

I'm trying to connect a Dapper server to my windows XP machine.
The server is physically connected to windows through a lan cable and then windows is connect to the internet wirelessly.
My problem is that the windows machine says that the network cable is unplugged
And I'm really not sure what to put in /etc/network/interfaces

Any help would be greatly appreciated!

Thank you!

---

### Post by ctyc on 2007-12-13
So what exactly are you trying to do:
are you using a traight through cable or crossover or rollover?
are you trying to share the internet connection on the windows box?
are you trying to access a samba "share" on the windows box?

any details would help.

---

### Post by scaredinjuly on 2007-12-13
I'm just trying to get it so i can putty into the server from the windows box
If the server can't connect to the internet, I don't care
I just want to be able to connect machine to machine

---

### Post by hfranco on 2007-12-13
Just so that I'm clear, you have the Dapper server connected to the Windows box threw a lan cable?


*The server is physically connected to windows through a lan cable and then windows is connect to the internet wirelessly.*

Are both boxes connected threw only the lan cable?  If it is that would be the problem.  You'll have to connect the Dapper Server to a router.

---

### Post by scaredinjuly on 2007-12-13
That makes sense
Thanks a lot :KS

---

