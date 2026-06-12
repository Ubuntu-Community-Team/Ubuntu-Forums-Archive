---
title: "Software Update Available or not?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by opticyclic on 2007-05-30
I usually run Kubuntu, but haven't removed the Gnome desktop yet.
I noticed recently that when I logged into Gnome that a popup appeared saying "Software Updates Available"
Is this the Update Manager running on logon?
How do I get it to automatically start when I logon using KDE?
And why doesn't it have that behaviour by default?

---

### Post by starcraft.man on 2007-05-30
> **opticyclic said:**
> I usually run Kubuntu, but haven't removed the Gnome desktop yet.
I noticed recently that when I logged into Gnome that a popup appeared saying "Software Updates Available"
Is this the Update Manager running on logon?
How do I get it to automatically start when I logon using KDE?
And why doesn't it have that behaviour by default?

Ummm, I assume you just installed the Kubuntu package overtop Ubuntu. The answer is that the Update Manager is on by default... You can check when your logged into Kubuntu by going to System > Preferences > Sessions, its labelled "Update Notifier". The answer to your other two questions is far as I know it is on by default...

If the entry is missing, make a new entry and label it "Update Notifier" and make the command "update-notifier". Then you can reboot and it will be on from now on. Maybe there was a little problem with the packages?

---

### Post by opticyclic on 2007-05-30
hmmm not sure if System > Preferences > Sessions is a Gnome menu, but I cant find it 
Anyway, a search elsewhere came up with adept_notifier (notice the underscore and not a dash) as the update manager for KDE.
When I ran it from the Konsole I got a message saying that I had disabled it last time and would I like to have it start automatically.
I guess I probably stopped it whilst I was getting Beryl to work.

Anyhow, its sorted itself and is up and running again.

---

### Post by starcraft.man on 2007-05-30
> **opticyclic said:**
> hmmm not sure if System > Preferences > Sessions is a Gnome menu, but I cant find it 
Anyway, a search elsewhere came up with adept_notifier (notice the underscore and not a dash) as the update manager for KDE.
When I ran it from the Konsole I got a message saying that I had disabled it last time and would I like to have it start automatically.
I guess I probably stopped it whilst I was getting Beryl to work.

Anyhow, its sorted itself and is up and running again.

Right, my bad, I'm a GNOME Guy. I have to get better acquainted with KDE and Kubuntu in my VM... I guess I'll do that tonight maybe for a bit. Glad you got it fixed though, sorry I gave you directions for GNOME :p.

---

