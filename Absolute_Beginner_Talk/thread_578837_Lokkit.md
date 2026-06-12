---
title: "Lokkit?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-17
Does anyone know the story on Lokkit?

The homepage is dead, there is no sourceforge page. We're on version 0.50.22-7.1 for Feisty and Gutsy, but I'm noticing screenshots of 0.50 show a 2001 copyright.

That's not terribly encouraging for a security item. Has Lokkit gone the way of the Norwegian Blue?

[Before helpful folk chime in about Firestarter and Guarddog, these don't work for me I'm afraid. I've been at this two weeks now - they /really/ don't work. Firestarter inexplicably blocks my LAN, and no combination of pinning ports will make Guarddog let NFS work reliably. But if there's some other iptable gui that handles basics like a trusted LAN and file sharing, feel free to mention it.]

---

### Post by jingo811 on 2007-10-17
non-GUI application that most Linux users use for bad ip blocking.

**Moblock**
[http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

---

### Post by julian67 on 2007-10-17
[Easy Firewall Generator for IPTables]("http://easyfwgen.morizot.net/gen/")

---

### Post by ofb on 2007-10-18
> **jingo811 said:**
> [http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

A 78 page thread of troubles, and there's notification on the MoBlock project page that the package "still" fails to work with Gusty and must be compiled... You know, thanks but I don't think I should try that.

Perhaps I should have been specific that I have not enjoyed the frustrations of the last two weeks. What I'm looking for is something that will work now, so I can get back to the projects that I do enjoy being frustrated by. ;)

> **julian67 said:**
> [Easy Firewall Generator for IPTables]("http://easyfwgen.morizot.net/gen/")

Good idea, but unfortunately it doesn't fit. My situation is two cards but not a gateway. The LAN is totally trusted and totally separated from internet traffic.

Firestater clearly should do that, but doesn't for myself and a few other unhappy souls. Guarddog simply doesn't do trusted connections, and the rather byzantine handstands necessary for NFS are not having an effect here. 

Possibly because that's a bit of a moving target? All the HowTo hacks are spread across different distros and kernels and versions of Guarddog. Once you search you find it's been a problem for years. The most recent HowTo is pinning ports that the current Guarddog already handles as random. There needs to be a fresh review of NFS in Guarddog, or more properly, it should be documented by the Guarddog developers.

So, what else have we got? Let's go ahead and have a little thread of available options. I can tell you from my reading that I won't be the only person this'll help if cracked. There's a lot of unsolved threads on this.

---

### Post by jingo811 on 2007-10-18
> **ofb said:**
> A 78 page thread of troubles, and there's notification on the MoBlock project page that the package "still" fails to work with Gusty and must be compiled... You know, thanks but I don't think I should try that.

Perhaps I should have been specific that I have not enjoyed the frustrations of the last two weeks. What I'm looking for is something that will work now, so I can get back to the projects that I do enjoy being frustrated by. ;)

.....
.....


Stick with Feisty 7.04 and you're only 4-5 commands from running Moblock and clearing your headaches.  Besides Gutsy 7.10 came out today Oct 18th of course things won't be 100% stable like on Feisty which has been tested by the public sine April 2007.
Those 78 pages of troubles mostly come from power users wanting to do stuff that ordinary ppl will never have to touch.
Just knowing how to start and stop Moblock will get you far.

---

