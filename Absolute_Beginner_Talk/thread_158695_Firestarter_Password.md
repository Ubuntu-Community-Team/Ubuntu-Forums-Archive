---
title: "Firestarter Password"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by phil66 on 2006-04-11
I have installed Firestarter Firewall and activated same.

Having read all the threads and followed the instructions to the letter I have been able to autostart but not eliminate having to use password.

In /etc/sudoers I am typing on the last line
ram7lc   ALL=NOPASSWD: /usr/sbin/firestarter

The panel for the password continues to open. 

I have set auto start to open after gnome ppp to allow dialup before Firestarter loads.
This works fine but still getting password panel.

Sudoers shows no syntax errors.

I have also made all the entries with Firestarter unloaded.

What am I missing to get nopassword to work.

Thanks for the help
Ray

---

### Post by cstudent on 2006-04-12
Take the space out between NOPASSWD: and /usr/sbin/firestarter

---

### Post by phil66 on 2006-04-12
[QUOTE=cstudent]Take the space out between NOPASSWD: and /usr/sbin/firestarter[/QUOTE]

Hi cstudent

Thanks for the reply

I took the space out between NOPASSWD and even moved the space between username and ALL.

This made no difference I am still being asked for a password.

Upon making all these moves should I not be getting a syntax error???

Tried removing the auto start and using manual login this did not work
.
No errors just plain  will not work.

Ray

---

### Post by cstudent on 2006-04-12
I take it you have read the Firestart FAQ at
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I don't know if you would get a syntax error if you have things wrong in the sudoers file. I think that any entries that aren't syntactically correct are just ignored. Seems to me I had the same kind of issues when I first starting using Firestarter and it came down to the entry in the sudoers file. I no longer have Firestarter setup that way. I let FS run in the background and only open the GUI when I want to make some changes. I don't mind entering my password for what little I have to open FS. But if you have to enter your password everytime you go online, I can see where that could become a pain real quick.

---

### Post by Sbarton on 2006-04-13
[QUOTE=phil66]Hi cstudent

Thanks for the reply

I took the space out between NOPASSWD and even moved the space between username and ALL.

This made no difference I am still being asked for a password.

Upon making all these moves should I not be getting a syntax error???

Tried removing the auto start and using manual login this did not work
.
No errors just plain  will not work.



Ray[/QUOTE]

I had the same problem I configured firestarter to start hidden by the following method: Gnome menu/System/Preferences/Sessions. Clicked on startup programs and added the following: sudo firestarter --start-hidden.Then deleted a existing entry which was gksudo /usr/sbin/firestarter. Closed everything rebooted and I have not had the box for password appear. I know Firestarter is running because when I shut down I see the entry for stopping Firestarter appear in the shutdown sequence.HTH
Regards

---

### Post by phil66 on 2006-04-13
cstudent

sbarton

Thanks for the help

I finally got a syntax error in sudoers by jamming all the script together.
Then I set it back up as recommended and no more syntax error.

Went to session startup programs and added sudo firestarter --start-hidden
this gave me the start without the password prompt.

Getting error message needed to be root to start firestarter.
Back to startup current sessions and found firestarter as an entry removed same.

Firestarter now starting with no password prompt and docking in the panel.

Thanks to everyone who help me get this app working to my satisfaction,

Ray

---

