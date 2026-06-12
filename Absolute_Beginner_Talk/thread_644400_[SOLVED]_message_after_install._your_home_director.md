---
title: "[SOLVED] message after install. your home directory does not appear to exist"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Silvain on 2007-12-18
After an install on a system using a remixed disc, I cannot access my home directory it appears. Get message "You home directory is listed as /home/xxx but it does not appear to exist. Do you want log in with the /(root) directory as your home directory ? It is unlikely anything will work unless you use a failsafe session" This is along with the yes or no radio buttons. I click yes then get this message "users$home/.dmc file is being ignored. This prevents the default session and language from being saved. File should be owned by the user and have 644 permissions. Users home directory must be owned by the user and not writable by other users." Anyone wanna take a try at this ?

---

### Post by yabbadabbadont on 2007-12-18
Are you currently logged in using the failsafe session?

---

### Post by spiderbatdad on 2007-12-18
so are you booting into the live cd, since you cannot access /home/user?

---

### Post by Silvain on 2007-12-18
Yeah I can boot off the livecd, but I can get into terminal with failsafe session, if i boot up from the Hd install. I can see the /home dir if I do "ls -l"  return is listing it as "drwxr -xr -x 2 root root 4096 ... home 
Is this informations useful ?

---

### Post by yabbadabbadont on 2007-12-18
Yes.  Please also post the output of "ls -l /home".

---

### Post by Silvain on 2007-12-18
I typed "ls -l /home" and got " total 0"

---

### Post by yabbadabbadont on 2007-12-18
What is the name of the user you created during the install?

---

### Post by Silvain on 2007-12-19
I decided to reinstall again, setup more parts, logical and /user /temp / /boot   . can't hurt anyways :lolflag:

I'll see if the problem crops up this time. possibly the trouble was due to not setting up enough diff parts? Oh and I am trying an entirely diff user name now. Maybe using same as what was used to make the remastered install disc was bad idea also ?

---

### Post by macogw on 2007-12-19
They're called /usr and /tmp

It appears that whatever remixed install disc you used didn't set it up correctly.  As root you'd need to 
mkdir /home/username
chown username:username /home/username/

---

### Post by Silvain on 2007-12-19
Oh and I made all the new parts as ext3, was doing some reading and some users seemed to be saying nice things about ext3. Well except for the swap partition.

---

### Post by Silvain on 2007-12-19
Oh that was just me saying that I picked from the Part menu those options. They were not spelled as I posted them necessarily, but thanks for the help :)

---

### Post by Silvain on 2007-12-19
Ok, the install went all the way this time, evidently the installer did not like the size of my swap partition so , the install did not finish. Thanks again for the replies. That was my 4th or 5th try. And yes its good news  that I  have a mostly working remastered install disc. :)

---

