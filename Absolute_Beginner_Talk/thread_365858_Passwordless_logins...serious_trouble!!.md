---
title: "Passwordless logins...serious trouble!!"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by oceanspray on 2007-02-20
I stumbled across a site with tips and followed these instructions to allow me to login automatically since I am the only user of this computer: 

   1.  Open /etc/pam.d/gdm and before this line:

      @include common-auth

      add these three lines:

      # start enable passworldless logins
      auth sufficient pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers.txt onerr=fail
      # end enable passwordless logins

   2. Now create the file /etc/X11/gdm/nopassusers.txt and add the usernames of the users that you want to have passwordless logins, one per line.

Did all this exactly how it is spelled out BUT NOW I can't login anylonger, not as user, and neither as root. It gives me an "authentication failed" error each time.

What to do??

Thank You for any help you can give me :)

---

### Post by Rinzwind on 2007-02-20
Login under tty1 ((cntrl)-alt-f1)  and use vi or nano to re-edit those 2 files (or by copying over  the backup of those files).

Easy as pie ;)

---

### Post by oceanspray on 2007-02-20
It may be easy as pie, and I will try it, hope I understand you correctly, because I'm very new to Ubuntu/Linux.  I've never used vi or Nano. 

Thanks for helping!!

---

### Post by orb9220 on 2007-02-20
I just set auto-login in system>admin>login and there is a tab to let you set auto-login.

---

### Post by oceanspray on 2007-02-20
orb9220, thanks, is a bit late for me, but if it helps others, great :)

Anyway, I tried to do what Rinzwind said but am not expert enough, it didn't work, vi and nano have all kinds of options and I need more details as to how to do this.

Anyone?   (i installed and uninstalled, then reinstalled Ubuntu numerous times in the past week, am really committed on making it work!!)

---

### Post by george29 on 2007-02-20
Hi oceanspray,

when you say 'you tried what rinzwind said - but it didn't work' do you mean that you were not able to login? or that you were unable to change the files using nano?

for the login problem - if you have ubuntu liveCD boot into that and mount your partitions such that you can edit the files necessary to change back to the original configuration. you can google on how to do this from the liveCD.

with nano - for these files you'll probably need root access, so open the file using 

sudo nano /path/to/file

then edit as you want. to exit press (ctrl + X) and answer the questions (y or n) as you see fit.

hope this helps 

george.

---

### Post by oceanspray on 2007-02-20
George, let me first state that I am using a triple boot system (first hard drive XP and Ubuntu, and on the second hard drive I have Vista).   The reasons for many of the troubles i had with Ubuntu are because i want to set it up just so, like i did with XP.   I am stumbling a lot. :(

When I get to the login screen I used cntrl-alt-f1 which got me to the black text screen and it asked for my login and pw, which i provided (gave it my root/pw), i then typed in vi, and i had no idea what to do next, then restarted the computer and did it all over, trying Nano this time, its choices bewildered me and have no clue how to get this done.

Yes, i have a Ubuntu live cd.  

When I get to Nano, I just type this command: sudo nano /path/to/file ???

---

### Post by oceanspray on 2007-02-20
Thanks to all :)
After login (as root) I was able to delete the references by going to sudo nano /etc/pam.d/gdm .

Am soo glad, thanks again!!!

---

### Post by oceanspray on 2007-02-20
PS:

I used orb9220's suggestion and it worked like a charm.  After posing my question three folks replied and i was able to to fix this.  Each reply was very helpful to me.   This is a great community and if I had to give one reason why i opted for Ubuntu over any other distro it would be the good members of this forum.

Take care all =D>

---

### Post by george29 on 2007-02-20
Glad you got it sorted out.

would've replied earlier, but was out enjoying lunch.

for future reference you can use the 'man' command - which launches the manual page for the program you are trying to use... 

so in a console typing

$man nano 

would bring up a page explaining the use of nano. (well as long as the relevant man page is included with the distribution you are using).

George

---

### Post by oceanspray on 2007-02-20
Thanks for the heads-up :)

---

