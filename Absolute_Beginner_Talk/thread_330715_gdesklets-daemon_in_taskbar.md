---
title: "gdesklets-daemon in taskbar"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by johnnyloot on 2007-01-03
Hey guys,
I just installed gdesklets on my gnome Edgy. 
After getting all of the desklets all setup the way I like (Using Kevin Kanes cpu/mom/eth/hd monitors) I noticed that upon reboot, two of them are listed as gdesklets-daemon in the program list. I find this really annoying because it should not be taking up that space.

I tried killing them and putting them in again and it still doesnt seem to work.
The only idea I had was that when the desklets are clicked on, they try to run xterm, should I allow this or not? Is this related to the problem.

Any help getting rid of them would be appreciated, thanks a lot.

---

### Post by 7Notes on 2007-03-26
Hi Johnnyloot - you ever solve this? I've just come across the same problem and it's annoying me too!

---

### Post by compmodder26 on 2007-03-26
Are you by chance running beryl as well?

---

### Post by genfish on 2007-03-27
Hi,

I am having this same problem on two machines which are both running beryl as well as gdesklets. An item appears in the window list with the title gdesklets-daemon.

Anyone know of a fix for this?

Thanks

---

### Post by compmodder26 on 2007-03-27
This is a known issue between beryl and gdesklets.  I'm not sure if there are any bug reports on it.  I fixed my problem by making the following executable script:

```
#!/bin/bash
gdesklets
sleep 5
beryl-manager
```

I then added it as a startup script in my gnome session.

---

### Post by genfish on 2007-03-28
thanks for the reply, ill give it a shot when i get home tonight

---

### Post by genfish on 2007-04-03
worked a treat, easy fix until its updated in the future, thanks

---

### Post by Jump on 2007-04-10
I need to fix this one as well. How do I make this a startup script?

---

### Post by FotoPhocus on 2007-06-07
Go to the System Menu --> Administration --> Sessions

There, you can add this script to your startup items.  It was probably obvious to the vets out here that this executable script launches gDesklets and Beryl, but I made the newbie mistake of not unchecking the separate boxes for those two programs in Sessions, so this script didn't do any good.  Make sure you uncheck the individual boxes for Beryl and gDesklets (if they are in there), because the executable script will launch them both.

Sorry for bringing up an old thread or if this was obvious... but if I made the mistake, I figured other newbies might too :)

---

### Post by CaptainInsaneO on 2007-06-25
Here's a full tutorial (this is how I did it) on how to fix this ever-annoying problem:

Go System-->Preferences-->Sessions

Uncheck Beryl and Gdesklets startup buttons.

In the same window, click "New", under Name type

```
Beryl Fix
```

for the command, type

```
/etc/init.d/beryl_fix
```

Click OK and then check the box next to "Beryl Fix".

Open terminal, type

```
sudo gedit /etc/init.d/beryl_fix
```

Copy and paste compmodder's EXCELLENT fix for this problem:

```
#!/bin/bash
gdesklets
sleep 5
beryl-manager
```

I just used "beryl" instead of "beryl-manager"... whichever one works for you, go with. I personally prefer a tidy taskbar, so that's why I just typed beryl.

Save the file and exit gedit.

Now, in terminal, type

```
sudo chmod +x /etc/init.d/beryl_fix
```

to make it executable.

Then type

```
sudo update-rc.d beryl_fix defaults
```

for proper runlevels (default on boot, etc.)

You are done! Press Alt+Ctrl+Backspace to restart X and see your handy work!

---

