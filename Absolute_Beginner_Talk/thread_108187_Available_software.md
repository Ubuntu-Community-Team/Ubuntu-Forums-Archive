---
title: "Available software"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by brummieman on 2005-12-25
A few newbie questions......

1. Is there a good DVD  and CD ripper for Ubuntu ?

2. Is there a good video editor ?

I am not afraid of the CLI, we are old friends from my DOS days, however, I am daunted by compiling software for the platform.....so a few questions :

3. what is the best guide to compiling software for Ubuntu.

4. Can any Linux source (e.g. a red hat package) be recompiled to work on Ubuntu or is that like getting Mac software to run on a X86 ?

5. I have an Nvidia 6800 graphics card, nice and fast, however, though Nvidia do Linux drivers for it, I can't find where I can configure the X-server in the same way i could in Mandrake to choose my hardware (currently graphics are very slow on my PC on Ubuntu)

Sorry for the long list.....but just starting the climb up the learning curve and it would be nice to get a leg up ;)

---

### Post by Perfect Storm on 2005-12-25
1. DVD::Rip

2. Kino

3. Depends what you want to compile. It's more like personal preference IMO. Further more it's always a good Idea to read what the developer(s) says on their page(s) and check the Readme file.

4. You can Alien a rpm. to .deb but there's no guarentee it works.

5. Isn't the same as Mandriva?

---

### Post by brummieman on 2005-12-25
Thanks for the answers....

yes Mandriva is what Mandrake is called now....but with that and Suse, you seemed to have more access to the X-server configuration so you could manually choose the drivers for your hardware...how can you do that in Ubuntu ?

and finally...showing my ignorance...what is alien an RPM ?  LOL :rolleyes:

---

### Post by mcduck on 2005-12-25
[QUOTE=brummieman]
and finally...showing my ignorance...what is alien an RPM ?  LOL :rolleyes:[/QUOTE]Install aprogram called 'alien' and then run 'alien yourpackage.rpm' and it will create yourpackage.deb. Then you can install it with 'sudo dpkg -i yourpackage.deb', and if you have any luck it will work :)

Your best bet with programs is still using apt-get, or .deb packages if you can't find something from Ubuntu repositories.

---

