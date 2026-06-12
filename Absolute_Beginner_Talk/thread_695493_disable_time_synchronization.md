---
title: "disable time synchronization"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-13
Hi 
I was told that to completely remove time synchronization I have to edit something here: /etc/rcS.d/S11hwclock.sh 

but what do I do with this?

---

### Post by Cypher on 2008-02-13
Who told you to remove time sychronization? And that particular script is essentially getting the current time from the RTC (real time clock) on your Mobo and using that to keep Linux happy and when Linux is going down, the value is sent back to the RTC (which will continue to run as even though Linux isn't running).

NTP is code that is actually sychronizing your system time with an external server on the Internet..

---

