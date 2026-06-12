---
title: "octaga player problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by jalirious on 2007-03-11
'lo kids. I'm trying to get Octaga player working on my (6.06) account. All I want is a program to view the .wrl files.

When I login as root it works alright, but when I'm in my user account (after linking the executable to PATH in my login) I only get the launch box, nothing else.

If anyone can help me with this, or alternatively link me to an installation guide to a decent .wrl viewer that'd be great.

Ta, ben.

---

### Post by jalirious on 2007-03-11
jibbed it and went for freewrl - job done. By the way, as no-one's linked anything with geant I got it working on dapper with; 

[http://geant4.slac.stanford.edu/tutorial/installation/Geant4.8.2/Linux/Geant4_8_2_Linux_Installation.htm](http://geant4.slac.stanford.edu/tutorial/installation/Geant4.8.2/Linux/Geant4_8_2_Linux_Installation.htm)

There's a few libraries you might need as extra, but the thing that stumped me for a bit was in RandGauss.h - need to change 'RandGauss' to 'CLHEP:: RandGauss'

---

