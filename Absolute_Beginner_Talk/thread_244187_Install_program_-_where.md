---
title: "Install program - where?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by McBainUK on 2006-08-26
OK, new to Ubuntu/Linux so be nice :) 

I've used Automatix to download Google Earth and it's asking me were do I want it to install. It's defaulting to my 'home' folder, isnt that like installing to "My Documents" in Windows!?

Be nice to have a seperate location to install programs, is the such a thing as a "Program Files" folder in Ubuntu? Or is this this how Linux works?

---

### Post by RavenOfOdin on 2006-08-26
The closest equivalent to "Program Files" is the /usr/sbin directory -- This is where system executable files are stored, albeit one level up from /sbin, which 
would be equivalent to C:\WINDOWS.

Linux installs can work in any number of ways. Some require you to install files to /home, some to /usr/sbin, etc. Some can even make you install to the /opt 
directory.

Where its installed is all dependent on what the program does and what it'll need to access.

Go with /home to be safe.

---

### Post by daou on 2006-08-26
Usually programs install themselves under the /usr/ directory. However, if you are relatively new to Linux I recommend you install it in your home directory. What you should do is make a "programs" folder in your home directory and install it in there and place any additional programs that prompt you for installation in there as well.

---

### Post by daou on 2006-08-26
But if you choose to install it under usr, you need to give the program admin rights with the sudo command.

---

### Post by McBainUK on 2006-08-26
> What you should do is make a "programs" folder in your home directory and install it in there and place any additional programs that prompt you for installation in there as well.
Done this in the end.

Thanks for the super-quick replies. There is so much to learn... :)

---

