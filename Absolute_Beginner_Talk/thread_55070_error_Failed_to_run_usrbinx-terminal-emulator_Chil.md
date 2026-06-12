---
title: "error: Failed to run /usr/bin/x-terminal-emulator:
 Child terminated with 1 status"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by Titi on 2005-08-07
Hello, i'm Maarten and i just installed UBUNTU (hurray), i'm totally new to it and know absolutely nothing about it. when i try to update with the update manager (or other stuff), and they ask for my password and i fill it in correctly, i get this error: Failed to run /usr/bin/x-terminal-emulator:
 Child terminated with 1 status

does anyone know what this means and what to do about it?

thanks in advance,
maarten

edit: here is what ubuntu tells me when i try to Su myself, or when i want to do anything, really:
maarten@Maarten:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
maarten is not in the sudoers file.  This incident will be reported.
maarten@Maarten:~$ sudo su
maarten is not in the sudoers file.  This incident will be reported.
maarten@Maarten:~$

---

### Post by Oceola on 2005-08-07
I'm as new as you are and I had a similar problem.
I had not set up root and root password so logging on as user didn't allow some administrative functions.
Do Not type quotation marks only to define typed info:

Open a terminal
Type  "sudo passwd root"
It will prompt for your password, Enter it
It will ask for the new Unix password: Type and enter a new password(root)
It will prompt for a repeat, Type the same and enter (root)
Note: Root is what you are making the password for.

Close the terminal, go to System->Administration->Login Manager
enter your user password when asked.
Under security tab select Allow Root Logins

Then logout and and log back in as Root and use the new password.
Open the root terminal and see if that lets you do your tasks.

---

### Post by confused on 2005-08-17
I have the same problem when i try to login to my root terminal or open a synaptic. Hence I am not able to perform any changes or do any editing with any of the files. Plz plz help.

---

### Post by cwaldbieser on 2005-08-18
[QUOTE=confused]I have the same problem when i try to login to my root terminal or open a synaptic. Hence I am not able to perform any changes or do any editing with any of the files. Plz plz help.[/QUOTE]

OK, this is a long shot, but can you open the "terminal" application from the menu?  If you can type:
```

$ /usr/bin/x-terminal-emulator
```
at the prompt?  What *should* happen is that another terminal window should open up.  However, if this problem is malfunctioning for you, maybe some sort of error message will appear in the original terminal.  If so, post that error information here, and maybe someone will be able to understand what it means.

---

### Post by garnertr on 2005-10-10
your example good doesn't help me at all... sigh...  has anyone been able to fix that type of error?

I get the same exact errors as the 1st poster... and yet cannot bypass the root-terminal...

will I have to install again?

---

