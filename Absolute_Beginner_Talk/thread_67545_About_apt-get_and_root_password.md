---
title: "About apt-get and root password"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by Carl0s on 2005-09-20
first , how can i change the way that apt-get downloads the files? Now when i'm trying to install irssi-text, i got "error message" "inster ubuntu installition cd...". I remember that on knoppix, user can chose where apt-get takes the files.

Second, How can i find out my root password? during installition installer didint ask me, what i would like to bee the root password. So, where, and how i can setup the password.



sry about my bad language, "london" aint my best language... :)

---

### Post by UbuWu on 2005-09-20
[QUOTE=Carl0s]first , how can i change the way that apt-get downloads the files? Now when i'm trying to install irssi-text, i got "error message" "inster ubuntu installition cd...". I remember that on knoppix, user can chose where apt-get takes the files.
[/QUOTE]

Remove the cd from synaptic -> preferences -> sources.

---

### Post by Carl0s on 2005-09-20
There is no "source" in synaptic preferenses.  :(

---

### Post by SilentCacophony on 2005-09-20
Hello. Ubuntu does not use the root account, but uses sudo instead. Just place *sudo* before the command that needs root access, and it will prompt you for the normal password you set up.

EDIT:

On my setup, you can go Settings -> Repositories, and remove the CD option there.

Also, there is gksudo if you need an X password prompt requester.

---

### Post by mlomker on 2005-09-20
[QUOTE=Carl0s]There is no "source" in synaptic preferenses.  :([/QUOTE]

You can edit the /etc/apt/sources.list file.  The CD is normally on the first line.

---

### Post by karuptdata on 2005-09-20
there is a way to enable the root login as well as change root password....open up terminal and first type sudo passwd root.. it will then prompt you for a new password..once that is completed then type in sudo gdmsetup and under the security tab there will be a box that says allow root to login with GDM check that box and close gdm. Logout and then you can login to root user from GDM if you prefer!

---

### Post by az on 2005-09-20
[QUOTE=karuptdata]then you can login to root user from GDM if you prefer![/QUOTE]


Ooo.  Why would you want to do that?  Ubuntu goes out of it's way to provide the security as well as the ease of use of not using a root account.

Carlos, how did you enable the other repositories so that you can install iirsi-text?  Use that same method to remove the cd as a repository.  Update, and you should be good to go.

---

### Post by Carl0s on 2005-09-20
No the apt-get takes the pakkages from internet, and the familiar "su" works. Thanks to everybody who awnsered :)


(i'm positive suprised about how fast can get help.  whit windows problems it takes atleast one day  to get help :) )

---

### Post by mlomker on 2005-09-20
>  Logout and then you can login to root user from GDM if you prefer!

For the record, you can also Ctrl-Alt-F2 over to another terminal and login as root.  If you type **startx** it'll boot into KDE as root.  I've only done that on a few rare ocassions.

---

### Post by karuptdata on 2005-09-20
AZZ & Mlomker you never let me down providing knowledge everyday....:) I never said it was the safest thing to log into root however i have numerous friends that just prefer it that way because its less of a hassle?  LOL

---

### Post by UbuWu on 2005-09-20
[QUOTE=Carl0s]There is no "source" in synaptic preferenses.  :([/QUOTE]

Sorry, translated from Dutch. It is probably repositories.  :wink:

---

### Post by mlomker on 2005-09-20
>  never said it was the safest thing to log into root however i have numerous friends that just prefer it that way because its less of a hassle?  LOL

You can do that too.  Open the /etc/kde3/kdm/kdmrc file and change this line:

```

AllowRootLogin=false

```

---

