---
title: "Updating Evolution, Gnome, Kernal without Upgrading to Edgy?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2006-10-30
My appologies if this question has been asked before, my initial search through the forums didn't turn anything up.

My question is, can I get all the fancy updates that normally come with the installation of Edgy without actually installing Edgy and sticking with Dapper Drake?  

(Last time my Edgy installation went a little sour...)

I would love to get:

Evolution Update
GNOME 2.16
Latest Kernal
Suspend Option in Log Out Dialog
OpenOffice 2.0.4
New Init System, Upstart
Rounded Corners

Is this possible? :confused: What could I get updated, and what wouldn't work?

---

### Post by dmizer on 2006-10-30
well, you can use the newest gnome, and the newest kernel, and the latest evolution in ubuntu ... but ... you'll have to compile everything yourself, and from then on, you would be requred to manually update these every time the next release came out. (wouldn't suggest this)

you should be able to enable the suspend option on logout without doing any of these updates ... don't know where you might find that though (i've done it once a while back and i couldn't find it again quickly).

rounded courners can be found by changing your theme preferences in system > preferences > theme

---

### Post by vixenk on 2006-10-30
It should be possible to update Gnome, Evolution, and OpenOffice. I'm not sure about the rest... you can try it, but it would be a bit more risky. Just add the Edgy repositories to /etc/apt/sources.list and mark only the packages you want to upgrade in Synaptic (I'm pretty sure Adept would not be proper for this... you can get to Synaptic by clicking on the "Advanced" button in "Add/Remove..." under "Applications"). Whenever the dialogue asks you if you want to replace any particular file, always answer NO. Whenever you finish, make sure to remove or disable the Edgy repositories in your sources.list so you don't accidentally forget about them and upgrade all your installed packages one day. ;)

I can't guarantee that this will work, as I've never tried it in Ubuntu before, but I have done it in previous distros without any major issues.

---

### Post by SendDerek on 2006-10-31
Excellent! 

Thanks very much you guys. I appreciate it.  

I guess I won't be doing it that way then.  Everything is working fine enough.  And come to think of it, the "quicker startup" wasn't that much "quicker". lol.

I got the rounded corners with the outdoor theme. Thanks again!

---

