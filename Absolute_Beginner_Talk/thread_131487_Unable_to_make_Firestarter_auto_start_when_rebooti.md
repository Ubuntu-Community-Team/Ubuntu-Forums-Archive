---
title: "Unable to make Firestarter auto start when rebooting :("
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by SMF on 2006-02-16
I have tinkered, tried and tested the Firestarter options so that it will launch automaticly upon starting my computer and login to ubuntu but it don't work. I have to do this manualy every time and enter my password before it will run.
Is there a work around to this? And or, is/are there any other firewalls for my ubuntu that you might suggest I try? Please advize.

Thank you.

---

### Post by kaamos on 2006-02-16
Hello!

Firestarter can be set to start up at boot in firestarter preferences. You won't get the panel icon at boot because that belongs to the gui part of firestarter. The firewall however is running.

The gui part of firestarter is needed only to look at logs and change the settings of the firewall.

---

### Post by Moebius on 2006-02-16
Here goes some advices for you.

Do not record the session with firestarter enabled

Add the following to /etc/sudoers
```
sudo gedit /etc/sudoers
```
```
your_username	ALL= NOPASSWD: /usr/sbin/firestarter
```

Add the following to System - Preferences - Sessions - Startup Programs
```
sudo firestarter --start-hiden 
```

And you should be set fine. If by any chance Gnome still complains about firestarter permissions it is very probable that you have a session saved with firestarted enabled.

---

### Post by SMF on 2006-02-16
[QUOTE=Moebius]Here goes some advices for you.

Do not record the session with firestarter enabled

Add the following to /etc/sudoers
```
sudo gedit /etc/sudoers
```
```
your_username	ALL= NOPASSWD: /usr/sbin/firestarter
```

Add the following to System - Preferences - Sessions - Startup Programs
```
sudo firestarter --start-hiden 
```

And you should be set fine. If by any chance Gnome still complains about firestarter permissions it is very probable that you have a session saved with firestarted enabled.[/QUOTE]

Ok kaamos your explination was clear thank you.

Moebius, you kind of lost me here:confused: do I use the terminal to input these codes? I am not sure where I am to use these codes. Sorry I am a big time lamer just posing and faking it until I make it:mrgreen: 
I know I shouldnt be so hard on myself :mrgreen:

---

### Post by Moebius on 2006-02-16
No problem.

Open a console and type
```
sudo gedit /etc/sudoers
```

At the end of the file add the following, replacing your_username with the username that you use in Ubuntu
```
your_username	ALL= NOPASSWD: /usr/sbin/firestarter
```

Then using the System menu, go to Preferences -> Sessions -> Startup Programs.

There click on Add and type the following
```
sudo firestarter --start-hiden
```

You should be set now. I only advise you not to record the session when logging off, it could mess those settings.

---

### Post by kaamos on 2006-02-16
[QUOTE=Moebius]No problem.

Open a console and type
```
sudo gedit /etc/sudoers
```
[/QUOTE]

Bad idea!! The sudoers file is not supposed to be edited like this because if you make a typo or something you could lose the ability to sudo thus making it kinda hard to fix that typo.

Instead use
```
export EDITOR="gedit" && sudo visudo
```
This checks that the file is ok before applying any changes.

---

### Post by missmoondog on 2006-04-10
you mean a typo such as the word "hiden" (hidden) in the startup programs tip? i realise that's not the sudoers list, but that's just how easy a typo is to do!

---

### Post by kent41 on 2006-04-10
I feel your pain SMF I had FIRESTARTER starting on boot up for weeks then one day it would not show up on the top panel. I've checked everything I did to make it start up on boot originality and all looked ok but FIRESTARTER was nowhere to be found. The best part of all of this is I have not made any  new install or changes.

Currently FIRESTARTER shows up in SYSTEM TOOLS > SYSTEM MONITOR but the GUI link is nowhere to be found.

I wish you good luck but but after reading other posts on FIRESTARTER it don't look good.](*,)

---

### Post by OffHand on 2006-04-10
[QUOTE=kent41]I feel your pain SMF I had FIRESTARTER starting on boot up for weeks then one day it would not show up on the top panel. I've checked everything I did to make it start up on boot originality and all looked ok but FIRESTARTER was nowhere to be found. The best part of all of this is I have not made any  new install or changes.

Currently FIRESTARTER shows up in SYSTEM TOOLS > SYSTEM MONITOR but the GUI link is nowhere to be found.

I wish you good luck but but after reading other posts on FIRESTARTER it don't look good.](*,)[/QUOTE]to start firestarter from the Terminal
```
sudo firestarter
```
And if it shows in your system monitor it is working.

---

### Post by kent41 on 2006-04-10
[QUOTE=subsonic_shadow]to start firestarter from the Terminal
```
sudo firestarter
```
And if it shows in your system monitor it is working.[/QUOTE]
If I start FIRESTARTER with **sudo firestarter** I then have multiple FIRESTARTERS running. There is more going on here than meets the eye.

If I look at current sessions I currently have  2 FIRESTARTERs running but no GUI available.

---

### Post by OffHand on 2006-04-10
[QUOTE=kent41]If I start FIRESTARTER with **sudo firestarter** I then have multiple FIRESTARTERS running. There is more going on here than meets the eye.

If I look at current sessions I currently have  2 FIRESTARTERs running but no GUI available.[/QUOTE]
Did you try to re-install firestarter through the Synaptic?

---

### Post by kent41 on 2006-04-10
If you look at some other post on Firestarter un-install you will see it is not that simple to un-install.
According to the post the un-install does not un-install everything. You must go in and manually remove Firestarter associations.

I am afraid to un-install Firestarter in fear something else will not work. 

The BIG question is why did firestarter work and then for no known reason it quits. 

You know it is starting to get very old to repeatedly to re-install apps that have already been installed and working.

---

### Post by OffHand on 2006-04-10
Pick 'Mark for re-installation' in the synaptic.
This shouldn't give any problems as far as I know.
(I had to re-install it myself once)

---

### Post by kent41 on 2006-04-10
[QUOTE=subsonic_shadow]Pick 'Mark for re-installation' in the synaptic.
This shouldn't give any problems as far as I know.
(I had to re-install it myself once)[/QUOTE]
OK subsonic_shadow since you took the time to help I went to synaptic and Marked Firestarter for re-install and it installed and I can run it , however the little blue ball on the top panel is still empty. It seems maybe I saw where you can create the link on the top panel but I can't remember were or how to create it.

Thanks again maybe someone will read this and remember how to create the blue ball icon on the top panel when Firestarter is running. You can just click on the blue ball and the GUI will open up.

---

### Post by OffHand on 2006-04-10
Can you go to preferences > interface and check settings for system tray.
You might need to enable it there.

---

### Post by kent41 on 2006-04-10
[QUOTE=subsonic_shadow]Can you go to preferences > interface and check settings for system tray.
You might need to enable it there.[/QUOTE]
Yes the box is checked for **enable tray icon** but no icon shows up, but it used to. surely someone knows why the icon is not on the top tray.

EDIT: Some post call the blue icon a Play Button on the top tool bar. The Blue icon turns red when Firestarter stops a intrusion or other problem it sees. But where is the Blue icon - There must be some code that places it on the tray.  

Oh by the way now when I reboot after the re-install I get the message not enough priv and I have to start the GUI with a terminal or use **Application>System Tools>Firestarter**

---

### Post by OffHand on 2006-04-10
I can't help you any further. At least you have the GUI now and a working Firewall. IMHO the tray icon is annoying anyways  ;)

---

### Post by kent41 on 2006-04-10
[QUOTE=subsonic_shadow]I can't help you any further. At least you have the GUI now and a working Firewall. IMHO the tray icon is annoying anyways  ;)[/QUOTE]
Thanks much for sticking with me. Kent41

---

