---
title: "Added accounts not accesible?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Sladi on 2007-05-02
Hi! 

I added accounts via System/Administration/Users-Groups. I clicked on add user and I guess I added root accounts, since I can't access them or see their folders. 

Then I added another user by right clicking on my account. This works fine. 

How can I remove the other accounts? 


Regards, 
Sladi

---

### Post by Seisen on 2007-05-02
Go back into User-groups and delete them, you should have an option to.

---

### Post by Sladi on 2007-05-02
Thanks Seisen but they're not listed in the GUI. :) 
I can see their folders in the terminal or in Nautilus. 
The last one I created by right-clicking on my account is listed and it works fine however.

---

### Post by Seisen on 2007-05-02
Check to see if the users where added to your group.

---

### Post by LaurelLynn on 2007-05-02
You can always go straight to the source.  ALL accounts have their settings in the two files "/etc/passwd" and "/etc/shadow" (shadow needs root permissions to read).

For each account there is a one line entry in each file. So, you can view exactly what accounts there are/are not. Removing those lines removes the account. It does not delete the home folder though. (which is listed in /etc/passwd).

Another trick is clearing the password through "/etc/shadow". The entry between the first two sets of colons is the password hash. Removing it leaves the account without a password.

There are tools both comand line and graphical to do all of this, but they do so by modifying these files. So changes here ALWAYS take effect. They are the ultimate authority.

---

### Post by Sladi on 2007-05-03
Thanks! :) 

I seems they are groups. There are no entries in "/etc/passwd". I'm sure clicked on "add user" though. They're listed under "manage groups". 
When I want to remove those, I get a warning about files' group IDs. 

There are folders for those groups in /home. Is this normal? 
I guess I should do this before I delete the groups? 

Also can I delete the groups added for every user? 

:popcorn: 

Regards, 
Sladi

---

