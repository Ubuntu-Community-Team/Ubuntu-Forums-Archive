---
title: "Additional System Sound for Login"
date: 2007-02-26
forum: Art &amp; Design
---

### Post by Bluesharp on 2007-02-26
Here's an additional sound file that I created with star-up/ login in mind.  Not that the default was that bad, but it didn't get me in the right mindset for some reason.  

It was too big to attach,  so I have it posted here:

[http://homepage.mac.com/wizzard4/](http://homepage.mac.com/wizzard4/)

Its called "login21.wav"

You can play it on the desktop you music/movie player. 

To get it running on login/start-up,  you'll need to add it to usr/share/sounds.  Since this file is owned by root you'll have to log in as root or work the magic in the terminal.   Me and the Terminal don't seem to get along too well so I had to go to System -> Administration -> Login Window - punch the Security tab and enable root login there.  Seems like I recall the root password had to be straightened out in Systems-> Administration -> Users and Groups,  as well.   

The sound file is a .wav (Windows) file formated as "signed 16 bit PCM."   I tried some other formats but none would play but this.  

Once in, log back in as "you" and go back to System ->  Preferences -> Sound and punch the middle sounds tab.   At the bottom you'll see Log in:  You should select "select sound file . . . "  which will give you the contents of usr/share/sounds. Double click login21.wav.   I had to re-boot to get it to set.  

As to the thing itself,  it seems to me to be close to "good,"  but then .  .  I'm posting for your thoughts.

---

### Post by Bluesharp on 2007-02-27
I've added another log-in and a log out.   

If you add them to usr/share/sounds by the log in as root method,  it may be better to copy these files to the home directory while you are in your normal user mode.  They will be easy to find in the home folder when you are logged in as root.

---

