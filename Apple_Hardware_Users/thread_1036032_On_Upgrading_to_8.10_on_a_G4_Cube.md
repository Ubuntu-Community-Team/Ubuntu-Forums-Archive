---
title: "On Upgrading to 8.10 on a G4 Cube"
date: 2009-01-10
forum: Apple Hardware Users
---

### Post by avtolle on 2009-01-10
I determined to take the plunge last night to upgrade my experimental Cube to 8.10 from 8.04. As I hadn't done a "network upgrade" from one release to another for a very long time, I thought I would try this just to see how it went. Armed with a printed version of my working /etc/X11/xorg.conf file and yaboot, I checked to see that the 8.04 was totally updated, and clicked on the box at the top of the Update Manager to begin.

The first problem I had was an error message concerning a bad file during the second step of the process. Reading the message, I realized the problem involved the Canonical partner repository. Removing that, once the system was restored to its existing state, and restarting the process, it proceeded without further problem.

Upon restarting, the system booted with a message that there was a problem with the graphics and a box that offered me three options; I chose the one to use low graphics for the session. After reassuring the system that was what I wanted, and waiting for the system to reset, I reached the expected desktop which, notwithstanding what I was told, appeared normal in appearance. The system appeared to operate fine, but a bit slow.

I then edited my /etc/X11/xorg.conf file to insert the information from my prior working configuration, restarted X, and again was informed the system would be in low graphics mode, which I accepted. Again, there didn't seem to be any difference with graphics once the system went to the desktop. After reading many of the threads here, I changed the driver from ati to fbdev, and restarted X, which seemed to eliminate the low graphics message, and the system seemed to run better. As I have no need for desktop effects, this was a suitable situation. 

System Information: G4 Cube, 450 mhz processor; upgraded to 576 mb RAM; Apple Studio 15" display; ATI Rage 128 video card.

Very pleased with 8.10 so far on the experimental machine. For the first time in many releases, I have system sounds (at least some of the time), and sound playback from videos, streaming audio, and audio CDs works with no problems.

---

### Post by avtolle on 2009-01-10
I'm posting my tweaked /etc/X11/xorg.conf for review by anyone who might find it helpful.

---

### Post by vociferous666 on 2009-08-02
thank you so much for this.  ive had so many problems with my powermac g4 with the ati rage 128 pro.  all i had to do to your config was change from the apple monitor to "configured monitor" and take out all the apple monitor stuff.  it was great!!  thanks again!!

---

