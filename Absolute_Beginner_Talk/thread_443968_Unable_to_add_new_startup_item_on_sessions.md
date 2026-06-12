---
title: "Unable to add new startup item on sessions"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by solracarevir on 2007-05-14
i have just installed beryl (at last! I upgraded to a laptop with a decent video chipset :D  )
when i go to 
System->Preferences->Sessions
and select **new  **to add "beryl-manager" to the sessions, as soon as I click the close button if I open it again the line i just added does not appear, if doesn't happens only with "beryl-manager" it happens with everything that i try to add.Does anyone have an idea of whats going on here??


thanks

---

### Post by Iokua on 2007-05-14
Does your Beryl installation have a .desktop file? It should. Try entering this into your Gnome sessions properties:

Name: Beryl
Command: /usr/share/applications/beryl-manager.desktop

If that doesn't work, try copying it manually:

sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop

---

### Post by solracarevir on 2007-05-14
that worked great for beryl, now it comes up when i login, i suppose i could use the same technique for my bluetooth file sharing app, but what could be th cause of being unable to add lines to the sessions menu?

---

### Post by Iokua on 2007-05-15
> **solracarevir said:**
> that worked great for beryl, now it comes up when i login, i suppose i could use the same technique for my bluetooth file sharing app, but what could be th cause of being unable to add lines to the sessions menu?

You had to the copy the file manually to get it to work? Or were you able to enter into the Gnome sessions manager?

---

### Post by SomethingCronic on 2007-05-15
> **solracarevir said:**
> that worked great for beryl, now it comes up when i login, i suppose i could use the same technique for my bluetooth file sharing app, but what could be th cause of being unable to add lines to the sessions menu?

I'm so sorry that I had exactly the same problem a while ago but can't remember how I fixed it. I'm pretty sure it was a permissions issue tho. Look at the hidden gnome related dirs (~/.gnome) in your home directory and ensure you have r/w access to them.

- Mike

---

### Post by Iokua on 2007-05-15
I was also thinking it may have something to do with permissions, but that would be a bit odd. I'm not on my Ubuntu machine at the moment, but solracarevir, try running:

```
sudo gnome-session-properties
```

And then try to ADD a new entry, just to see if this could be permissions related.

---

### Post by solracarevir on 2007-05-15
i had to copy the .desktop file to make it boot. When i make it to my home i will take a tool on my laptop to see if using this works
sudo gnome-session-properties

---

### Post by solracarevir on 2007-05-15
gnome-session-properties, didn't make the trick :(

---

### Post by NumberOne on 2007-05-23
This is a problem that alot of people are experiencing, including myself.  The problem is that you are not the owner of the folder, therefore not allowed to write to it.  Try this:

```
sudo chown <your username> ~/.config/autostart
```

HTH
T.

---

### Post by solracarevir on 2007-05-23
It works!!! It's alive!!! jejeje thanks a lot it make the trick

 	Code:
 	sudo chown <your username> ~/.config/autostart

---

### Post by Iokua on 2007-05-24
Good catch NumberOne!

---

### Post by khughitt on 2007-05-27
Thanks! I was having same problem for some reason, but changing the ownership fixed things. Does anyone know how the folder ended up becoming owned by root? It's strange too since this happened for only one of several users on my machine.

Has anyone filed a bug report?

---

