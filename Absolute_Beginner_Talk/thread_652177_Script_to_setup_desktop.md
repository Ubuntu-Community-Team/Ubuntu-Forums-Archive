---
title: "Script to setup desktop"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by ae804 on 2007-12-28
So I'm trying to write a script that will initialize my desktop.  It'll do some of the following (and probably more once I understand everything that is going on)

```

#!/bin/bash

#Move to workspace 0 and open terminal in fullscreen mode:
wmctrl -s 0
gnome-terminal
#???(need to "hit" F11 on the keyboard or maybe there's a -? I could use to open full screen)

#Move to workspace 1 and open Firefox
wmctrl -s 1
firefox

#Move to workspace 2 and open audio player
wmctrl -s 2
amarok

#Start Beryl manager
beryl-manager
```

That's as far as I've gotten so far.  If anyone could tell me how to put this in the correct run level (I believe I want this to run at log in, so RL 2?)--Also any help filling in the last couple unknowns would be helpful.

Thanks,
AE

---

### Post by nathandelane on 2007-12-28
Runlevel directories are located in the /etc/ directory. If you are running Desktop, which you are, you need to copy your script into the rc2.d directory under /etc/. Open up a teminal (from the System menu) and go to where your script is located. If it is in your home directory, then you'll probably already be there, but to be sure type:

cd ~

and press Enter

This will take you to your home directory.  Then to copy your script to the /etc/rc2.d directory, let's say your script is called setup_desktop.sh, type the following:

sudo cp ./setup_desktop.sh /etc/rc2.d/setup_desktop.sh

When you are prompted for a password type your user password.  Next browse to the /etc/rc2.d directory:

cd /etc/rc2.d

Then make your script executable:

sudo chmod + x ./setup_desktop.sh

And your done.  That's how you should do it in theory - but I don't know how to ensure that it runs after your GNOMe or KDE starts up.

Nathan

---

