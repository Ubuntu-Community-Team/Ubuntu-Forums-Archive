---
title: "OpenOffice 2.2 problems - want to install 2.2.1"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by celerystx on 2007-08-09
Hi,
I recently upgraded to OpenOffice 2.2 on Ubuntu Fiesty. Now I can't open documents I made before the upgrade. When I click on a .ods file a window pops up called "Filter Selection", I choose "Open Office 1.0 Spreadsheet" from the list and then it gives me an error "General Error. General input/output error."

Since I didn't have this problem until I upgraded I imagine it's this new version. Version 2.2.1 is a bugfix and I'm hoping that can solve this problem. Unfortunately, I don't know how to upgrade to 2.2.1 since 2.2 is only available in the repositories.

Does anyone know how to install OpenOffice 2.2.1? Or has anyone had the same problem and have been able to fix it?

Thanks in advance!
Barb

---

### Post by igknighted on 2007-08-09
> **celerystx said:**
> Hi,
I recently upgraded to OpenOffice 2.2 on Ubuntu Fiesty. Now I can't open documents I made before the upgrade. When I click on a .ods file a window pops up called "Filter Selection", I choose "Open Office 1.0 Spreadsheet" from the list and then it gives me an error "General Error. General input/output error."

Since I didn't have this problem until I upgraded I imagine it's this new version. Version 2.2.1 is a bugfix and I'm hoping that can solve this problem. Unfortunately, I don't know how to upgrade to 2.2.1 since 2.2 is only available in the repositories.

Does anyone know how to install OpenOffice 2.2.1? Or has anyone had the same problem and have been able to fix it?

Thanks in advance!
Barb

Try removing OO.o via apt/synaptic, then going to [www.openoffice.org](www.openoffice.org) and download the installer there.  There might be a repo to add it to Ubuntu's apt, but its easy and safe to install from the official OO.o site, and you never know when a random .deb or repo could conflict with your system.

---

### Post by Hospadar on 2007-08-09
Well you can download it manually [here]("http://download.openoffice.org/2.2.1/contribute.html?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.2.1") and install that, and then just wait for 2.2.1 to get in the repositories and then uninstall the one you intstalled manually

---

### Post by stchman on 2007-08-09
> **celerystx said:**
> Hi,
I recently upgraded to OpenOffice 2.2 on Ubuntu Fiesty. Now I can't open documents I made before the upgrade. When I click on a .ods file a window pops up called "Filter Selection", I choose "Open Office 1.0 Spreadsheet" from the list and then it gives me an error "General Error. General input/output error."

Since I didn't have this problem until I upgraded I imagine it's this new version. Version 2.2.1 is a bugfix and I'm hoping that can solve this problem. Unfortunately, I don't know how to upgrade to 2.2.1 since 2.2 is only available in the repositories.

Does anyone know how to install OpenOffice 2.2.1? Or has anyone had the same problem and have been able to fix it?

Thanks in advance!
Barb

I have a procedure to upgrade Edgy 2.0 to 2.2.  If you substitute 2.2.1 for 2.2 it should work.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

---

### Post by igknighted on 2007-08-09
> **Hospadar said:**
> Well you can download it manually [here]("http://download.openoffice.org/2.2.1/contribute.html?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.2.1") and install that, and then just wait for 2.2.1 to get in the repositories and then uninstall the one you intstalled manually

Knowing Ubuntu, 2.2.1 will never be in the repos.  They do not upgrade apps mid release (think thunderbird, gaim/pidgin, firefox, etc.).  Like I mentioned, you MIGHT get a third party repo, and chances are that would be safe to use, but the safest choice is to go with the OO.o website's version.

---

### Post by celerystx on 2007-08-09
Thanks everyone! I think I'll uninstall 2.2 and install 2.2.1 manually as suggested.

Stchman, thanks for the line by line tutorial. I think I'll give that a try.

---

