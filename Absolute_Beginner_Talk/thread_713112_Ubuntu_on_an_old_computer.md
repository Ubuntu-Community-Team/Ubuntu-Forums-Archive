---
title: "Ubuntu on an old computer"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Le 3eme Oeil on 2008-03-02
I have this old HP computer that has a 38.1Gb HDD, 128MB of RAM and a Pentium 3 (i don't know how many Mhz it is.) 

I was wondering if i could install ubuntu onto it with those specs, or should i go for Xubuntu or some other kind of linux.

:)

---

### Post by jerksire on 2008-03-02
Ubuntu and family runs good on 256MB and above. The first time I  tried using  it with the Live Ubuntu CD with a 128MB of ram it did'nt work so I'd recommend first to try and get a 256MB of Ram .

---

### Post by freebeer on 2008-03-02
Ubuntu will install on that machine, but your memory is a little light for Gnome (or so the general consensus goes from what I have read).  I think Xubuntu (which uses a lighter desktop manager) is probably a better choice.  Or run out and get a bit more memory (256M is ok for Gnome, but 512 would be better). ;)

---

### Post by Zeroangel on 2008-03-02
Whoa! Most definitely not. Ubuntu has nearly the same performance requirements as Windows XP. In fact the liveCD will not even run at all unless you already have a linux swap partition set up -- and if you can install using the text installer, it will positively CRAWL (just as it would with Windows XP installed).

Go with a lighter weight distro like xubuntu. Or even a non *buntu distro like puppy which is specially designed for older computers.

The last time I checked, Ubuntu needs 256MB to run at an acceptable clip.

Cheers.

---

### Post by wolfen69 on 2008-03-02
perhaps Fluxbuntu will work for you.

---

### Post by linuxjerk on 2008-03-02
Does that machine have a ps1 or ps2 mouse?

If you have a ps1 mouse you will have real problems.

I have personal experience with this.

---

### Post by mike.desmo on 2008-03-02
I would agree about the ram problem, would be far better if the computer had more memory. As far as xubuntu, install it and you will be quite happy. It uses the XFCE desktop, which is really light weight, quite fast with limited resources. I am running xubuntu on two laptops, one an old ibm with a 600 mhz processor and a CF-72 Toughbook with 850 mhz processor, 320 megs of ram on both.

---

### Post by frankos44 on 2008-03-02
I have Ubuntu running well on a Pentium 2 here. Yes it is is considerable slower than my Pentium 4 but it is usable. 256Mb ram is a must and see if you can find a reasonable graphics card for it. A more modern hard disk will improve performance too.

Another thing is remove Open office in favor of Gnome office will make the machine a bit more lightweight.

$ sudo apt get remove openoffice*
$ sudo apt-get install gnome-office

---

### Post by Zeroangel on 2008-03-02
Oh, and no matter which distro you use. I suggest:

Sylpheed (email)
Kazehakase (tabbed mozilla-based web browser -- uses only 6MB of RAM at startup!)

---

### Post by frankos44 on 2008-03-03
> **Zeroangel said:**
> Oh, and no matter which distro you use. I suggest:

Sylpheed (email)
Kazehakase (tabbed mozilla-based web browser -- uses only 6MB of RAM at startup!)

Excellent program's, I would consider moving from Evolution but cant find a way to convert my address book to csv.

The bowser is good too but Mozilla 3 is much faster on Hardy alpha 5 and I depend on the HTML validator Plugin.

---

### Post by FakeOutdoorsman on 2008-03-03
> **Le 3eme Oeil said:**
> I have this old HP computer that has a 38.1Gb HDD, 128MB of RAM and a Pentium 3 (i don't know how many Mhz it is.) 

I was wondering if i could install ubuntu onto it with those specs, or should i go for Xubuntu or some other kind of linux.

:)

Of course you can install Ubuntu on that machine.  I've installed it on an old Panasonic Toughbook (Pentium II/266, 4GB HD, can't remember how much RAM).  It was slow, but usable.  The first thing I recommend is looking up the model of your HP computer on the forums to find out if others had any trouble with it.  You will probably need the alternate install disc, because of your RAM size.  I didn't do a normal Ubuntu install.  I did a command-line install to keep things light and then manually installed things from there. I ended up using Openbox instead of Gnome/GDM (Ubuntu uses Gnome as the windows manager and Xubuntu uses XFCE). Xubuntu might be a little quicker than Ubuntu, but some people say that Xubuntu has been bulking up and slowing down a bit. Don't be afraid to try a command-line install and customizing a bit, especially if you even have just a little Linux experience. Also, you could try some distros suited for older machines.  Check these out:

[Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") [Ubuntu Wiki]
[Urukrama’s  Openbox guide]("http://urukrama.wordpress.com/openbox-guide/")
[Lightweight Gnome]("http://ubuntuforums.org/showthread.php?t=298835") [Ubuntu Forums]
[Looking for a lightweight Gnome alternative]("http://ubuntuforums.org/showthread.php?t=282452") [Ubuntu Forums]
[Is it worth loading Ubuntu on an old PC?]("http://ubuntuforums.org/showthread.php?t=617666") [Ubuntu Forums]

Distros: Arch Linux, MEPIS Antix, Wolvix Cub.

---

### Post by OrangeCrate on 2008-03-03
Put as much RAM in it as it can hold - it's cheap anyway, then install Ubuntu. I've fixed up several old boxes over the past couple of years, and donated them to our high school.

The last one was an HP 512n. It had 128 meg of ram. I swapped it out for two sticks of 256 ( max of 512), and intalled Gutsy. Runs like a champ.

Here's a good place to buy memory, they're easy to work with, service is excellent, and if it doesn't work, returns are a snap.

[http://www.memorygiant.com/](http://www.memorygiant.com/)

---

### Post by linfidel on 2008-03-03
> **OrangeCrate said:**
> Put as much RAM in it as it can hold - it's cheap anyway, then install Ubuntu. I've fixed up several old boxes over the past couple of years, and donated them to our high school.

The last one was an HP 512n. It had 128 meg of ram. I swapped it out for two sticks of 256 ( max of 512), and intalled Gutsy. Runs like a champ.

Here's a good place to buy memory, they're easy to work with, service is excellent, and if it doesn't work, returns are a snap.

[http://www.memorygiant.com/](http://www.memorygiant.com/)Old memory is never cheap.  I'd bet 128 meg of ram for that computer, if you can get it, is lots more than 4GB would be of DDR2.

Depending on his needs, it would be a waste of money.  I believe a basic Ubuntu will run, Xubuntu definitely, using the alternate install disc.

Feisty spec'd 64 mb minimum for Ubuntu, 48 mb for xubuntu.  Of course, they recommended 192 mb as better, but it really depends on what you need it for.

---

### Post by ugm6hr on 2008-03-03
If you want a decent Ubuntu installation, try the advice here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

You can then add the programs you want - you will probably want a file manager (e.g. thunar or ROX) in addition to the programs listed.

---

