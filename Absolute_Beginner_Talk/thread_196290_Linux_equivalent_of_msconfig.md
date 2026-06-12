---
title: "Linux equivalent of msconfig"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by physcsdrk on 2006-06-14
Is there a program or a text file or something that one can edit to determine what starts up when you start ubuntu?  Specifically I am trying to stop the firewall firestarter from starting.

Thanks for any help :)

---

### Post by jason.b.c on 2006-06-14
> I am trying to stop the firewall firestarter from starting.

Why would you want to stop that..???[-X 

:confused:

---

### Post by linuchsan on 2006-06-14
update-rc.d -f service remove

---

### Post by physcsdrk on 2006-06-14
When I log in it comes up and asks for my password, which is annoying, and then gives an error, which is even more annoying.  I have other issues I'm more interested in fixing at the moment so I figured I would just turn this off and save it for later.

---

### Post by u.b.u.n.t.u on 2006-06-14
[QUOTE=physcsdrk]Is there a program or a text file or something that one can edit to determine what starts up when you start ubuntu?  Specifically I am trying to stop the firewall firestarter from starting.

Thanks for any help :)[/QUOTE]

By default Firestarter does not start. You need to add an entry to the startup menu to do that.

This,

System > Preferences > Sessions > Start up Programs

"sudo firestarter --start-hidden" added for Firestarter to start automatically.

---

### Post by u.b.u.n.t.u on 2006-06-14
[QUOTE=physcsdrk]When I log in it comes up and asks for my password, which is annoying, and then gives an error, which is even more annoying.  I have other issues I'm more interested in fixing at the moment so I figured I would just turn this off and save it for later.[/QUOTE]

Open Firestarter and,

Edit > Preferences > Firewall

then untick all the options.

"start/restart"

Maybe that will help.

---

