---
title: "How to add another Gnome or KDE session at the login screen?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Crakie on 2006-11-02
Currently I can choose a Gnome session and a KDE session at login on my Edgy install (after apt-get install kubuntu-desktop). I would like to add another KDE session, one that I can mess around with so if something goes wrong, I still have the original to work with. Is is possible to add a completely independent session? If so, how?

The reason for my question is that 
a) Gnome is a little buggy on my system: it tends to freeze at times. That's why I added the KDE session and it appears to be stable. 
b) I completely pimped my Gnome session with Beryl and kiba-dock, and I love that stuff so much I want to do the same with my KDE interface. But I want to keep a clean KDE session so I always have something to work on.

(Incidentally, Gnome being buggy has nothing to do with Beryl and Kiba, it has been freezing since the first boot).

---

### Post by Polygon on 2006-11-02
i think if you both have gnome and kde installed correctly, you should be able to just click "sessions" (it may be different according to your gdm theme) and then select kde or gnome for your login session, and then just login normally.

im not sure how well this would work out, you might want to just log out of your gnome session before your kde session if you encounter problems running gnome and kde at the same time in different sessions (it might also prevent your comp from lagging from running two WM's at the same time)

---

### Post by bsussman on 2006-11-02
In kde, kmenu, switch user.  in gnome, system -> quit -> switch user

---

### Post by raul_ on 2006-11-02
I don't think he wants to switch from gnome to KDE. I think he wants to have 2 gnome sessions and 2 Kde sessions. Maybe if u have 2 users? one to mess around and another to work

---

### Post by Crakie on 2006-11-02
You misunderstood. I can login just fine in either Gnome or KDE. What I want is ANOTHER KDE session to choose from, let's call it KDE #2. 

When I create KDE #2, it could be the same as the current KDE session (let's call that one KDE #1). When I start messing around with KDE #2, I don't want the changes to be implemented in KDE #1.

So at login I want to able to choose from:

1) Gnome
2) KDE #1 (no (pre-)alpha software installed)
3) KDE #2 (to be added, will add Beryl and Kiba-dock and whatever other things I decide to experiment with)

---

### Post by taurus on 2006-11-02
> **Crakie said:**
> You misunderstood. I can login just fine in either Gnome or KDE. What I want is ANOTHER KDE session to choose from, let's call it KDE #2. 

When I create KDE #2, it could be the same as the current KDE session (let's call that one KDE #1). When I start messing around with KDE #2, I don't want the changes to be implemented in KDE #1.

So at login I want to able to choose from:

1) Gnome
2) KDE #1 (no (pre-)alpha software installed)
3) KDE #2 (to be added, will add Beryl and Kiba-dock and whatever other things I decide to experiment with)
Why don't you create another user, test, and use that account to mess around with KDE or whatever you want.  If you screw up, delete and user and recreate it.  And if you are happy with the setup, then make the changes to your regular account...

---

### Post by xyz on 2006-11-02
Make a back up of your system so that you can restore it and then "mess around" to your heart's desire.

---

### Post by bsussman on 2006-11-02
> **Crakie said:**
> You misunderstood. I can login just fine in either Gnome or KDE. What I want is ANOTHER KDE session to choose from, let's call it KDE #2. 

When I create KDE #2, it could be the same as the current KDE session (let's call that one KDE #1). When I start messing around with KDE #2, I don't want the changes to be implemented in KDE #1.

So at login I want to able to choose from:

1) Gnome
2) KDE #1 (no (pre-)alpha software installed)
3) KDE #2 (to be added, will add Beryl and Kiba-dock and whatever other things I decide to experiment with)
My instructions accomplish only multiple 1) and 3).  Having 2 instances of kde is unusual and, I believe, tricky.  2 different users will not accomplish it. 2 different users would allow you to play with different configurable items but usually there is only one set of libs and executables for a given desktop manager.

---

### Post by Crakie on 2006-11-02
I suppose it's a decent option to create another user account. I hadn't thought of that. 

Still, I remember from Beryl/Compiz documentation people adding another session to their current user account, so they get one that does run Beryl and one that doesn't (as a backup). I just cannot find that anymore...

---

### Post by bsussman on 2006-11-02
> **Crakie said:**
> I suppose it's a decent option to create another user account. I hadn't thought of that. 

Still, I remember from Beryl/Compiz documentation people adding another session to their current user account, so they get one that does run Beryl and one that doesn't (as a backup). I just cannot find that anymore...
I do not know Beryl but what you suggest will work if beryl is optionally configurable per user.

Another reason for using a different user is that there are many things that preserve state from session to session and are tied to the user.  Having 2 instances of the same user is asking for confusion at best and probably crankiness or worse.

---

