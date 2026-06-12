---
title: "PSC 1610 Prints Blank Pages"
date: 2008-03-28
forum: Apple PPC Users
---

### Post by joshtheiss on 2008-03-28
Hey all,

I've been thinking of switching to Ubuntu Linux, so i've had it installed onto an external drive for awhile now.  I'm fairly happy with it, and am tempted to install it onto the internal drive, but i can't get my printer set up!  I know it works, because it prints perfectly from my Apple OS X partition. It sets up very quickly in Ubuntu, and all seems well, but when i go to print anything, the printer head moves and it seems like it's printing, but it spits out a blank page.  I don't think it's a driver issue, as i can scan in Ubuntu using the same printer.  

I'm currently running an iBook G4 and trying to print to an HP PSC 1610.  I've tried uninstalling, reinstalling, reinstalling using cups, the gnome thing, and the HP installer.  I've tried messing with the print resolution (600dpi, colour, black and colour, etc).  Is printing in Ubuntu really supposed to be this hard?  (of course not, but i'm frustrated at the moment :(... sorry)

Any help on the matter would be appreciated.  Thanks in advance,

josh

---

### Post by stream303 on 2008-03-28
I'm no printer expert by any means, but with my HP, even though it seemed to be automatically detected, I had to add another printer, and try it again manually.

Are there any updates in the backports to the printer drivers?  You may want to enable the backports repository in software sources, and see if it will pick up any updates...

Sorry I couldn't be more helpful, just stabs in the dark here..

---

### Post by joshtheiss on 2008-03-28
Hey, thanks for the quick response!

I enabled the backports, downloaded everything that said "HP" (of course, making sure that it was actually related w/ hewlett packard), and then set up the printer again, but no luck... 

Any other ideas?  Or any other takers on my problem?  Seems like it's a common problem that doesn't have a lot of solutions...

---

### Post by stream303 on 2008-04-01
I just thought of something that happened to me awhile back - are you set for the right paper dimensions, ie A4 vs 8.5x11 etc?

---

### Post by joshtheiss on 2008-04-01
Thanks once again for your reply.

Actually though, i got frustrated with not being able to print, and opted to try Fedora.  Seems like they have better support for PPC, and everything i need worked within a day, so i'll go with them for the moment.

Thanks once again for your time though.  It was very much appreciated!

---

### Post by lark5000 on 2008-06-12
It took me 10 minutes to figure this one out.

I could only print blank pages from the 'Text Editor' aka 'gedit'.
So what I did was go to the tab marked 'Advanced' from the 'Print...' option and selected 'draft grayscale (black catridge)' under General/Printout Mode and '300 dpi, grayscale, black cartridge' under Printout Mod/Resolution/Quality/Ink Type/Media Type.  Don't leave it with the default options ie normal, color cartidge and controlled by printout mode, respectively.  I started printing something besides blank pages!  Hope this helps... its at least a start...

---

