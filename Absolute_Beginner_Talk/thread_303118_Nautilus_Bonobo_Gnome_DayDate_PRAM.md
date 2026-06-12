---
title: "Nautilus Bonobo Gnome Day/Date PRAM"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by Radiolad on 2006-11-19
[COLOR="Black"]Well, I thought I had resolved the Day/Date bug using the fix as shown below** which works fine.
I have replaced the old battery (3.6 volt 1/2AA type) with a brand **_new _**one (tested and giving a healthy 3.6 volts as opposed to Nil on the old battery)
I restarted the iMac and used the bug fix (below) to initially set the Day/Date. Ubuntu came up great. I went into the Day/Date option (windows style) just for 'comfort' to see all was well which it was. I then shut-down the iMac, waited for a couple of minutes and switched it back on hoping to sail through into Ubuntu. NO SUCH LUCK...the same errors came up on screen as per before! I.E. [/COLOR]
[COLOR="DarkGreen"]-Nautilus can't be used now, due to an unexpected error from Bonobo when attemping to register the file manager view server
Error
-There was a problem registering the panel with the bonobo activation server
-The error code is 3
-The panel will now exit
Error
-There was a problem starting the GNOME Settings Daemon
-Some things such as themes, sounds or background settings may not work correctly.
-The Settings Daemon restarted too many times [/COLOR]

**So can anyone help ... please**

[COLOR="Indigo"]_BUG FIX **_:-
Boot to the point of the brown screen, then press crtl+alt+f1 (ctrl-option-F1 on a Mac) to get a terminal, and log in. Type:
date
if you get something like
Fri Jan 11 19:11:32 GMT 1970
then run the command
sudo date -s "Fri Nov 11 19:11:32 GMT 2005"
(you will need to put in your password)
now do the command
sudo /etc/init.d/gdm restart
and hopefully you can log in[/COLOR]

  Thanks for reading and hope you can help... Radiolad

---

### Post by Radiolad on 2006-11-20
Hi, With much thanks to **LINEAR **for providing a link to the fix.
    [http://www.macosxhints.com/article.php?story=20060814075952448]("http://www.macosxhints.com/article.php?story=20060814075952448")

I've tested the iMac on 'Restart' and 'Shutdown' and the Day/Date is finally remembered giving me a faultless boot into Ubuntu.

 Thanks again LINEAR,     Regards, Radiolad :-D :-D :-D

---

