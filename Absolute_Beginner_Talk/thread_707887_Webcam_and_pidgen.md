---
title: "Webcam and pidgen"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by MasterAlone on 2008-02-25
[B][COLOR="Red"][SIZE="3"][SIZE="5"]I am moving from windows to ubuntu slowly as I learn how to do more things in linux.  I have 2 questions tho.


First, in windows I have used trillian for years to handle all my IMs.  It starts automaticly at bootup.  How do I get pidgen to do the same thing?  I am so used to the automatic startup of trillian, I have spent hours doing something in ubuntu only to realize that pidgen wasn't running and nobody could contact me.

Second, where can I find information on webcams such as installation, use with a messenger like yahoo, etc.

TIA[/SIZE][/SIZE][/COLOR][/B]

---

### Post by PeterJS on 2008-02-25
Big red text doesn't help.

Start up stuff is handled by System > Preferences > Sessions, the front tab is programs that auto start.

Here's the documentation on webcams, which ones just work, which ones need some work, and which don't:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by bazzawill on 2008-02-25
To get pidgin to start when you log in go to system -> preferences -> sessions in the start up. tab click add to add a new start up program. Fill in the details as follows 
Name: Pidgin
Command: pidgin
Comment:Send instant messages over multiple proticols.
Unfortunatly as far as I am aware pidgin cannot use webcam's at this point in time

---

### Post by spiderbatdad on 2008-02-25
gyache is a good yahoo client with webcam support. Kopete also has webcam support.

---

### Post by Crafty Kisses on 2008-02-25
> **spiderbatdad said:**
> gyache is a good yahoo client with webcam support. Kopete also has webcam support.

I actually really like Kopete. :)

---

### Post by MasterAlone on 2008-02-25
**[COLOR="black"]Tried a restart and a cold boot.  Pidgen didn't start automaticly.[/COLOR]**

---

### Post by igknighted on 2008-02-25
> **MasterAlone said:**
> **[COLOR="black"]Tried a restart and a cold boot.  Pidgen didn't start automaticly.[/COLOR]**

the command is "pidgin", not Pidgen.  Did you spell it properly?

---

### Post by macogw on 2008-02-25
> **MasterAlone said:**
> **[COLOR="black"]Tried a restart and a cold boot.  Pidgen didn't start automaticly.[/COLOR]**

Since you keep spelling it wrong here, could you double check that you didn't spell it wrong in the preferences thing?

---

### Post by MasterAlone on 2008-02-25
**[SIZE="2"]Thank you for the spelling correction, works perfectly now.[/SIZE]**

---

### Post by zorkerz on 2008-03-18
I am going to set pidgin to load on startup as well. However i would like it to wait until i have connected to a network. At home my network requires me to give the password for the default keyring.

is there a simple way to do this?

my first guess will be under the current session tab in sessions to set pidgins order high say 60, but as the tab name implies its only the current session.

Also does anyone know what the various styles in the current session tab mean?

---

