---
title: "What happened to my ubuntu interface?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-04
So my synapytc wasn't opening so I decided to logout and log back in. But the logout went on forever so I ctr-alt-bcksp and got into a black screen terminal. The I restarted the computer and got the same interface. How do I get back to my ubuntu interface (ie. my light brown login page)?

Thanks,
Chris

---

### Post by harisund on 2006-05-04
If you are rebooted back into the console, I would suggest you try and do ```
sudo invoke-rc.d gdm restart
``` and check if you can get a login screen. 

If not ```
startx
``` should get you your ubuntu interface

---

### Post by cl3ellio on 2006-05-04
I've tried both, with "sudo invoke-rc.d gdm restart" I get the following message:

Starting GNOME Display Manager...           [fail]

and then I'm kicked back to the command line. The with startx I get the following error ms:

xauth: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

---

### Post by cl3ellio on 2006-05-04
A little bit more on my problem, if I try and start the gdm with:

sudo gdm

And I get the following error:

gdm: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

So I'm thinking thats there's a problem with xlib11, but I'm not too sure how to fix it? Should I just reinstall ubuntu?

---

### Post by nalmeth on 2006-05-04
maybe a previous download of those libraries was interupted, and you just have broken files.
In that command line, give:
sudo apt-get update
sudo apt-get upgrade
sudo reboot

and try the previous steps again

---

### Post by cl3ellio on 2006-05-04
Well I'm still having the same problem. When I ran 'sudo apt-get upgrade' I had unmet dependencies on the following packages:

geomview (the root of my pain!)
lesstif-bin
libx11-6
motif-clients

I then restarted it, but trying the previous steps provided the same results as previously mentioned.

---

### Post by nalmeth on 2006-05-04
ok, we're getting somewhere then try 
sudo apt-get -f install
to try to resolve the unresolved dependencies

---

### Post by cl3ellio on 2006-05-04
Its all good!! Works like a charm, so does geomview!! 2 birds with one stone... Thanks for the quick reply... My condolences on the Falmes, I lost the Habs last night, its quite the rollercoaster!
Cheers

---

### Post by nalmeth on 2006-05-04
[quote=cl3ellio]Its all good!! Works like a charm, so does geomview!! 2 birds with one stone... Thanks for the quick reply... My condolences on the Falmes, I lost the Habs last night, its quite the rollercoaster!
Cheers[/quote] :cry:

Yes I felt for les canadien aswell, it's a sad state of affairs.
Trying to keep busy and take my mind off of it
Glad you're all fixed up tho!

---

