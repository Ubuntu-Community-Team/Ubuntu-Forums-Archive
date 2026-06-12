---
title: "When to aptitude, apt-get, add remove programs, synaptics, adept, etc...?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by girard on 2007-03-30
It's been about three weeks since I started reading on linux, ubuntu, the terminal, the whole opensource thing, etc...

Just this morning i installed the KDE DE for ubuntu, but when I used sudo aptitude install kubuntu-desktop it didn't work well. I ended up making it work with apt-get, although i did notice some difference between the two, which i cannot remember nor did i note. well it's working now anyway.

Articles have been telling that using aptitude is better than apt-get, particularly for installation because it removes everything when you uninstall. So is this a correct assumption: aptitude is better because it operates "deeper" into the apt system/function[?] (not sure what it's called) compared to apt-get?

could this apply:

                                                  system
Deep >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>> Surface
apt >>> aptitude>>> apt-get>>> synaptics>>> add/remove programs

please shed light.

---

### Post by hyper_ch on 2007-03-30
Basically aptitude handles meta-packages, such as kubuntu-desktop better than apt-get and aptitude will also install recommended programs while apt-get will just install the required ones.

---

### Post by girard on 2007-03-30
So should there be things to consider whether to use aptitude or apt-get, or add/remove programs or synaptics for that matter?

---

### Post by az on 2007-03-30
> **girard said:**
> So should there be things to consider whether to use aptitude or apt-get, or add/remove programs or synaptics for that matter?

Not really.

The difference between how aptitude handles the removal of dependencies and how Apt does is pretty much irrelevant to the majority of users.  It may sometimes actually remove too many packages (in my experience).  

The advantage of the add-remove tool is that it can show you packages even if the repositories are not enabled in your sources.list.

All packages are installed and removed by the same backend: dpgk.  So use whatever turns you on to install and remove packages.  It's all good.

They key thing to remember is to not mix repositories.  Ubuntu and Debian distributions are not binary-compatible with one another.  You must keep repos that are all the same distro and the same release or else you may have problems.  Just be picky about what repos you add to your software channels (repositories list).

I would guess that the reason you could not install a package with aptitude, but were successful with apt-get is that you hadn't updated your package list before trying aptitude.  The graphical tools do that for you.  On the command line, you have to do that by hand.

---

### Post by girard on 2007-03-30
> **az said:**
> Not really.

The difference between how aptitude handles the removal of dependencies and how Apt does is pretty much irrelevant to the majority of users.  It may sometimes actually remove too many packages (in my experience).  

The advantage of the add-remove tool is that it can show you packages even if the repositories are not enabled in your sources.list.

All packages are installed and removed by the same backend: dpgk.  So use whatever turns you on to install and remove packages.  It's all good.

They key thing to remember is to not mix repositories.  Ubuntu and Debian distributions are not binary-compatible with one another.  You must keep repos that are all the same distro and the same release or else you may have problems.  Just be picky about what repos you add to your software channels (repositories list).

I would guess that the reason you could not install a package with aptitude, but were successful with apt-get is that you hadn't updated your package list before trying aptitude.  The graphical tools do that for you.  On the command line, you have to do that by hand.
thanks a lot for the quick reply.

and it does not matter also whether you are logged on to KDE or Gnome? meaning using adept to remove/install something, is TOTALLY the same as using synaptics?

isn't sudo apt-get/aptitude update the same as "updating your package list"? and is it the same as clicking on the "reload" on synaptic and whatever its equivalent in adept? (i prefer synaptic as it is more organized lol)

---

### Post by girard on 2007-03-30
i was actually a click away from what i was reading last night. i guess i found the answer to my own query.

it's found here: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

but still, for the benefit of newbies like me, why and when should we opt to use aptitude or apt-get... also a matter of preference?

---

### Post by Maestro23 on 2007-03-30
> **girard said:**
> i was actually a click away from what i was reading last night. i guess i found the answer to my own query.

it's found here: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

but still, for the benefit of newbies like me, why and when should we opt to use aptitude or apt-get... also a matter of preference?

Getting ready to post this link for you.  Aptitude handles dependencies better than apt-get.

**Apt-get vs. Aptitude:** [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by az on 2007-03-30
> **girard said:**
> thanks a lot for the quick reply.

and it does not matter also whether you are logged on to KDE or Gnome? meaning using adept to remove/install something, is TOTALLY the same as using synaptics?)

That does not matter.

> **girard said:**
> 

isn't sudo apt-get/aptitude update the same as "updating your package list"? and is it the same as clicking on the "reload" on synaptic and whatever its equivalent in adept? (i prefer synaptic as it is more organized lol)

No.  Aptitude keeps a different database than apt.  Apt-get update will update the list for all apt-based frontends.  There are no aptitude frontends, since it does not seem to be built to be as good a backend as apt.

It tends to screw people up, which is why I never really mention aptitude.
> **Maestro23 said:**
> Getting ready to post this link for you.  Aptitude handles dependencies better than apt-get.


Only for the removal of packages that were installed with aptitude.  And sometimes *too* well.

---

### Post by Maestro23 on 2007-03-30
> Only for the removal of packages that were installed with aptitude. And sometimes *too* well.

Very true..:popcorn:

---

### Post by girard on 2007-03-31
aptitude removes things too well... probably because it also installs more than what would be installed using apt-get because it installs also the RECOMMENDED packages as well right?!?

i wonder what you get from installing, or not installing those RECOMMENDED packages?

just to get this cleared up already (without having to read pages and pages again)...

you cannot undo something that you did with apt-get, by using aptitude right... and the same goes for everything else? 

ex: installing via synaptic cannot be undone by apt-get or by aptitude, or by add/remove? and same goes for all the other combinations?

---

### Post by az on 2007-04-01
> **girard said:**
> aptitude removes things too well... probably because it also installs more than what would be installed using apt-get because it installs also the RECOMMENDED packages as well right?!?

i wonder what you get from installing, or not installing those RECOMMENDED packages?

That depends on the individual package.  If you use synaptic, you just need to right-click on the package and tell it to install the recommends, as well.

And with aptitude, you can dissable that, so that it does not install the recommends.

> **girard said:**
> 
just to get this cleared up already (without having to read pages and pages again)...

you cannot undo something that you did with apt-get, by using aptitude right... and the same goes for everything else? 

ex: installing via synaptic cannot be undone by apt-get or by aptitude, or by add/remove? and same goes for all the other combinations?

FALSE.  All packages are installed by dpkg.  Whether you install something using aptitude, apt, add-remove, whatever...  you can remove it by using any (other) tool you want.

---

### Post by rillip on 2007-04-01
> **girard said:**
> aptitude removes things too well... probably because it also installs more than what would be installed using apt-get because it installs also the RECOMMENDED packages as well right?!?

i wonder what you get from installing, or not installing those RECOMMENDED packages?

just to get this cleared up already (without having to read pages and pages again)...

you cannot undo something that you did with apt-get, by using aptitude right... and the same goes for everything else? 

ex: installing via synaptic cannot be undone by apt-get or by aptitude, or by add/remove? and same goes for all the other combinations?

I think you're missing the bigger picture.

Apt installs packages.  Aptitude installs packages.  Synaptic installs pacakages.  Add/remove programs installs packages.  They all remove packages as well.  You can install something with Synaptic and remove it with apt-get, and pretty much any other combination.

Here's the catch: each program might be keeping its own database, as Az mentioned.  If you see it there to remove it, you can.

Now, when you do something like sudo apt-get remove amarok, it will only remove that package.  But when you installed it, it might have added alsa-base and alsa-utils.   These are neccesary for sound in general to work, not specific to Amarok.  If they weren't there, Amarok wouldn't work, so it added them, but you could be using them for some other app. like Kaffiene, so it leaves them there unless you explicitly remove them.

Removing it from aptiutde might remove them as well (hence some of the jabs at it).  Removing it from add/remove might remove an entirely different set.

The behavior of each is different, but they all are using the same back end, so they can all acomplish the same task.

Here is what I do:

If it's a simple app I'm looking for and I don't know what I want to use, (let's take a simple example, like... a calculator), I'll start looking in add/remove.  I'll add them, and when I'm done trying, I'll remove them.

If I don't find enough variety there, I'll go to the Adept manager (belive this is most similar to Synapic, I'm in the KDE so don't have it).  There I can see not only the gnome and kde supported apps, but any that are in any of my repositories (this is where az's warning comes into play; this isn't something you can do by accident, and given the ammount of confusion over installing/removing software, I don't think you have much to worry about ;)).  

If I'm searching the net and a troubleshooting guide tells me to run something from apt-get or something of the like, I use apt-get.  I only use apt-get when I already know exactly the name of the package I want to add.

I hope that clears things up a little.  Basically, go with what works for you.  Everyone has a little different experience level and their own preferences.  Many advances users might use only apt-get and never mess with the add/remove.  Heck, I rarely mess with it because Adept gives me so many more options and I'm not an expert user.  Go with what is comfortable for you and gets the job done.

---

### Post by girard on 2007-04-09
just got back from my vacation... sorry for the late reply.

Thanks a lot to all.

---

