---
title: "trouble starting desklet"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-23
I have just downloaded the adesklets program:

sudo apt-get install adesklets

afterwards, I downloaded the weatherforecast.2.0.tar.bz2  which was stored into my /temp.
my question is how do I start it?  I restarted everything using ctrl+alt+bckspce.  Can anyone help?

---

### Post by Happy_Man on 2007-09-23
You have to use the adesklets configuration programs. First, though, move the file into your /home. /tmp gets wiped every 30 days, so it's not a good place for long-term storage.

Don't use ctrl-alt-backspace unless you really have to. It's a very powerful command that restarts the GUI backend. Not something to be used frivoulously unless you have good reason, IMO.

---

### Post by fiskking on 2007-09-23
I extracted the files to /home and read the readme file.  The only requirements was to have Python 2.3.4(not sure if I have Python installed,though) and adesklets version greater than 0.4.0.  I double-clicked the weathercast.py file where nothing happened.  You stated to use the config. programs but how do u do so?

---

