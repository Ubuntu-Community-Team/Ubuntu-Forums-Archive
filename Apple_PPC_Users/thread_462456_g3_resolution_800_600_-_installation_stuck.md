---
title: "g3 resolution 800 600 - installation stuck"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by ppcubu on 2007-06-02
hi
i have a ppc g3 500 mhz and am trying to install feisty 7.04
the live cd boots fine
although the screen resolution remains at 800x600

so when i double click the 'install' icon on the desktop
the install screens open but they are not resizable and are bigger than the 800x600
the first screen( choose language ) is ok: i double click "english"
and the next screen( setting place and time ) opens
but here i get stuck because i probably have to click a button 
that is unreachable at the invisible bottom of the screen

anyone had the same problem and found a solution ?
thanks
ppcubu

---

### Post by Auria on 2007-06-02
I have no idea about your problem - however I know the alternate CD uses a command-line installer so it is very unlikely that it would have this problem, perhaps try it if no one knows

---

### Post by Lord Shank on 2007-06-04
I have the same problem with an ibook g3 600mhz using the alt install?  That and I can't even get past the time selection phase of the install.  What gives?

---

### Post by Lord Shank on 2007-06-04
Fixed!!!

Looked at an old post.

*sudo dpkg-reconfigure xerver-xorg*

Google your model for specs on the vid card.  You'll have to manually reconfigure, but it is easy.  I have a g3 600mhz, and it only took a trip to cnet to find out I have an ATI Rage Mobility 128, make sure to enter **ATI driver** and the right keyboard layouts, i.e.,  *Macintosh, do not emulate 3 button mouse*, etc and make sure that 1024x768 is checked.  Tab to get to thee <ok> 's and hit enter.  When all is done ***ctrl +alt/option +delete*** and login.

Cheers

---

### Post by Lord Shank on 2007-06-04
Also I forgot to mention.  To install and get to the good stuff, select localization, **do not hit anything on the *time zone* screen but enter**.  You can change the time zone later.  Just worry about getting Ubuntu installed and configured.  You have to be installed on the drive to have priveledges to edit xorg.conf.

---

