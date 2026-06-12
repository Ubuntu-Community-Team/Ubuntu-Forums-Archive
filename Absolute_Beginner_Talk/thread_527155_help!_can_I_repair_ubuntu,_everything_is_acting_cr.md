---
title: "help! can I repair ubuntu, everything is acting crazy."
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by reedfamily on 2007-08-16
Don't know what's wrong with my ubuntu. I am a complete noob and can't seem to do anything to fix this. Cannot boot without the CD, cannot get to repositories from Synaptic, it just flashes open a minute then closes. Firefox is constantly freezing and causing me to force quit. 

Everytime I try any of the commands recommended on other threads for problems....I get this message from the terminal:

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


Please tell me there is some way to repair this without having to lose everything I have saved on my PC. Anyone have any advice??? ](*,)

---

### Post by oilchangeguy on 2007-08-16
> **reedfamily said:**
> Don't know what's wrong with my ubuntu. I am a complete noob and can't seem to do anything to fix this. Cannot boot without the CD, cannot get to repositories from Synaptic, it just flashes open a minute then closes. Firefox is constantly freezing and causing me to force quit. 

Everytime I try any of the commands recommended on other threads for problems....I get this message from the terminal:

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


Please tell me there is some way to repair this without having to lose everything I have saved on my PC. Anyone have any advice??? ](*,)

my advice is, to back up your data, and do a fresh install. sounds like you've been playing, where you shouldn't be. and messed up ubuntu, so start over.

---

### Post by moore.bryan on 2007-08-16
*have you tried the "rescue a broken system" choice on the live cd?*

---

### Post by irish_flu on 2007-08-16
Any chance the hard drive is full?

---

### Post by omegamike3 on 2007-08-16
sounds like the system-level files have had their permissions reset somehow. see if you can't boot into recovery mode or off of the live cd. once you get to that point, i would just backup the stuff you need an reinstall, since resetting permissions can be a real pain, since some things require certain permissions schemes.

---

### Post by reedfamily on 2007-08-16
well this is just awful. I have stuff saved on my windows 2000 through vmware, but the CD burner isn't working on win.2000 anymore :( so I can't burn that stuff onto disk and there is tons of important docs on there and a few programs. I guess it's pretty much a lost case on those files if I have to reinstall. I know my computer is no where near full. :( Is there no other options?

---

### Post by omegamike3 on 2007-08-16
> **reedfamily said:**
> well this is just awful. I have stuff saved on my windows 2000 through vmware, but the CD burner isn't working on win.2000 anymore :( so I can't burn that stuff onto disk and there is tons of important docs on there and a few programs. I guess it's pretty much a lost case on those files if I have to reinstall. I know my computer is no where near full. :( Is there no other options?

flash drives? secondary/external hdd's? network backup?

---

### Post by reedfamily on 2007-08-16
nope nothing like that...never felt like spending much money on this dinosaur of a computer. :( Prolly won't buy a flash drive or anything like that anytime soon, as with the pc acting this way, it probably won't pick up a new hardware install. <sigh> such is life when you are absolutely not a techie person.

---

### Post by diljan on 2007-08-21
I had this same problem and just fixed it.  Not sure if it will work for you but it worked for me.

Open System>Administration>Software Sources.  Get rid of any third party sources and restore defaults under the Authentication tab.  Now reload the sources list and try running synaptic again.

This solved my problem with this error and i am now able to install updates as before.

Hope it helps.

Dale.

---

