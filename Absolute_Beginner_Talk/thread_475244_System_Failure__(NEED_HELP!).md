---
title: "System Failure  (NEED HELP!)"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by james.gravley on 2007-06-15
When I boot my machine in Ubuntu, it goes to the login window like normal. However, from there I get an error message saying that "Either the disk is full or ... home folder could not be written to, contact system administrator."  I am still very new to Ubuntu and have no idea what happened. It was running fine, I restarted and boom. Any help here would be very greatly appreciated.

---

### Post by 67GTA on 2007-06-15
When it is booting(before the login window) try hitting ALT + F1 to see if it will drop you into a text window. You might be able to get some error messages that will help diagnose it.

---

### Post by Dr Small on 2007-06-15
Did you recently change any permissions for your /home/$user folder?
It sounds like it doesn't have sufficient write permissions.

Dr Small

---

### Post by james.gravley on 2007-06-15
No I haven't changed anything like that. I will try the alt-F1 thing

---

### Post by james.gravley on 2007-06-16
The first part of the error message says

"GDM could not write to your authorization file." and then the rest that I said before.

I did the alt-F1 thing and the only part that might be something said,

[31.600000] intel_rng:FWH not detected, but then it kept going and went to my login screen. 

Thanks again, and I hope that helps

---

### Post by 67GTA on 2007-06-16
That could be a couple of things. Do you know how much free space is left on your root partition? If it is full it will cause that error because there is no room left to write. How big is your partition? Boot into recovery mode and run "df-h". That will tell you. Your var file could be full also. Try "du-h" from inside the var folder.

---

### Post by james.gravley on 2007-06-16
Yeah, for some reason my 20 GB partition with ubuntu got completely filled up (?) so I just did a reninstall. thanks for the help as always.

---

