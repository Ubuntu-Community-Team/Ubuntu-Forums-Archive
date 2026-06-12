---
title: "Purpose for installation of Loop Back adapater"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by cctez on 2007-02-19
In the standard desktop installation, what is the purpose for the Loop Back adapter being installed?

Does the install use TCP and the local address to pull the necessary packages?

After installation is it safe to get rid of the loop back adapter?

Thanks,
- C

---

### Post by cctez on 2007-02-19
bump

---

### Post by Bachstelze on 2007-02-19
You don't want to get rid of the lo interface. It is used forconnections to the X server and certainly lots of other things.

---

### Post by cctez on 2007-02-19
Thanks. - C

---

### Post by n8bounds on 2007-02-19
If you came from windows, it had a loopback interface as well.  From windows ping 127.0.0.1 (thats you, thats your loopback) sometime to see what I mean.  The idea is, if you are troubleshooting networking problems, and you can't ping an external source, say, your default gateway, but you can ping the loopback address (overwhelmingly 127.0.0.1) then it at least isn't your lower level network card functions that are messed up.  ...you know, or something like that... ;)

---

### Post by cctez on 2007-02-20
> **n8bounds said:**
> If you came from windows, it had a loopback interface as well.  From windows ping 127.0.0.1 (thats you, thats your loopback) sometime to see what I mean.  The idea is, if you are troubleshooting networking problems, and you can't ping an external source, say, your default gateway, but you can ping the loopback address (overwhelmingly 127.0.0.1) then it at least isn't your lower level network card functions that are messed up.  ...you know, or something like that... ;)

Exactly, I don't have a Windows machine around at the moment so I cannot double check what I am about to say, but the MS Loopback adapter enabled (among other things) an admin to configure or test TCP on a machine without a NIC... 

Where there is deviation in spec is that MS' windows kernel doesn't use the loopback adapter to communicate with shell AFAIK...

For me, the toughest part of making this transition from MS Windows to Linux, is learning/un-learning the architecture of "How OSes Work." Because I am a software architect who has been developing systems on the MS platform for over 15 years, I have many assumptions regarding how "OSes are supposed to work." When I see applications, my mind immeadiately charts requirements, architecture, design patterns and development paths. It's humbling and refreshing to start over as a noob, but I am catching on.

:)

- C

---

