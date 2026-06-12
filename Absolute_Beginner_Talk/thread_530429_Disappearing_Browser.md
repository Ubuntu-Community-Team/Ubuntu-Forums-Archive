---
title: "Disappearing Browser"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2007-08-20
Hello everyone;

As I am surfing the web with Firefox, my browser will suddenly disappear. I have to relaunch it and choose whether to restore or start a new session. First I thought it might be Firefox itself, so I switched to Swiftfox. Same result. How could I find the source of this problem? It is very hard to enjoy surfing the web when your browser keeps closing down and/or dissapearing.
I am almost at the point where I want to reinstall Ubuntu 7.04 from scratch.

Thank you for all your help,

Loyaleagle :confused:

---

### Post by irish_flu on 2007-08-20
OK I'm not really familiar with which files are shared by Firefox and Swiftfox so some of my suggestions might not be relevant.

For starters, do they share "themes"?  If so, and if you're using the same theme, switch to a different theme and see if that makes a difference.


I'd also try using Synaptic to reinstall Firefox.  BACK UP YOUR BOOKMARKS before you do this.

System ---> Administration ---> Synaptic Package Manager

Search for "firefox", and find the package called simply "firefox".  Click on it, and select "Mark for Reinstallation".

---

### Post by irish_flu on 2007-08-20
Oh yeah, one other thing I'd try:

Open up a terminal window, and start firefox by typing the command "firefox" at the command prompt.  When it crashes, you might see the error printed in the window.

---

### Post by loyaleagle on 2007-08-20
Ok, I will try to start it from the terminal ans see what error comes up. I will also try to reinstall it from the synaptic package manager. I will let you know what happens.

Thanks....

---

### Post by Raineer on 2007-08-20
I've had this happen, and it only showed after Firefox went to version 2.0+

1.5 was as stable as could be, and I believe that Swiftfox shares the 2.0 code (as it's just a tuned firefox).  You might try installing Firefox 1.5 and see if it still occurs.

---

### Post by Dr Small on 2007-08-20
I have the exact same problem, hence I am using Swiftfox too, but it does exactly the same thing. I may have to try this.

Dr Small

---

