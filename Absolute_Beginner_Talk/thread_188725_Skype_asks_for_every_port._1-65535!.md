---
title: "Skype asks for every port. 1-65535!"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by brallan on 2006-06-04
Get this! In the help files for skype it says that when you're behind a router:
> Ideally, outgoing TCP connections to all ports (1..65535) should be opened. This option results in Skype working most reliably. This is only necessary for your Skype to be able to connect to the Skype network and will not make your network any less secure.
Can anyone tell me if that's true, I could swear i caught a whiff of bovine fecal matter.

---

### Post by frodon on 2006-06-05
I don't think so because i filter my outgoing traffic and i don't allow traffic to such a huge range of ports and however skype works, it's quite weird.

---

### Post by mat1t on 2006-06-05
It's the way it uses Peer to Peer.

Skype will randomly choose a port to accept incoming connections on. However, You can set this in the options and then it will only use the one you have set. This can improve your skype experience, as you will not have to go through relays to talk to anyone else. The downside is that there is a potential for you to become a relay for other people.

I have it set up this way, and have opened a port on my NAT router so that I never have to go through relays.

edit: didn't read the original post properly. Skype does use a random high-end port, but it only needs a few. If it can't get through on one port, it will try another. Unless you're explicitly blocking them though, it is allowed (as it's an outbound request, not an inbound connection)

---

