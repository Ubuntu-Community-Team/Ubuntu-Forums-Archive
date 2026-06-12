---
title: "OO2.2 v Nautilus"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2007-04-28
After "upgrading" from Edgy to Feisty,  through a clean install, I immediately encountered a major problem. I couldn't open files on my network using OpenOffice 2.2.
I couldn't open files through Nautilus and I couldn't reach the NAS through the OpenOffice file browsing utility.

I tried:

1) Uninstall and reinstalled OO2.2 through SPM.
2) Uninstall Canonical's version of 2,2 and install the OO.org version.

No improvement. Uninstalled the OO.org version and reinstalled Canonical's version.

Then went back to SPM and installed every package that reasonably had to do with Canonical's version of 2,2.

Success. Canonical's version can now access my NAS and open both MIME types (OO and MS).

But .... OO will still not open a file through Nautilus ....

What am I missing?

---

### Post by AdotB on 2007-04-28
Can you right-click and "Open With" ?  If so, open an OO file's Properties, go to the Open With tab and set it to OO.
Hope that helps.

---

### Post by fjm03 on 2007-04-28
Thank you. I've looked at so many trees this past week that I lost sight of the forest.

*.xls was  still associated with  "document viewer" on my system as a result of earlier experimentation. Returned the default association to Open Office Spreadsheet, removed "document viewer" and "image viewer" from the assoications list and I'm now back to "normal".

I'm still wondering why, any dependency so basic, was not included in the default package  from Canonical. Home networks, with dedicated file servers are becoming fairly common. I still don't know which supplementary package  restored Canonical's original omission because I downloaded so many (19) during my shotgun approach to a dependency cure.

Thanks again.

---

### Post by Michaelt74 on 2007-04-28
This is why I recommend doing a clean install instead of upgrading; for any operating system, not only Ubuntu.

---

### Post by fjm03 on 2007-04-28
It was a clean install and the "upgrade" process has been an interesting experience. Not unlike an armed bandit trying to rob someone wearing an explosive vest.

I upgraded from Edgy to Feisty because of a lapse in the Edgy repo soon after Feisty was released. I would have preferred to wait until a bit more was publicly known about the changes in Feisty but the error in the Edgy repo affected a mission critical application on my system,  the forum consensus was that the error was not going to soon be fixed and sudden expatriation was my fate.

I installed Feisty and immediately discovered compatibility problems with OO2.2 and VMware Server 1.0.2. Beryl was also a bit of a mystery because of a  little publicized gatekeeper lurking on the System menu.

The week that ensued was a bit of a standoff. As we, the victims, learned more about the exact nature of the glitches in Feisty, we were better able to challenge the Canonical team to provide solutions or at least more explanation of their changes.

Within the past 7 days, as the masses howled, the Canonical team was apparently working diligently in the background to address the mob's concerns before Canonical's best intentions blew up in their face.

A week later, many of the concerns have been addressed through SPM if you know where to look, take the correct steps in the correct order and have a bit of experience with Ubuntu. As an example, the VMware Server is now a seamless, SPM install if you first do some manual preparation with regard to basic configuration and Fesity's idiosyncrasies.

My system is now back to it's Edgy profile. OO2.2 opens both OO and MS MIME types across a network, VMware Server now operates a virtual XP machine and Beryl spins the cube. Life is good. It's great to be home but the trip was a bit unsettling for an old MS hand.

---

