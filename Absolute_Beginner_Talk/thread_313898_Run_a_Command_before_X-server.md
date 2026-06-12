---
title: "Run a Command before X-server"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by darkblade25 on 2006-12-06
Ok I am new so I need the simplest instructions. 

I have 915resolution installed and I need to run sudo /etc/init.d/915resolution start before the x-server start. I want to do this so that I dont need to type it out and restart the x-server everytime I start Ubuntu. 

Does anyone know how to do this?

---

### Post by agustin.g on 2006-12-06
system --> Preferences --> Sessions

there's a "startup programs" tab, you should be able to add a new command which will be run at startup

---

### Post by jordanmthomas on 2006-12-06
[http://gentoo-wiki.com/TIP_Run_Commands_at_X_Startup](http://gentoo-wiki.com/TIP_Run_Commands_at_X_Startup)
This may be of use to you, but maybe not.  Apparently, if you have a file called .xprofile, commands in it are executed *as* X starts.  Not sure if this would be early enough for you or not...and I am also not sure where to put .xprofile for Ubuntu since the user doesn't start X.

Also, look up the program bootup manager (BUM).  Since your script is /etc/init.d, you should be able to start it when you go into init 5

Better yet, look up how to edit which init scripts are run and how to turn them on / off.  I'm not exactly sure how, so I'm not going to try to tell you how...

---

