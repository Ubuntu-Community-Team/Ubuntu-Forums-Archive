---
title: "new to linux, should I use server or desktop?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by edmicman on 2006-08-22
I've played with linux a little bit, run some livecds, etc., but am looking to jump in and learn more.  I have a spare PC (some old HP Celereon) that I'd like to turn into a file server to hold some backup files, etc.  My question is:

Should I install the server version of ubuntu or the desktop version?  I think the server install would be more appropriate (I can do the canned LAMP install and also use it as a file server, too, right?), but I see it doesn't install a GUI.  Being new to administering a linux box, and really my only experience being with livecd GUIs and such, I'm thinking maybe I might install the desktop version and sort of run it as a "server" anyway.  I dunno.  Now that I think about it maybe I should just go head first into the server install and learn from there.  Just wanted to hear some thoughts - thanks!

---

### Post by Nick Garvey on 2006-08-22
I think you could do the server install then do "sudo apt-get install ubuntu-desktop" if you wanted.  That way you get the LAMP set up for you and a GUI.

---

### Post by Brunellus on 2006-08-22
"server" is just that.  no GUI, no X.  Commandline or bust.

IF--and this is a big IF--you are willing to learn how to configure and administer a server with the command line only, go ahead and install "server."  

If you don't feel up to learning how to do that, install one of the desktops and add the necessary packages/services to make it a server.  

A headless server without X is easier to deal with because it can be administered remotely (via ssh), and because it runs with less overhead (no GUI!).

---

### Post by edmicman on 2006-08-22
Thanks everyone for the replies!  The "headless" server is nice - I've set up a knoppmyth install that I followed tutorials to use ssh to administer, and that works slick.  I think the server install will be the way to go for now, and I'll just learn what I need to do.  Sometime I'll get around to fully converting over to the desktop install, too....just gotta get my .NET development desktop built!  Thanks!

---

### Post by steve.horsley on 2006-08-22
Desktop. Desktop. Desktop.

If you're a beginner, go for the desktop install. then you get all the GUI whiz-bang utiities. Once you have your servers set up it's an easy step to kill the GUI, so unless you are absurdly short on disk space it won't hurt to have it there. And having a GUI file system navigator and a GUI editor while finding your way around is invaluable.

---

