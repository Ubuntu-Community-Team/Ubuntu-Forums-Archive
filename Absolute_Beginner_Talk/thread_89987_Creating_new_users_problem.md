---
title: "Creating new users problem"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by lauchenauer on 2005-11-13
I have just installed ubuntu and am trying to create additional users. That all seems to work fine and the user is created in the GUI as well. The problem happens when I log out with the main (admin) user and attempt to log in as the user that was just created ... I just keep getting the the message "Incorrect username and password". I have tried this multiple times so it is definitely not a problem of getting the wrong password.

---

### Post by Mustard on 2005-11-13
You seem to have done everything correctly.  I can only assume its some small detail, like case sensitivity or caps lock key being on, or something along those lines.

---

### Post by lauchenauer on 2005-11-13
I just tested it again and set the password to something really simple (abc) and I still get the same response when trying to log in, so it has to be something else than a caps lock problem or case sensitivity.

---

### Post by lauchenauer on 2005-11-14
I have now also tried reinstalling the complete system again and have come across exactly the same problem again. I tried this on the default install and did nothing before adding the new user.

---

### Post by gruepig on 2005-11-14
That sounds very strange ....

First, let's verify that the new accounts have been created.  Account information is stored in the file /etc/passwd (and /etc/shadow).  Take a look in this file (using 'less' from a terminal or 'gedit' in X or whatever) and see if the usernames you created are in there.

Also, while logged in as the main user, open up a terminal (or switch to the console) and type in 'su - <newusername>'.  Enter the password for the new user account when prompted.  Does that work, or do you get an authentication failure?

Also, if you log out of X or switch to a console (ctrl-alt-f1), you should see a login prompt.  Can you log in with the new username/password here?

---

### Post by lauchenauer on 2005-11-14
I checked the /etc/passwd file and the new user is listed in there

though no matter what I try ... su - new user or going to the console (Ctrl-Alt-F1) i keep getting Login incorrect when attempting to log in with the new user.

---

### Post by lauchenauer on 2005-11-14
I just made an interesting discovery .... if I use adduser in the console it seems to accept the user. adding the user in the GUI does not work correctly.

---

