---
title: "How to use Openbox :S"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-15
Hey I just switched from fluxbox to openbox. First thing is since there are no toolbars or menu entries, where would I/how would I edit the menu entries and add a toolbar?? Appreciate the help :D :D

---

### Post by bodhi.zazen on 2006-10-15
> **WalmartSniperLX said:**
> Hey I just switched from fluxbox to openbox. First thing is since there are no toolbars or menu entries, where would I/how would I edit the menu entries and add a toolbar?? Appreciate the help :D :D

You need to find a panel you line and add it to the openbox start scripts.

My favs are pypanel, fbpanel, and perlpanel. fbpanel is NOT related to fluxbox.

~.config/openbox.sh:
> #!/bin/sh

#Screensaver and numberlock
/usr/bin/xscreensaver &
/usr/bin/numlockx &

# Set BG image
/usr/bin/fbsetbg -f <path to image> &


# Start a panel
/usr/bin/fbpanel &
# /usr/bin/xfce4-panel &
# /usr/bin/perlpanel &

#Start Openbox
/usr/bin/openbox

---

### Post by WalmartSniperLX on 2006-10-15
> **bodhi.zazen said:**
> You need to find a panel you line and add it to the openbox start scripts.

My favs are pypanel, fbpanel, and perlpanel. fbpanel is NOT related to fluxbox.

~.config/openbox.sh:

Thanks :D

---

### Post by MaLek on 2008-04-28
idon't hv the path ~.config/openbox.sh
i hv only ~.config/openbox/rc.xml 
also can't find ~.theme 
i working in hardy now but i hd the same thing when i was in gutsy.
any help ?

---

### Post by urukrama on 2008-04-28
> **bodhi.zazen said:**
> You need to find a panel you line and add it to the openbox start scripts.

This was posted more than a year ago. This method is now very outdated. 

Current releases of Openbox make it a lot simpler. Whether you installed Openbox from the repos or from built it from source, you should have new sessions in GDM (press F10 to see them). Select 'Openbox' and it will run openbox-session, which launches Openbox and the autostart.sh file located in /etc/xdg/openbox/ (default settings) or /home/USERNAME/.config/openbox/ .

**MaLek:** Have a look at my Openbox guide. It should help you get started, and answer a lot of your questions. The link is in my signature.

---

