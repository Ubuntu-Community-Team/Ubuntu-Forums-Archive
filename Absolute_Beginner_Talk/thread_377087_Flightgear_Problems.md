---
title: "Flightgear Problems"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by wheelhorse2347 on 2007-03-05
Hello,
I'm running Ubuntu and was interested in using Flightgear.  Each time in terminal I type 'fgfs' to start flightgear I get this message.

jordan@jordan-desktop:~$ fgfs
Error reading properties: 
Failed to open file
 at /home/jordan/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
altitude         = -1.12977
sea level radius = 2.08996e+07
latitude         = 0.653236
longitude        = -2.13554
Initializing Nasal Electrical System
Failed to find a good runway for LAX

  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
altitude         = 3.54125
sea level radius = 2.08996e+07
latitude         = 0.653331
longitude        = -2.13584
  Sorry, wdot doesn't appear to be trimmable

Trim Failed

  Trim Results: 
       Angle of Attack:   7.50  wdot:  3.21e+01 Tolerance: 1e-03  Failed
              Throttle:   0.50  udot:  0.00e+00 Tolerance: 1e-03  Passed
            Pitch Trim:   0.00  qdot: -7.83e-11 Tolerance: 1e-04  Passed
  Model Author:  Unknown
  Creation Date: 2002-01-01
  Version:       $Id: c172p.xml,v 1.17 2006-03-13 15:27:14 ehofman Exp $
  Description:   Cessna C-172
altitude         = 3.54125
sea level radius = 2.08996e+07
latitude         = 0.653331
longitude        = -2.13584
freeglut  ERROR:  Function <glutSetCursor> called without first calling 'glutInit'.

I have no idea what any of this means.  Would any of you be able to help me? \

Thank you
Jordan

---

### Post by 23meg on 2007-03-05
Did you install it from the repositories?

---

### Post by ecs_pf5 on 2007-03-05
I don't have any help from a Linux perspective but, I did notice that under Windows, Flightgear throws out many similar errors in it's CMD console, whilst otherwise managing to run just fine. Possibly only one or two of the above errors are actually preventing the program from starting up.

Bear in mind I essentially installed Linux for the first time 6 hours ago, so I am no expert. But perhaps look deeper at that last line freeglut ERROR: Function <glutSetCursor> called without first calling 'glutInit'.

---

