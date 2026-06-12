---
title: "Firestarter won't work"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by Janzuka on 2006-01-19
I had to reinstall ubuntu, and before that firestarter worked just fine. I got via apt-get , and immediately it appeared to the system tools menu. But now i've tried to get it via synaptic and via apt-get. I even tried automatix, it just won't work. Everything seems to be okay, but it will not appear to the system tool, and when i try to open it by typing "sudo firestarter" in terminal, it tells me that no such directory or file exists. Still it pops up this firestarter wizard, but the program itself won't start. What's wrong?

---

### Post by bscbrit on 2006-01-19
Well, from what you have said it appears that your assumption is not quite correct.  It is wrong to say the 'Firestarter won't work' but rather 'Firestarter won't install'.  So lets try to find out why not...

The first clue that it won't install is that, when you try to run it, you get the error message that the file or directory is not found.

Open Synaptic, select search and type in firestarter.  If it doesn't find the appropriate files to install it is probably a problem with your repositories.  Make sure that all repositories are selected as active. e.g. open Synaptic -> Settings -> Repositories -> Settings and check that 'Show disabled software sources' is selected.  Then make sure that they are all selected in subsequent displays.

Try to re-install again and, when installation is complete, try the following commands in a terminal window:

sudo find / -name 'firestarter*'

or 

which firestarter


if neither provide an answer then Synaptic failed to install them.  Come back here and we can look at possible reasons why that might happen.

If 'firestarter' is found, then type the full path (e.g. sudo /usr/sbin/firestarter and let us know what error messages are displayed, or what is seen on the screen.

:p

---

### Post by bscbrit on 2006-01-19
Looking at your original post again, what do you mean exactly by ' it pops up this firestarter wizard, but the program itself won't start.'  Either the program is starting or it is not.  What did you expect to see and what did you actually see?

---

### Post by Janzuka on 2006-01-20
Thanks fot the advice, even though i did not manage to get it work. Well bscbrit at first about your second post: it pops up the wizard but after all the wizard settings are made, i cannot press the forward button. I tried both of the commands and yes, firestarter was found, so i believe it is somehow installed.  A bunch of errors like this #Error reading file /etc/firestarter/inbound/allow-from: Tiedostoa tai hakemistoa ei ole
 are displayed (if it's any use i'can post all of them in here, but they were pretty similar to each other, so i thought it wouldn't be necessary) and the two last lines are the following 
Warning: External interface previously configured not found

Warning: Internal interface previously configured not found

Thanks for your patience.

---

### Post by bscbrit on 2006-01-21
This appears to be a corrupt installation.  Try removing it using Synaptic and then re-install it again.

---

### Post by Janzuka on 2006-01-21
Probably it was, because it finally works. I have no idea, why it didn't install it properly   during those other times i installed it. I did nothing differently this time :o  But now it works fine. Thank you again very much bscbrit!

---

