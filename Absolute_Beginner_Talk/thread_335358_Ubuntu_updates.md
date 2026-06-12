---
title: "Ubuntu updates"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Prime_Numbers on 2007-01-10
When I logged in this morning, I noticed that there is an update available.  When I clicked on the small icon, I was prompted to enter my password, which I did.  Then the update window popped up but, I got an error message saying that only one software manager should be running at a time.  To my knowledge Im not running anything else.  Does anyone have any suggestions?

---

### Post by navneeth on 2007-01-10
Perhaps you were using apt-get or aptitude from the terminal at the same time?

---

### Post by AlanRogers on 2007-01-10
Are you sure you didn't double-click and fire up two instances?

---

### Post by nsleiman on 2007-01-10
go to the konsole and type:

ps aux | grep 'username'

u will be able to see if any apt* is hanging , after this kill -9 pid#

'username' is the user login u are using and pid# is the number (maybe 4 digits)

---

### Post by Prime_Numbers on 2007-01-10
How will I know if Im using apt-get or aptitude?

---

### Post by navneeth on 2007-01-10
Did you enter any commands similar to the ones below just before opening the update manager?

sudo apt-get update

sudo apt-get dist-upgrade

sudo apt-get upgrade

sudo apt-get install 'program name'

(or aptitude in place of apt-get in any of the above)

---

### Post by Prime_Numbers on 2007-01-10
> **navneeth said:**
> Did you enter any commands similar to the ones below just before opening the update manager?

sudo apt-get update

sudo apt-get dist-upgrade

sudo apt-get upgrade

sudo apt-get install 'program name'

(or aptitude in place of apt-get in any of the above)

No I did not.  I was trying to do it by clicking on the orange update icon on my task bar.

---

### Post by xyz on 2007-01-10
I get this when I try to install/update stuff via a terminal (sudo aptitude...) while forgetting that my Synaptic window is open. I close the window.

---

### Post by Prime_Numbers on 2007-01-10
> **xyz said:**
> I get this when I try to install/update stuff via a terminal (sudo aptitude...) while forgetting that my Synaptic window is open. I close the window.

Hmmm...  I dont have anything else open

---

### Post by xyz on 2007-01-10
How long has this been going on?
It may also be that Update Manager is working "in the background"...meaning that it's busy fetching new updates which could explain the "another program is running."

---

### Post by Prime_Numbers on 2007-01-10
> **xyz said:**
> How long has this been going on?
It may also be that Update Manager is working "in the background"...meaning that it's busy fetching new updates which could explain the "another program is running."

Ok, I know that I have my settings set up to check for updates daily.  Maybe this has something to do with it.  I will have to check when I get home tonight.  Thank you for your help.

---

### Post by xyz on 2007-01-10
OK then let's see if it's that simple...hopefully!!
Good luck and let us know how it goes.
See you.

---

### Post by scrooge_74 on 2007-01-10
Someone had a similar problem a while back, the update manager was not working right, I have mine to only check once a week and from time to time I check manually

sudo apt-get update
sudo apt-get upgrade

and that's it

In your case it was probably running in the background doint who knows what

---

