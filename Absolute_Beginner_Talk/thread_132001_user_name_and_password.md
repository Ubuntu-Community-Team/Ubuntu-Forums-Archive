---
title: "user name and password"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by magwa999 on 2006-02-17
Had no problems installing but when it came to the first time to use my user name and password didn't work. Anyway to bypass?

---

### Post by uopjohnson on 2006-02-17
there is no way to bypass... there are ways to reset however.  
I did a search on the fourum for :reset password" and it returned [This link]("http://www.ubuntuforums.org/showthread.php?t=129226&highlight=reset+password")

---

### Post by wolfmaniac on 2006-02-17
boot system in recovery mode (in grub selec second option)
then at terminal write
sudo passwd root
to then login as root

then use set passwd user_name to use a new password

all is done

---

### Post by SMF on 2006-02-17
I am not sure at what stage you are in but if this is from the begining when you get the user name and log in and password screen then I too ran into a very strange problem as I used the name lets say:

RAMON

and the password 
wertysudo98523

Ok this is not my real user name and password (dur)

but when I went to log in I had to use 
ramon and not RAMON even though I suggested all caps in the installation when asked to assign a pass. glitch? Who knows.

also make sure your nums lock on too.

Maybe you made your password too long? I dont know what the limit is but I do know that somethings do not allow over some 12 some 16 and others 32 you get the idea.
If you cant get past that cant you just re-install the ubuntu again? since you already know what you are doing I guess nothing lost but time.

Hope my littel tid bit was helpful cus I am a newb and I suck at this but am getting by.

Peace.

---

### Post by uopjohnson on 2006-02-17
System password have a limit of upwards of 100 characters (probably 128, but don't quote me)

---

### Post by Brunellus on 2006-02-17
usernames cannot use capital letters.

---

