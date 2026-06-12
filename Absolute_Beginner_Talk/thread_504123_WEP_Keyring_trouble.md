---
title: "WEP Keyring trouble"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-18
ok i just recently got my wireless working on my dell laptop (thanks god!!!) and when i was configuring the details it asked me to enter a Keyring password. So i entered a password and confirmed it, now every time i log in its asks for the Keyring Password. I type in the password and it  brings up the message again as if i entered it incorrectly. Does anyone know how to fix this, it is very annoying to open a document i made of all my WEP keys and copy and paste when i could just type in my password. I know this is just me being lazy but it has been happening for a while now and I really want a solution. I have tried many things but none have workd. 

What should i do??:confused:

---

### Post by tennvolsmb on 2007-07-18
anyone?

---

### Post by Papi-KB7VGW on 2007-07-18
Is it the same password that you use for root access?  That is what I used but it only asks for it once when I logon.  I think that the default is to always ask.  But that doesn't help with why the 2nd time.  Sorry  maybe some knows how to change it.

---

### Post by ubanchaos on 2007-07-18
i think u might  need to use the synaptic package manager

---

### Post by bigboy_pdb on 2007-07-18
If you want to reset the gnome keyring manager then do the following:
Go to "Places -> Home Folder". Press Ctrl-H to see the hidden files and folders. Go into the folder ".gnome2" and then the folder "keyrings" and then delete the file called "default.keyring".

---

### Post by anewguy on 2007-07-18
I'm just a rookie here myself, but I have to agree with what bigboy_pdb said about deleting the default keyring.  I for some reason had the same problem you did after a changed network managers, and deleting that file solved it for me because it asks for a password and confirmation to set it all up again.  If you don't know, I read a post somewhere (I'm very sorry I don't remember where) on something I think was called "Pam", and if I understood what it was saying correctly, you can set it up so that if your logon password is the same as the password for the keyring it will just automatically use it and not ask for your password for the keyring when you start up.  I haven't tried that yet, as I'm new enough I have my own little list of things I want to try before I get around to that one.

Maybe this can help you or somebody else who may reading this thread.:)

---

