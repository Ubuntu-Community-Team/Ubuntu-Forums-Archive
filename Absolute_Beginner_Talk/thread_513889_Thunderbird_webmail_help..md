---
title: "Thunderbird webmail help."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by travislhendrix on 2007-07-31
I am new to Ubuntu and lenix in general.  I am trying to install the webmail extensions in thunderbird to allow it to connect to hotmail (I know hotmail is not the best).  I had it set up in windows without a problem, but in Ubuntu it will not connect to the localhost.  When I try to get mail I get the message "could not connect to localhost; the connection was refused".  Is there something special I need to do to set up the localhost?

---

### Post by heimo on 2007-07-31
I don't understand why it needs to connect localhost, but there must be some reason? Anyway, try pinging localhost in terminal. In other words, open a terminal window (it's somewhere in your upper left menu) and type:
```
ping localhost
```

You can stop it with ctrl+C or just closing the window. Does it ping localhost?

Please link to the extension we're talking about.

---

### Post by travislhendrix on 2007-07-31
Yes it can ping localhost.  It needs to connect to localhost because that is how it creates a pop server for hotmail, gmail, yahoo, lycos, and others.

---

### Post by travislhendrix on 2007-07-31
sorry here is the link [http://webmail.mozdev.org/index.html](http://webmail.mozdev.org/index.html)

---

### Post by travislhendrix on 2007-08-16
I found a solution to this for anyone who needs it.  The problem was that I was not running thunderbird as root.  I created a launcher by clicking on the desktop and selecting create launcher.  I then changed it from application to application in terminal (not sure why the first did not work).  Then I gave it a name and put the command  sudo /opt/thunderbird/thunderbird.
Now when I run the launcher it opens a terminal and asks for the password which I put in then thunderbird opens and all extensions work fine.

---

