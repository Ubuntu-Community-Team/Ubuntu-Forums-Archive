---
title: "Fuduntu's become rolling distro - will the packages up-to-date with upstream?"
date: 2011-09-16
forum: Any Other OS
---

### Post by Oxwivi on 2011-09-16
So Fuduntu [became a rolling release distro]("http://www.webupd8.org/2011/09/fuduntu-becomes-rolling-release.html"). I am not quite familiar with the rolling release method works in terms of the packaged software - does it mean all the programs will be whatever version declared stable by the upstream projects?

---

### Post by pqwoerituytrueiwoq on 2011-09-16
if ubuntu 10.04 was a rolling release i would have vlc 1.1.x instead of 1.0.6 now
i would have firefox 6 without the need for the mozilla ppa

---

### Post by fuduntu on 2011-09-16
> **Oxwivi said:**
> So Fuduntu [became a rolling release distro]("http://www.webupd8.org/2011/09/fuduntu-becomes-rolling-release.html"). I am not quite familiar with the rolling release method works in terms of the packaged software - does it mean all the programs will be whatever version declared stable by the upstream projects?

Basically the Fuduntu team will vet packages as we always do, but we will continue to vet major packages that will roll into the distribution.  This means we do not wait for major releases of the distribution to release new versions of software.  For the packages that we support, we will try to keep up with the latest stable packages upstream as we have historically.

---

### Post by sikander3786 on 2011-09-16
Yeah like you said, it is kind of continuously updated release independent of point releases like Ubuntu 10.04, 10.10, 11.04 etc. Arch Linux is a well known rolling release already. More info:

[http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

---

### Post by Oxwivi on 2011-09-16
> **fuduntu said:**
> Basically the Fuduntu team will vet packages as we always do, but we will continue to vet major packages that will roll into the distribution.  This means we do not wait for major releases of the distribution to release new versions of software.  For the packages that we support, we will try to keep up with the latest stable packages upstream as we have historically.
So your repos will have the latest stable packages for all softwares, aye? (I'm assuming whatever software you have in your repos are the ones you support) And since you're based on Fedora, how will Fuduntu be affected by their releases?

---

### Post by fuduntu on 2011-09-16
> **Oxwivi said:**
> So your repos will have the latest stable packages for all softwares, aye? (I'm assuming whatever software you have in your repos are the ones you support) And since you're based on Fedora, how will Fuduntu be affected by their releases?

Our repos will have the latest stable packages for all software that we add to the repository, yes.  :D

We won't be effected by their releases because we are not rebasing on new Fedora releases.  When Fedora 14 becomes unsupported, we will just continue to roll until we are no longer dependent on the original 14 base.

---

### Post by Oxwivi on 2011-09-16
Thanks for replying! I've been wanting to take Fuduntu for a spin, and since it's mostly a minimal install, I'll be sure to enjoy it on my 4 GB HDD...

---

### Post by MasterNetra on 2011-09-16
> **pqwoerituytrueiwoq said:**
> if ubuntu 10.04 was a rolling release i would have vlc 1.1.x instead of 1.0.6 now
i would have firefox 5 without the need for the mozilla ppa

Your behind sir, Firefox is at 6.0.2, you may want to upgrade as some certificates have been compromised, or at the very least remove them yourself.

Here is a article that talked about it in case you missed it: [http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts](http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts)

---

### Post by kaldor on 2011-09-16
A Fedora-based rolling-release? I think I'm in love.

<3

Edit: Any plans on changing the name so that it doesn't seem like a joke?

---

### Post by fuduntu on 2011-09-16
> **kaldor said:**
> A Fedora-based rolling-release? I think I'm in love.

<3

Edit: Any plans on changing the name so that it doesn't seem like a joke?

Nope, no plans to change the name. :D

---

### Post by kaldor on 2011-09-16
So Fuduntu is going to eventually break the connection with Fedora entirely? Are you trying to maintain compatibility with Fedora or will there be possible issues later on down the road? Also, will you be working closely upstream or not?

---

### Post by fuduntu on 2011-09-16
> **kaldor said:**
> So Fuduntu is going to eventually break the connection with Fedora entirely? Are you trying to maintain compatibility with Fedora or will there be possible issues later on down the road? Also, will you be working closely upstream or not?

Yes, we will eventually sever the connection to Fedora.  We don't go out of our way to become incompatible with Fedora, but there will likely be issues down the road.  We have sent bug reports upstream (to Fedora and other distributions / upstream providers) when I see something awry and will always continue to do so.

---

### Post by kaldor on 2011-09-16
> **fuduntu said:**
> We have sent bug reports upstream (to Fedora and other distributions / upstream providers) when I see something awry and will always continue to do so.

Good; that's the way a project should operate. Though, on that note, why support GNOME 2 for as long as you can? Have you considered getting involved with GNOME to improve the "fallback session"? It's a good idea to avoid GNOME 3 right now, but I think it could be shooting yourself in the foot if you keep on using GNOME 2 for the future of your project. Just some thoughts :)

Random question: Do Fuduntu team members gather on #fuduntu much? I might pop along now and then just to see how this project works.

---

### Post by Oxwivi on 2011-09-17
Whenever I went to #fuduntu, it was empty. Even the ChanServ left for some reason.

Speaking of GNOME 2, play around with the fork Mate much?

And the Nouveau experimental 3D support with the package libgl1-mesa-dri-expermintal works great for me on Ubuntu. Any equivalent on Fuduntu? Or is it gonna be there by default like Oneiric?

---

### Post by fuduntu on 2011-09-17
> **Oxwivi said:**
> Whenever I went to #fuduntu, it was empty. Even the ChanServ left for some reason.

Speaking of GNOME 2, play around with the fork Mate much?

And the Nouveau experimental 3D support with the package libgl1-mesa-dri-expermintal works great for me on Ubuntu. Any equivalent on Fuduntu? Or is it gonna be there by default like Oneiric?

I don't hang out in #Fuduntu often enough, I've been trying to get into the habit of it again.

---

### Post by pqwoerituytrueiwoq on 2011-09-17
> **MasterNetra said:**
> Your behind sir, Firefox is at 6.0.2, you may want to upgrade as some certificates have been compromised, or at the very least remove them yourself.

Here is a article that talked about it in case you missed it: [http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts](http://www.conceivablytech.com/9157/products/iran-may-have-acquired-google-ssl-certificates-prompts-browser-security-alerts)
opps wrong nunmber version number changes too much to remember what version you have anymore, 10 days till firefox 7 :popcorn:

---

