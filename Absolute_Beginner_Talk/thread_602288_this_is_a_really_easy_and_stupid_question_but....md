---
title: "this is a really easy and stupid question but..."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-11-04
when i go into the Konsole (i'm using Kumbuntu) i type "su" <eneter> and it asks for my password (although the cursor seems frozen) i enter my password and it says "su: Authentication failure"
if im looking to run commands that need root - is this not the way to do it ??

---

### Post by jpittack on 2007-11-04
sudo runs root

and I have a feeling you typed your password in wrong.  the cursor won't move.  it is still accepting what you type.  Call it a security feature.

---

### Post by TeaSwigger on 2007-11-04
As jpittack said, Kubuntu (and the other ubuntus and some other distros as well) use sudo instead of a super-user account per se. There's a lot to the whys and wherefores of su / super-user vs sudo, but for the moment keep this in mind:

- Use sudo for commands as root, such as in Konsole.

- Use kdesu for running GUI apps as root.

In various instructions you may see references to using gksu. That is the Gnome / Ubuntu / Xubuntu version of KDE / Kubuntu's kdesu. Where they say gksu you should simply put kdesu instead.

So again: root commands are sudo, running GUI apps as root in Kubuntu are kdesu. Jot that down ;)

You'll get the hang of it :)

---

### Post by lupgop on 2007-11-04
thanks - one thing more - i installed firefox as konqueror wasnt working to well for me as a web browser.
i put it in the /usr/share/apps/  , i can run from there but how do i add to the applications menu ???

---

