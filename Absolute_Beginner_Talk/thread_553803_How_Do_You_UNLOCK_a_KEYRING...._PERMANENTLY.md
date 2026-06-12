---
title: "How Do You UNLOCK a KEYRING.... PERMANENTLY?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-09-18
Hello....

Each time I start-up my machine I keep getting the following message:


Unlock Keyring

Enter Password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked


I believe this is being asked because when I installed a restricted device (wifi adapter) it asked me at that time to create a password etc....

Anyway, I'd like to know if I can somehow unlock permanently this keyring so that I don't have to keep entering a password each time I start-up my pc.


Thank You

---

### Post by justleen on 2007-09-18
Install PAM Keyring:

    sudo aptitude install libpam-keyring

Configure PAM Keyring:

    sudo gedit /etc/pam.d/gdm

&#8230;add the fllowing line at the end of the conf file:

    @include common-pamkeyring

---

### Post by ThrobbingBrain66 on 2007-09-18
Use justleen's advice.  However, keep in mind that if you currently use the auto-login feature, you won't be able to use it anymore.  For the pam-keyring workaround to work, you have to supply your username and password at the login screen.

---

### Post by James7 on 2007-09-18
i read in another thread that they will in gutsy have it so that once you log in normally your keyring will automatically be logged in too. :D

---

### Post by ThrobbingBrain66 on 2007-09-18
Yup, that feature was just added in the last day or two.

---

### Post by saeedk on 2007-09-18
> **justleen said:**
> Install PAM Keyring:

    sudo aptitude install libpam-keyring

Configure PAM Keyring:

    sudo gedit /etc/pam.d/gdm

…add the fllowing line at the end of the conf file:

    @include common-pamkeyring

I have the same problem!

I have done what you proposed and still have the same problem :confused:

---

### Post by steeef on 2007-10-22
I'm using Gutsy on a fresh install, and I see no option to automatically unlock my keyring. I even deleted the login keyring and it still didn't work. Help!

---

