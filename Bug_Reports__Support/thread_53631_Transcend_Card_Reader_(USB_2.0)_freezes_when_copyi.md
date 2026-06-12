---
title: "Transcend Card Reader (USB 2.0) freezes when copying a file to a CF card"
date: 2005-08-01
forum: Bug Reports / Support
---

### Post by Cockroach on 2005-08-01
I'm having problems with my card reader, I use Transcend Card reader (USB 2.0) which has CF, MMC/SD and SmartMedia slots. 

Until few days ago it worked like a charm, but now I'm the card reader freezes when I try to copy something into my CF. The output of dmesg doesn't give any indication of error, I cannot unmount the CF or kill the 'cp' process. 

The file which I try to copy is not that big, only about 10MB (Familiar Linux JFFS2 image).

Oh, another symptoms include... If I kill the Xserver after that freezing has happened and re-login, Ubuntu displays my desktop background and waits... waits some more... and says "HAL could not be initialized" (or something close to that) and no icons nor upper/lower panels appear. Only thing left is to CTRL+ALT+Backspace followed by CTRL+ALT+DEL or selecting 'Reboot' from the login screen. This leads to textmode, which does... nothing. Only way to reboot is to press reset switch. 

Is/are there some other logfile(s) (addition to dmesg) which I could try to check in order to learn more? 
Anyone else having the same problems?
Fix suggestions?

---

### Post by sjmorgan on 2005-08-02
[QUOTE=Cockroach]Fix suggestions?[/QUOTE]Start by posting to the right forum. You could also try [filing a bug](http://bugzilla.ubuntu.com/).

---

### Post by Cockroach on 2005-08-03
[QUOTE=sjmorgan]Start by posting to the right forum. You could also try [filing a bug](http://bugzilla.ubuntu.com/).[/QUOTE]
Ok, my bad. But what would be the right forum for backports related problems? Plain "Ubuntu Backports"? 
I also checked the sticky about reporting bugs, but decided first to try this forum before signing up yet another account, thus adding another password to be remembered.

---

### Post by Darrena on 2005-08-03
[QUOTE=Cockroach]Ok, my bad. But what would be the right forum for backports related problems? Plain "Ubuntu Backports"? 
I also checked the sticky about reporting bugs, but decided first to try this forum before signing up yet another account, thus adding another password to be remembered.[/QUOTE]

I don't think this has anything to do with any package that was backported or am I mistaken?  If it does please post the package itself so it can be looked into.

Thanks

---

