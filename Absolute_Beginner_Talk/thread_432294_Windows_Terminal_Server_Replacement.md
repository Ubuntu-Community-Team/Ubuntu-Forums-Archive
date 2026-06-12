---
title: "Windows Terminal Server Replacement"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by random.brown on 2007-05-03
Hi,

My employer wants me to set up a server to allow 5 remote users to log into our VPN, and then create a GUI login session (each one separate) and run an accounting package.

Now, Windows terminal server will do this easily, but I really don't want to buy a server license, individual OS licenses, AND access licenses!

I know there is an Ubuntu installation that allows thin client booting (LTSP), but is there any way I can set up a Linux server to do this?

I know all about running the windows software on linux via Wine or Crossover Office; what I really need help on is the multiple-GUI sessions from windows clients into an Ubuntu server.

Please help!

Aaron
Denver

---

### Post by phr0ze on 2007-05-03
I don't have an exact answer for you but I access a remote Ubuntu box using VNC. I just had to turn on remote desktop. This solution allows one connection but it shouldn't be hard to find a solution which allows multiple sessions.

---

### Post by random.brown on 2007-05-03
Thank you for the reply.

I've looked at VNC but it seems to only allow "remote control" of a single, existing user session.

I'm looking for a true, GUI, multi-user connection and login solution.

I don't mind paying a reasonable amount, but Microsoft's charges for terminal services is just lunacy.

Thanks again for the suggestion!

---

### Post by thk on 2007-05-03
You can do this with X windows, but the clients much run X. You might look into NX server as an alternative. I believe VNC can be setup to launch multiple simultaneous sessions. You may need to run multiple servers on different ports. Look around for recipes using (x)inetd to launch sessions.

---

