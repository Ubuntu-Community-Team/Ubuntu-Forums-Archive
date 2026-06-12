---
title: "Installing KDE On Gnome With CD"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by mitchmaster on 2006-09-17
Hi my name is Mitch and I have tested out Kubuntu, and absolutely love the KDE Interface compared to the old GNOME one I have had for a while. I have a Kubuntu lived cd and was wondering whether it was possible to install KDE onto my Ubuntu (gnome) that I already have, through the cd.


Can anyone please help me?
Thanks! I love you UBUNTU!:KS

---

### Post by AndyCooll on 2006-09-17
The short answer to your question is yes.

I use GNOME, however I always install the KDE desktop too. To do this I do a normal install. Then I go to the command line and type:

```
sudo apt-get install kubuntu-desktop
```

This will then install the KDE desktop. Next, you logout. Then choose "sessions" on the login screen and select "KDE". Now enter your name and password and when you login you'll have a Kubuntu desktop.

:cool:

---

### Post by mitchmaster on 2006-09-17
Sorry... That doesnt seem to work? Is there something else that I have to do? It says it cannot find the package called "kubuntu-desktop"

Mitchhhhh

---

### Post by comppsyco on 2006-09-17
Does it need to be off the CD? it would be easier off the repos.

---

### Post by bulldog on 2006-09-17
> **mitchmaster said:**
> Sorry... That doesnt seem to work? Is there something else that I have to do? It says it cannot find the package called "kubuntu-desktop"

Mitchhhhh

Open synaptic [administration--synaptic] and go to configuration--packages and click your cd so it's a repositorie.

then do again 

sudo aptitude update
sudo aptitude install kubuntu-desktop

---

### Post by aysiu on 2006-09-17
Yikes!

First of all, do **not** use *apt-get* to install a desktop environment. Makes it very hard to remove later, should you ever wish to do so.

Full installation guide is here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

And, no, you cannot install it off the **Desktop CD**. The only way to add KDE to Gnome is off the internet repositories or off the **Alternate CD**.

---

### Post by bulldog on 2006-09-17
And, no, you cannot install it off the Desktop CD. The only way to add KDE to Gnome is off the internet repositories or off the Alternate CD.

Not even the Kubuntu cd??

Never too old to learn,didn't know that.

Thanks for the info.

---

### Post by aysiu on 2006-09-17
Yes, that principle applies to any of the Desktop CDs (Kubuntu, Xubuntu, Ubuntu).

The Desktop CDs have only *ndiswrapper* and *build-essential* in their repositories.

The Alternate CDs have the full desktop environment in their repositories.

---

### Post by mitchmaster on 2006-09-17
> **aysiu said:**
> Yes, that principle applies to any of the Desktop CDs (Kubuntu, Xubuntu, Ubuntu).

The Desktop CDs have only *ndiswrapper* and *build-essential* in their repositories.

The Alternate CDs have the full desktop environment in their repositories.


Wait... now I'm confused...
Is the desktop cd the ones that they mail to you through shipit? Is there some way to tell?

...
Thanks for everyone trying to help me out:) You can contact me at [email]mitch__master@hotmail.com[/email] (email or through msn) or even through here; I am checking it quite often hoping someone can help me out (damn those rainy days:wink:)

Anyways... Thanks...

Mitch

---

### Post by aysiu on 2006-09-17
The Desktop CDs are live CDs that can also install. They are full graphical, point-and-click environments.

See how it looks here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The Alternate CDs are install-only with different install options (OEM, barebones, etc.). They're graphical text-based environments.

See how it looks here: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by mitchmaster on 2006-09-17
> **aysiu said:**
> The Desktop CDs are live CDs that can also install. They are full graphical, point-and-click environments.

See how it looks here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The Alternate CDs are install-only with different install options (OEM, barebones, etc.). They're graphical text-based environments.

See how it looks here: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Okay...
So what you're saying is that I cannot add KDE unless I have an internet connection, and that the cds that i got through 'shipit' do not work?

Please just explain in plain words >_<


Mitch

---

### Post by aysiu on 2006-09-17
In plain words, the CDs you got through ShipIt will allow you to do one of three things:

1. Run a live session of Kubuntu
2. Install Kubuntu *over* your old installation, erasing everything that was there before
3. Install *ndiswrapper* or *build-essential*

If you want to **add** Kubuntu to your current Ubuntu installation, you have two options:

1. Somehow obtain an Alternate CD and then do ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

2. Download and install Kubuntu over the internet with these commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

**Bottom Line**: You need to use the internet or the Alternate CD.

---

### Post by terabite on 2007-01-10
So.. i can install KDE as a SECOND desktop environment if i download ALTERNATE CD of Kubuntu and adding it in repository list of Synaptic? Right?:-k

---

### Post by aysiu on 2007-01-10
> **terabite said:**
> So.. i can install KDE as a SECOND desktop environment if i download ALTERNATE CD of Kubuntu and adding it in repository list of Synaptic? Right?:-k
Yes.

---

