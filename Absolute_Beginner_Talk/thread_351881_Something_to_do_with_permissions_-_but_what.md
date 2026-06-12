---
title: "Something to do with permissions - but what"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by thompa on 2007-02-02
Hi there,

Having a problem right now with changing settngs and the settings not being saved... I am sure that it is something to do with permissions - but what, I don't know :-((

I have checked where I can that I have write permissions.. but I am not sure about accessing 'root'....

When I booted the machine the wireless network wasn't recognised so I went into Network Settings and although I reset the configuration the settings weren't saved when I exited and reopened. It is running now - but the Network settings window is open.

Also having a problem with the printer not keeping it's newtork status - it is set to local right now and I want it to work on the network.

thanks in anticipation

Allan

---

### Post by l951b951 on 2007-02-02
> **thompa said:**
> Hi there,

Having a problem right now with changing settngs and the settings not being saved... I am sure that it is something to do with permissions - but what, I don't know :-((

I have checked where I can that I have write permissions.. but I am not sure about accessing 'root'....

When I booted the machine the wireless network wasn't recognised so I went into Network Settings and although I reset the configuration the settings weren't saved when I exited and reopened. It is running now - but the Network settings window is open.

Also having a problem with the printer not keeping it's newtork status - it is set to local right now and I want it to work on the network.

thanks in anticipation

Allan

From the terminal, sudo chmod 777 /YOURDIRECTORY/YOURFILE 
use your path instead of the capitalized one I show.  This will let everyone read/write/execute the file.

A smarter way is from the terminal, sudo gedit /YOURDIRECTORY/YOURFILE
this opens the file with root permissions.  then you can edit it and save it while you are the superuser.  However, you are not changing the permissions, so if that is your goal use the first.

**EDIT:**  After re-reading your post, it looks like you are using a GUI.  I'm not sure which program you are using that has "Network Settings" I couldn't find it on my machine.  If you can find the runline command for it you can run the gui in superuser mode by using # gksudo COMMAND  .  So if you wanted to open nautilus with root permission, you would run #gksudo nautilus .

---

### Post by thompa on 2007-02-02
Hi again,

Problem is.. I don't know what 'YOURIRECTORY' and 'YOURFILE" are...

I thought that I had changed permissions in ROOT to let me proceed and I rebooted (not sure I needed to do that but I have to do that often in Windows sooo,,,)

Booted ok, but there was a message which I don't fully understand...:-

*'Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by others'*

I don't know what the Network settings file is or how to find it - feeling pretty inept right now!

I get to the Network settings by using the GUI... System/Administration/Networking and this shows no entry in location but otherwise shows the wireless connection active.. although it isn't!

I change the location to my machine name and the windows tells me it is changing the profile which eventually happens... but the wireless connection is now 'not configured'!
So, I enter the Properties screen and 'enable the connection' all of the greyed out data appears bold and the wireless connection is made.

As before, the wireless connection keeps operating as long as the Network settings window is open - as soon as I close it the connection is lost...

Still seems odd that I can't correct this issue using a GUI.... the command line just seems to me like going back to DOS! I know that it is powerful - but one typo and zilch... and then you have to learn all of the nemonics and their usage. Took me years to learn DOS before Windows was stable and I don't really think thta it is a good idea for me to start over!

---

