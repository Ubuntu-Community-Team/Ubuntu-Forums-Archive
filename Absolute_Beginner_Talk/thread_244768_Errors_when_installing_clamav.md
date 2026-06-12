---
title: "Errors when installing clamav"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by DeathOnJuice on 2006-08-26
Hey, everyone. I just installed clamav and firestarter from Synaptic, and when the installation was done I got a little box of errors. It had several line of something about dependency errors for clamav, but I don't believe there was anything else. I selected it all, hit Control-C and closed it, but it apparently didn't copy :( . So, what does this mean? I believe the only things it installed for clamav were clamav, clamav-base, clamav-freshclam, and libclamav1. Was it supposed to install more or less? Will I be protected?

Thanks!

---

### Post by Schalken on 2006-08-26
You really don't need an antivirus program for Ubuntu, there are very few *serious* viruses for Linux. AFAIK Clam AV was mainly designed for servers to stop viruses for *other* operating systems going through it.

If you want clamav anyway, you can find what packages clamav is missing by going into Synaptic, clicking the 'Custom' button in the bottom left and selecting 'Broken' in the left pane.

---

### Post by DeathOnJuice on 2006-08-26
I know that viruses are very, very few in Linux, but why not run an AV?

Also, there are no broken packages listed in Synaptic. Odd...

By the way, thanks! Also, any other ideas, or should is it working?

Actually, I think I'll delete it and just keep firestarter. It says that the version of clamav is out of date when I try to update, even though it's the newest on Synaptic, and I don't really want to compile it from source because then it will be hard to remove.

IMPORTANT: When I remove it from Synaptic, should I do remove or remove completely? What's the difference?

---

### Post by DeathOnJuice on 2006-08-26
Bump.

---

### Post by Kilz on 2006-08-26
> **DeathOnJuice said:**
> I know that viruses are very, very few in Linux, but why not run an AV?
The anti virus for linux isnt quite the same as anti virus for Windows. It wont run all the time, most of them are command line scanners. In other words you have to tell the application to scan a file or group of files with a command in the terminal. or a mail server can be set to scan incoming attachments.
Most people think its a waste of time, so it just takes up space.If you feel safer with one, go ahead, but I bet you stop using it in a few weeks. 

> Also, there are no broken packages listed in Synaptic. Odd...

By the way, thanks! Also, any other ideas, or should is it working?

Actually, I think I'll delete it and just keep firestarter. It says that the version of clamav is out of date when I try to update, even though it's the newest on Synaptic, and I don't really want to compile it from source because then it will be hard to remove.

IMPORTANT: When I remove it from Synaptic, should I do remove or remove completely? What's the difference?

Remove will remove the application, remove completly will remove the application and any other files you have added since installing it like config files. Since you just installed it, it doesnt matter.

---

### Post by DeathOnJuice on 2006-08-26
Alright, thanks! I'm going to go ahead and delete clamav.

That's one problem solved. Now, I need to fix my other problem here:

[http://www.ubuntuforums.org/showthread.php?p=1427171#post1427171](http://www.ubuntuforums.org/showthread.php?p=1427171#post1427171)

Then, everything will be good :) .

---

