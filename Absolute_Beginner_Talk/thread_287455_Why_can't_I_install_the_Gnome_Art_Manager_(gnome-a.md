---
title: "Why can't I install the Gnome Art Manager (gnome-art)?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by elcasey on 2006-10-28
I'm trying like mad to install the GNOME Art Manager, yet I can't find it anywhere. The closest thing I've found is [here on MikeTech](http://www.miketech.net/gnome-art/), which tells me the project isn't even supported anymore (but it's from 2005). 

I go to Synaptic, Search, then type "gnome-art," as instructed in some places, or "gnome art" as instructed in others. Either way, a package named "gnome-art" never appears.

I've gone to the Terminal and done "sudo apt-get install gnome-art" and I get a "package not found" error.

So, in short, how in the hell do I install the GNOME Art Manager?!! I'm a theme maniac and constantly change stuff, so this is a very useful utility for people like me.

What am I doing wrong? ](*,)

---

### Post by d3v1ant_0n3 on 2006-10-28
GNOME already has a theme manager...It's in System>Preferences in Ubuntu I think. I'm not 100% on this, because I'm in KDE and can't be bothered logging out...but I think I'm right on this.

---

### Post by elcasey on 2006-10-28
I'm not simply trying to install themes. The GNOME Art Manager connects to art.gnome.org and lets you browse wallpapers, themes, etc. from the site. Theme manager is a different application.

I may, however, end up installing Kubuntu Edgy and calling it a day. I've played around with Ubuntu a good bit via LiveCD, but I just installed it on my Toshiba laptop three days ago. I haven't had any trouble with anything else in Ubuntu, though.

---

### Post by d3v1ant_0n3 on 2006-10-28
ah, with you now. Although if the prog isn't supported/in  development anymore, it might just not work. I know that's a useless answer, sorry.

From my opinion, Kubuntu gives you more eyecandy based theming options. I find the panels better to deal with (and they don't have the annoying handles). I much prefer the theme manager in KDE also. 

On the flipside, GNOME can give a much 'cleaner' look than KDE, many people find it cluttered.

I installed Ubuntu dapper, upgraded to edgy and then installed the kubuntu-desktop package-Allows me to play with KDE and GNOME, depending on my mood. I'm favouring KDE at the moment tho.

And don't get me started on theming- I generally change my complete desktop at least once a week (check out the gallery lol)-I've made a nice Halloween theme and I'm struggling to keep it on til halloween.

---

### Post by Mimsy on 2006-10-28
> **d3v1ant_0n3 said:**
> ah, with you now. Although if the prog isn't supported/in  development anymore, it might just not work. I know that's a useless answer, sorry.


I installed it a few days ago, so it's there.

Elcasey, have you enabled all the repositories in Synaptic? go to Preferences -> Repositories and make sure they're all checked. You need to reload the packages list if you add anything, then search for gnome-art again. (I don't know which repository it's in, or I'd be more specific.)

It should be there. This is weird.

/Mimsy

---

### Post by elcasey on 2006-10-28
Mimsy, **thank you**. I had to enable all of the "LTS" groups of binaries and just for "fun" I enabled the Source groups as well. I'm sure there's a reason, but I wonder why my copy (I used the install CD that came with an Ubuntu book) had them off by default?

Anyway, it finally showed up and is currently installing. Deviant One, I appreciate your help as well. Maybe now I'll be able to install the kde packages (tried that earlier, too, to no avail).

Thanks again, both of you!

---

### Post by Midway on 2006-10-28
I looked for it too in Edgy but didn't see it.  I noticed all the repos except the sources were enabled so I just enabled the sources and now it shows up. So thanks from me too :)

---

### Post by elcasey on 2006-10-29
> **Midway said:**
> I looked for it too in Edgy but didn't see it.

I should've mentioned I'm running Dapper.

---

### Post by Mimsy on 2006-10-29
Awesome. :) Glad to hear it's working now.

/Mimsy

---

