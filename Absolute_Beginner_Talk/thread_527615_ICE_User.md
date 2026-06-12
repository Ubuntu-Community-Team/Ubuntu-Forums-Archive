---
title: "ICE User?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-08-16
hey,

When I started Ubuntu 6.10 EE it said that my last session lasted less than 10 seconds. Upon opening up the detail tab it said that it could not access a permission file (.ICE or something)

what should I do?

thanks!!!! (panics)

---

### Post by diatribe on 2007-08-16
so are you able to log into X?

---

### Post by JasonBourneLinux on 2007-08-16
nope

---

### Post by diatribe on 2007-08-16
then we need to know specifically what file it is looking for

---

### Post by JasonBourneLinux on 2007-08-16
it says unable to lock ICE authority file /home/ubuntu/.ICEauthority

---

### Post by diatribe on 2007-08-16
when it dumps you to the terminal type:

cd /home/ubuntu
ls -a .ICE*

and see if it exists. if it doesnt, type 
touch .ICEauthority

if it does exist type
mv .ICEauthority ICE

and retry

---

### Post by JasonBourneLinux on 2007-08-16
thanks! (Havent tried it yet- but thanks for the advice!)

---

### Post by diatribe on 2007-08-16
not a problem, let us know if it works

---

### Post by JasonBourneLinux on 2007-08-19
didnt work

---

### Post by Nephron on 2007-08-27
I encountered this problem as well, but managed to find a solution.

I modified what was done [here]("http://andocs.wordpress.com/2007/06/05/ubuntu-iceauthority-problem/").

First get to a terminal (Ctrl+Alt+F1).

Log in.

Verify that you have the .ICEauthority file:
> ls -a
Look for the file, if it is there you can fix this.

Now you must edit the file /etc/gdm/Xsession.
> sudo nano /etc/gdm/Xsession
The "nano" editing interface will pop up.

Add these lines right under the "PROGNAME = Xsession" line:
(replace YOURNAME with your user name)
> ICEAUTHORITY=”/home/YOURNAME/.ICEauthority${root}”
export ICEAUTHORITY

Save it (press Ctrl+o then enter)
Exit (Ctrl+x)

Go back to your login screen (Ctrl+Alt+F7) and try to log in.

Hope it works for you.

---

### Post by mandras on 2008-06-01
I got the same problem, and I've been looking all over the internet, but nothing worked except your solution! So thank you a hundred times!!! I'm very glad, because I was so confused that I was thinking about reinstall ubuntu. I'm glad, that there is no need for that!!! :D 
Thank you again!

---

