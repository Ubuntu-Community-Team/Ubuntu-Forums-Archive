---
title: "Sudo commands (Solved)"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Alvar on 2006-10-25
When I type in a sudo command I get 
"Sorry, user sumel may not run sudo on localhost."
What do I do about this, Ubuntu is not letting me listen to music or change files because of this. I don't know how I got into this

---

### Post by NeoGreen on 2006-10-25
You may have to change the privileges of the user.  I'll have to remember how to do that.  I'll have to get back to you on this one.:)

---

### Post by Alvar on 2006-10-25
To add a new user to sudo, open the Users and Groups tool from System --> Administration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Executing system administration tasks and check that.

/!\ In the terminal this would be: sudo adduser $user admin, where you replace $user with the name of the user. 

But the thing is that I don't have a User and Groups option in my admin menu](*,)  And the terminal doesn't work eithher

---

### Post by NeoGreen on 2006-10-25
Did you create a root or superuser when you did the install?

---

### Post by Alvar on 2006-10-25
I'm not sure, but the thing is that I could do admin tasks before and mysteriously one day I don't have access to admin tasks?? Whats up with that. But what i'm gonna do now is reboot and go into recovery and addggroup username admin.  That should help I guess. Wish me luck

---

### Post by astoltz on 2006-10-25
You'll have to boot to single user mode.  If you don't have sudo rights to begin with, you won't be able to give yourself sudo rights.

Once in single user mode, the command line should do the trick.

---

### Post by Alvar on 2006-10-25
Thanks so much guys!!:)  It worked, I'm not sure what you are talking about single boot?? But I had root privillages in recovery and I finally am added to the root user account. I'm so happy Now I can listen to music off my other partition. At least I hope??

---

