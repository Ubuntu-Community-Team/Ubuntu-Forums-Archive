---
title: "Pidgin and OTR encryption problem"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by davesmith on 2008-01-15
Hallo, can someone plz help with my OTR problem?
 
OTR (off the record) is an exceptionally cool encryption plugin for pidgin that has all sorts of advantages over pidgin-encryption. (like having no digital signature attached to your messages etc)
 
I installed otr from the repositories but when i try and generate my personal key, pidgin hangs and i have to force it to quit. Pidgin also hangs when my privacy-minded contact's pidgin sends a request for my key.
 
Does anyone know what is going on here? I can generate keys using pidgin-encryption with no problem.
 
Thanks
 
DaveS

---

### Post by kevdog on 2008-01-17
Did you install pidgin from source?  I take it you also compiled the otr plugin from source?

---

### Post by davesmith on 2008-01-18
Thanks for your reply....to answer your question....nope, i only ever install from the repos. 
 
However I did solve the problem:-
 
Firstly I purged pidgin and then pidgin-otr. Next i found the pidgin config settings in a hidden file the the home directory ~/.purple.
 
Then I re-installed pidgin and pidgin-otr from the repos. After clicking on "generate key" i randomly moved the mouse about and randomly tapped the keyboard.
 
The key was generated and I can now enjoy secure and private conversations.
 
I recommend pidgin-otr to anyone who is concerned about privacy and security of comms over the net. Its a fine piece of code, seems very stable and works well.
 
My thanks to the guys at cyberpunks and especially Ian for helping me with this.
 
[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)
 
DaveS

---

