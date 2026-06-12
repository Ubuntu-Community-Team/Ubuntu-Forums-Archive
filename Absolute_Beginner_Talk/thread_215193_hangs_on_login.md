---
title: "hangs on login"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by tobeon on 2006-07-13
Oookay so I was installing some sort of program walked away, came back to find out that very important things had disappeared e.g. terminal, pretty much everything in the system menu etc so I decided to restart (old windows way of thinking) and now I can't login, ubuntu boots up shows the login screen I enter my username password login it loads and doesn't do anything else

any idea how I can fix this? or is a reinstall going to be needed?

Thanks for any help!

---

### Post by shoot2kill on 2006-07-13
try loading into recovery mode...

if you dual boot - select recoverymode in grub

if you only have linux, press esc when prompted at boot up, (be quick though, u only have 2-3 seconds)

---

### Post by cotcot on 2006-07-13
And what if you make a new user (adduser) from the recovery console  and login with the new user name ?
Recovery is in the boot menu. Go to terminal. 
```
adduser yournewname
adduser yournewname admin
```
reboot.

---

### Post by tobeon on 2006-07-14
I tried making the new user but logging in with the new user does exactly the same thing as logging in as the old user, it accepts the username and apssword then just goes to a blank screen (like you get just before the desktop loads) but the desktop never loads :(

---

