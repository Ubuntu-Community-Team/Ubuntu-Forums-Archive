---
title: "strange freak accident"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by buddhalover on 2006-07-27
The strangest thing happened.
Ubuntu turned into both Kubuntu and Edubuntu?!
I tried turning it into Kubuntu using Synaptic
but it has traces of Edubuntu, load screen and Education apps.
Do you know how this happened?


first i tried removing the silly games.
(leaving only the zsnes which i activated beforehand)
default games refused to be removed from the basic add/remove from applications.
So i twitched around with synaptic
to removed the games
but it tells me that it has to remove ubuntu-desktop as
well if i wanted to do that
so i thought okay... i'll add the kubuntu desktop package
to replace the ubuntu-desktop package that goes with the games...
from there it went a bit haywire
kubuntu-desktop package wanted to be installed with all these other media players and apps. i now have several... which i don't need. and strangely edubuntu packages were also installed.
hmnn...any thoughts? 
:confused:

---

### Post by PingunZ on 2006-07-27
the ubuntu-desktop package can safely be removed.
why would you install kde just for deleting a few games ???
Just stay gnome and remove the games AND the ubuntu-desktop package.

---

### Post by kigina on 2006-07-27
i had the same edubuntu problem
i installed ubuntu (breezy at the time) and i got edubuntu

---

### Post by buddhalover on 2006-07-28
It can safely be removed?
So it's used for games only?
I thought it was important
and needed to be replaced by another desktop package.

(Some clarification
I do understand that ubuntu runs on Gnome.
Kubuntu on Kde 
so i can't run application packages that depend on kde
on gnome desktop?)

Pardon my naivette. 
This edubuntu kubuntu mutant thing that this has become 
has rather confused me.:confused:

---

### Post by aysiu on 2006-07-28
From Synaptic's description: > **The Ubuntu desktop system**
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

---

### Post by buddhalover on 2006-07-29
PingunZ

the ubuntu-desktop package can safely be removed.
why would you install kde just for deleting a few games ???

(i didn't know this at the time i removed it along with the games
i made the assumption that it had to be replaced)


Just stay gnome and remove the games AND the ubuntu-desktop package.

(I am uncertain if I am still using gnome at the moment. If I decide to reformat to solve this strange problem this edukubuntu mutant package has become I will follow the step you mention here.)

Aisu

. However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

( I see it being safe to remove. But it appears that there is a recommendation to keep it. Why can I not remove the games only and not the desktop in order to avail of certain upgrade transitions keeping it installed provides? )


More details on the edukubuntu mutant: 
1)Firefox is going buggy crashing almost randomly.
2)Shutdown and Reboot icons are missing. (i use terminal to shutdown now. *newbie glee* :)
3)Boots Edubuntu. Then Log in Kubuntu. Shutdown Edubuntu again.

---

### Post by aysiu on 2006-07-29
It's really important to have only when upgrading from Breezy to Dapper or from Dapper to Edgy.

At least for the next two months, you won't need the *ubuntu-desktop* metapackage.

---

### Post by buddhalover on 2006-07-30
What would you suggest I do...
Start over? Format then reinstall?
Or would there still be a way in which I can tweak it back to normal?

---

