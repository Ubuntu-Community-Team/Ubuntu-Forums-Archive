---
title: "Please Help !!! Urgent"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by manishraichur on 2006-11-13
Hi all
I installed a new language support from System --> Administration --> Langauage,but made my login window as "English (USA )" as default
So now i have 2 language supports.

The problem is whenever i enter my login informatiom, the desktop comes up for a min and again it takes me back to login screen.

Manish

---

### Post by manishraichur on 2006-11-13
** bump ** update: I can login as guest (other account that i created )

---

### Post by LLRNR on 2006-11-13
Wow now that's a good thing if you can log in as guest... but what exactly doesn't work with your first account ? Do you get a red writing telling you that you mistyped your password ?

Anyway, if you can login using another account, then maybe you can try to un-do the changes you made that first got you into this mess... I don't know if it's possible, but give it a try, anyway. (Try to un-install the language support you just added)

LLRNR

---

### Post by MrFSL on 2006-11-13
Alright you logged in with another account... this tells you that there is not a system-wide problem but rather a local one -> Probably having to do with some settings stored for your original user.

Log in as "Guest" open a terminal and:

sudo su

This will get you root access.

cd /home/UserName

Go into your home folder (replace UserName above with your actual username)

And now you can delete out configuration files with are hidden files (i.e. they have a "." in front of them) which will only effect that user. To see all these files you can:

ls -A

You can be selective about what you delete, but in my experience I would find it just as easy to: 

rm -rf /home/UserName/.*

Sure... that resets you account and all your settings but its might very well be the fastest method.

Hope this helps.

---

### Post by manishraichur on 2006-11-13
i can just log in to my guest account and not as root user
when i do Crtl+Alt+F1 i can log in as root.

please help me how to fix this

---

