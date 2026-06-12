---
title: "X11 error.  Please help"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-22
THIS IS (partially) SOLVED, THANKS!  Still having other issues, but I'll make a new thread.  

I (finally) got the Samsung linux printer driver software to install properly, and even ran it a few times, but never got past the login screen.

Now, when I run it from the terminal, I get an error stating:  

"Linux Configuration must be run from X11."  What can I do to accomplish this?  Doesn't Ubuntu already include X11?  This is vital, please help.  Thanks.

---

### Post by Brunellus on 2005-11-22
if iunderstand correctly, it means that you must run the program from inside an X session, rather than frmo a tty console.

---

### Post by adwait on 2005-11-22
It means that you should it run it through the GUI. Which terminal are you talking about? The one in the Application menu? Or the one you get when you rpess Shift+Alt+F1? Try running from the terminal in the application menu. Also, try running it from the "Run Command".

---

### Post by deNoobius on 2005-11-22
I was talking about the terminal in the applications menu.  I can get the program to run from the GUI, but, the only way I've been able to get the program to work is to login as root.  This is my printer driver, which doesn't seem to work well with Ubuntu.  


What happens next is that the software runs, I click "add printer", and a dialog appears asking me to sign on as  "administrator."   But I can't -- if i sign is as myself or root, I get an error.

I realize that this is a program specific problem, but, would there typically be some kind of configuration file that I could edit to get rid of the password request, (or get it to accept my password), or is this most likely in the binary itself?  I tried changing the file permissions to rwx for everyone, but that didn't help.

---

