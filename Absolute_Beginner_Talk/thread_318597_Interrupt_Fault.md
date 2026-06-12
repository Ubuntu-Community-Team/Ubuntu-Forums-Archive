---
title: "Interrupt Fault"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Ram97 on 2006-12-14
On boot I get a continuous Unknown interrupt or fault at EIP 00010006 00000060 c041d20b which prevents Ubuntu 6.10 from booting. I can get booted up using the generic (recovery mode) on the initial menu but am unable to figure out what is causing the error or what the error code actually means. I am assuming that a previous patch may have caused it since the error started appearing after a required restart. I even reinstalled the OS to see if it would help and it did the same thing after some patches are installed. I am just not able to figure out which one caused it. _Does anyone out there know the exact explanation for the listed error code or a way to fix it so that I can boot normally?_ I have already tried checking all my programs for updated patches and associated packages (installed versus available) patches and ran the latest updates. Any help will be appreciated. Thanks! ](*,)

---

### Post by purplearcanist on 2006-12-14
What type of computer do you have?  And what are the hard drives (model/partition)?
This may help us understand the problem.

I would suggest a reinstallation (since that temporarily fixes the problem), and then, install one patch at a time, taking notes of what patch you install, and rebooting the computer after each one.  After installing a patch, if it causes this error, reinstall Ubuntu, but after reinstalling, don't install that particular patch.  You should report the particular patch that caused the problem to the Ubuntu community, so this bug can be fixed.

Sorry, but that is all the help I can give.

---

