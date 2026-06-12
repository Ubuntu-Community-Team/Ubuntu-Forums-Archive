---
title: "Does Ubuntu have a Remote Desktop Client like XP does?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by DevilsRejection on 2005-11-22
And don't say VNC :)

I need something that works on the RDP protocol so I can access all my computers at home, and my server. I really don't want to deal with installing VNC, and I have played with it recently and it just isn't up to the satisfaction I am used to with Remote Desktop Connection.

I found an application called [Tarantella]("http://www.tarantella.com/news/releases/2004/13.html") but it isn't free. 

Does anyone know of a similar solution?

---

### Post by aysiu on 2005-11-22
So you've already tried System > Preferences > Remote Desktop, and that didn't suit your needs?

---

### Post by DevilsRejection on 2005-11-22
[QUOTE=aysiu]So you've already tried System > Preferences > Remote Desktop, and that didn't suit your needs?[/QUOTE]

Thanks, will definitly try it out, I am still downloading Ubuntu as we speak, should be another hour or so. Maybe I should stop getting ahead of myself :D 

But I have to ask you, why is it in System > Preferences ? Woulnd't it be more of a networking tool? Just a thought.

---

### Post by aysiu on 2005-11-22
I'm just taking a stab in the dark (i.e., I don't know), but I would guess that since Linux is a multi-user environment, maybe it's a preference because you can share your desktop and another user can choose not to share her desktop...?

---

### Post by gord on 2005-11-22
system -> preferences -> remote desktop is actualy just the preferences for the remote desktop

"
 users can view your desktop using this command:
 vncviewer localhost.localdomain:0
"

---

### Post by DevilsRejection on 2005-11-22
Ah ok, so what is an actual client that will let me see use my Windows Desktop over RDP?

---

### Post by tim15856 on 2005-11-22
I think you're looking for rdesktop [http://www.rdesktop.org/](http://www.rdesktop.org/)

---

### Post by storm80y on 2006-08-13
Applications > Internet > Terminal Server Client

---

### Post by slakkie on 2006-08-13
> **tim15856 said:**
> I think you're looking for rdesktop [http://www.rdesktop.org/](http://www.rdesktop.org/)

I think its in the repositories, or its included in the default install:

ii  rdesktop                               1.4.1-1.1                               RDP client for Windows NT/2000 Terminal Serv

---

