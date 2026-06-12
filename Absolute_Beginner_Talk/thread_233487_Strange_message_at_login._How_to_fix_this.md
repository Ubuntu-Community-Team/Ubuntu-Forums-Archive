---
title: "Strange message at login. How to fix this?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-08-10
Hello!

I use Xubuntu 6.06 and since yesterday when I login as the only user I defined I get this message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

There is a button of "OK". I press it and all seems normal, but this is a bit anoying.

How can I fix whatever I have done bad? :confused: 

Thanks!

Jordi

---

### Post by Titus A Duxass on 2006-08-10
You'll have to go into a terminal and sudo chmod 644 the file and directory.

You might be able to do this in the GUI by right clicking on the file and look/editting the properties.

---

### Post by orb9220 on 2006-08-10
sudo chmod 755 /home/<username>/.dmrc

Should do the same, and may be a bit safer

---

### Post by jordi_rc on 2006-08-10
To anyone that may help:

The problem was not solved by the instructions you gave me but was something very similar. These 2 instructions in Terminal solved it:

sudo chmod 700 /home/jordi
sudo chmod 644 /home/jordi/.dmrc

where "jordi" is the name of my user.

Now it is OK.

Thanks again.

Jordi

---

