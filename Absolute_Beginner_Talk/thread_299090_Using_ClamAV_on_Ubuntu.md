---
title: "Using ClamAV on Ubuntu"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by leerjordan on 2006-11-13
My office is new to using Ubuntu.  We have a small difficulty and would appreciate some assistance or guidance.

I got Ubuntu upgraded to version 6.10 code name "Edgy". I uninstalled clamAV packages (and ran 'find -name 'clam*' / 'freshclam' to get rid of any stragglers). Then ran: 'sudo apt-get update' to get all the latest package repository info. Crossing my fingers, I typed 'sudo apt-get install clamav' and "ta-da!" it grabbed the latest version. Ran 'clamscan' it says virus definitions are outdated, so I ran 'sudo freshclam' and.....nothing. "command not found". It installed the latest version of clamAV, yet freshclam doesn't work. The package info is there, but the command isn't being recognized. I'm stumped!

---

### Post by SubWolf on 2006-11-16
It's a seperate package.

sudo apt-get install clamav-freshclam

---

