---
title: "Adding Devices to xcdroast"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2006-05-19
I am trying to configure xcdroast so I can burn cds and copy them etc. It doesn't recognize my cd-drive I get a pop-up that says:

"No CD-writer or CD-ROM device detected.
For ATAPI/IDE devices under Linux you have to enable
SCSI-Emulation in the kernel in order to activate them."

Any ideas on how to proceed?

---

### Post by richbarna on 2006-05-19
Have you tried K3B ? It seems to be the burner of choice for CD's and DVD's.
Also when I just looked at the xcdroast setup, it says that it doesn't like ATAPI DVD devices and told me that I can only burn CD's unless I install SuperDVD or something.
Your choice, but I would recommend K3b.

---

### Post by TheFourElements on 2006-05-19
Will k3b auto-detect my hardware?

---

### Post by richbarna on 2006-05-19
It did with mine, I've got ATAPI drives as well, one is a cd/dvd combi which normally cause problems but works great.
Try it and post back, any problems and i'll check out my settings.
Have you got the usual codecs, cdrdao etc installed?
Automatix will switch on DMA support on cd and dvd drives.

---

### Post by TheFourElements on 2006-05-19
K3B worked like a charm. Plus, it's a whole lot better looking than xcdroast. Thank you.

---

### Post by richbarna on 2006-05-19
I prefer it too, glad it worked for you :D
Happy Burning.

---

### Post by Coburn on 2006-12-30
OK, you guys.

I'm glad you're happy with K3B.  I want to get xcdroast to work.

Site FAQ says to configure /etc/modules.conf  But not on Ubuntu, right, b/c no such file?

Got to get the drive recognized as a pseudo-SCSI device so xcdroast can read it.

Um, sounds like sloppy developing to me, but </rant>

So, how do I do that the EZ way?

Thanks

---

### Post by Coburn on 2007-01-05
Update:  I broke down and got k3b.  Didn't want to mess w/ the KDE stuff, but hey, k3b is OK.  It is a good frontend for pretty much all of the options you see in command-line.
:cool:

---

### Post by bayvista on 2007-08-14
Thanks guys. After wrestling with Windows and several Ubuntu utilities which didn't work, I checked here, installed K3B and it worked first time.

However...has anyone got X-CD-Roast to work with Ubuntu? If so, please tell the world.

Thanks

David

---

