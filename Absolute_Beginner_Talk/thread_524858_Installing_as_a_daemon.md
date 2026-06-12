---
title: "Installing as a daemon"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-08-13
How can I make sure an application starts every time I start my computer (whether I log in or not)?

I'm trying to make Geronimo web server start automatically.  But this may be something I want to do with several applications.

---

### Post by yellowband on 2007-08-13
hmm interesting, think i'll subscribe to this post for an answer as well.


You could add the command to your session preferences, but like you say, the command may not be executed if you don't actually log in.  Maybe you could have an automatic login when your computer starts.

---

### Post by schorsch on 2007-08-13
Just write a start script, place it in directory /etc/init.d and make two links to this script in /etc/rc2.d, then the application will be started at boot.
The first link starts with SXX and the second link starts with KYY.
"S" for start and "K" for kill/stop; "XX" and "YY" determine when the skript will be run to start and stop the appliaction. To start a webserver of course makes only sense when network is up and running. Stopping the webserver should be done before the network is shut down.
Just take a look in directory /etc/init.d and perhaps you can take the file "apache2" as an template.

---

### Post by purdticker on 2007-08-13
/etc/init.d/apache2

/etc/rc2.d
S91apache2 -> ../init.d/apache2

---

### Post by purdticker on 2007-08-13
Ok I think I understand, thanks!

---

### Post by purdticker on 2007-08-28
ok I created the script:
**/etc/init.d/geronimo**
> 
:/etc/init.d$ cat geronimo 
/opt/geronimo/bin/startup.sh
/opt/james/bin/run.sh


> 
:/etc/init.d$ ll geronimo
-rwxr-xr-x 1 root root 52 2007-08-27 20:52 geronimo


Then I created a softlink in
**/etc/rc2.d**
> :/etc/rc2.d$ ll *geronimo*
lrwxrwxrwx 1 root root 18 2007-08-27 20:54 S91geronimo -> ../init.d/geronimo



However, when I restart my computer, nothing happens...

---

### Post by schorsch on 2007-08-28
You should take an existing startup script as a template. When the script is called at startup via the link S91geronimo the command executed is
```
/etc/init.d/geronimo start
```
as far as I know. But when your script is called with the parameter "start" I guess it wil not work. So I would take a small script like "/etc/init.d/atd", copy it to "/etc/init.d/geronimo" and edit it to suit your needs. Furthermore you will have the correct header syntax by acting this way.

---

