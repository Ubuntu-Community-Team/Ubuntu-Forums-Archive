---
title: "[SOLVED] Save file with ssh through elinks"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by stomakmonkee on 2008-04-12
Greetings--
Here is my issue.  I have an Ubuntu Server setup, and its CLI and headless.  I use SSH to access it.  I would like to be able to download large files directly to this server using only this server.
Presently I open a terminal, start SSH, and use ELinks to download the file.  However this means that I have to leave the terminal open or the download cancels, correct?
I would like to know if anyone knows some way that I can SSH into the server, start a download, and be able to shut down the term and have the download continue.  Any help is GREATLY appreciated.  It would save me some electricity to only have my server downloading these things and leave one machine on at bedtime :-)

---

### Post by llamakc on 2008-04-12
```

wget http://name.of.file &

```

---

### Post by stomakmonkee on 2008-04-12
That's perfect!  Thanks!

---

### Post by carltondhouston on 2008-04-12
Glad that worked for you.  I am also quite fond of running things in 'screen' sessions.  If you are not familiar, run the command 'screen'.  Then you can detach from the screen session by hitting ctrl-a, d.  Or pick back up on a detached session with 'screen -r'.  It's really handy when you need to run something but want to keep a console on it.

---

