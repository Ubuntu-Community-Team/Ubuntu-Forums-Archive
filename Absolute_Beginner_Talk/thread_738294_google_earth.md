---
title: "google earth"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by jwalters on 2008-03-28
downloaded google earth and made it to the desktop where it won't open.......anybody use the linux version?...........I'm using 7.10 gutsy

---

### Post by Calash on 2008-03-28
I use it, works just like the Windows version.

Easiest way is to use the Package manager.  I found this post with some details on how to do that.

[http://ubuntuforums.org/showthread.php?t=732131&highlight=google+earth](http://ubuntuforums.org/showthread.php?t=732131&highlight=google+earth)

---

### Post by reeseslover531 on 2008-03-28
not sure what the problem is, but maybe this will help [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Google_Earth_.28World_map_utility.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Google_Earth_.28World_map_utility.29)

---

### Post by LowSky on 2008-03-28
how did you download it?
best way to get it is to have the medibuntu repos, and just search synaptic for it to install

---

### Post by oldos2er on 2008-03-28
> **jwalters said:**
> downloaded google earth and made it to the desktop where it won't open.......anybody use the linux version?...........I'm using 7.10 gutsy

 Right click on it, choose Properties, check the box next Allow executing file as program (under Permissions tab). Close the Properties window, double-click the icon.

---

### Post by stchman on 2008-03-28
> **jwalters said:**
> downloaded google earth and made it to the desktop where it won't open.......anybody use the linux version?...........I'm using 7.10 gutsy

You must have your openGL drivers for your video card installed.

---

### Post by jwalters on 2008-03-29
downloaded and installed the latest "heron" and then downloaded google earth..........
it appears on my desktop and when I try to open it says....There is no application installed for this file type......... What application should I use? to install these sort of programs

---

### Post by adi_das on 2008-03-29
Did u install it from package manager(synaptic)?.

---

### Post by jwalters on 2008-03-29
I installed it from the google download site.........synaptic had an application in there but it must have been some special code or something . The program itself didn't download through synaptic.

---

### Post by luceerose on 2008-03-29
I'll just try installing googleearth. Give me a few minutes.

---

### Post by luceerose on 2008-03-29
That was a cinche.
Works flawlessly.
Are you sure you have 3D acceleration enabled ?

---

### Post by jwalters on 2008-03-29
how?

---

### Post by luceerose on 2008-03-29
What type of Video card do you have?

---

### Post by jwalters on 2008-03-29
I have a nvidia card that's integrated on the mother board......not the greatest I suppose.........maybe to weak to do the job?

---

### Post by luceerose on 2008-03-29
That's great. I also have onboard nvidia so I should be able to help you.

You should just be able to go to System>Administration>Hardware Drivers
tick the box (if any)
and go from there

Sorry I took so long to reply I was just trying out google earth.
I was looking at okinawa's shopping district !

---

### Post by jwalters on 2008-03-29
nothing happened.................Koza? Futenma?

There has to be some way of opening this package sitting on my desktop. GoogleEarthLin ux.bin

---

### Post by luceerose on 2008-03-29
I just searched for google earth in synaptic and installed it from there.
That's probably the safest way.
It only took me just under 3 mins to download, install & start perving at Japan !

---

### Post by WinterWeaver on 2008-03-29
Sounds to me like you're not even getting past the install step?

The bin file you download from Google is a installer.
You have to make it executable first. To do that, follow the steps mentioned earlier.
```
right click the bin file >> Properties >> Permissions (3rd tab) >> check the box: "Allow executing ..." >> OK
```

Then you just double click the icon, choose run in terminal, and the installer will start

ta,

WW

---

### Post by jwalters on 2008-03-29
yeah I marked it earlier...no go

when I search synaptic I get 'google earth-package 0.5.2 utility to automatically build a Debian package of Google earth'...............applied it, but nothing different

---

### Post by jwalters on 2008-03-29
This is what I keep getting when I try to install it from desktop.(the little install square is there)............"Couldn't display "/home/jwalters/Desktop/GoogleEarthLinux.bin". There is no application installed for this file type"

---

### Post by luceerose on 2008-03-29
With synaptic you only need 2 packages;

googleearth
googleearth-data

Once synaptic has installed it, you find it under Applications>Internet

---

### Post by jwalters on 2008-03-29
well I finally found it ...had to download more files into synaptic and there it was.

Thanks for the help................

---

