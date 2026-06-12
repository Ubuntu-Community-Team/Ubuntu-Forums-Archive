---
title: "replacing a user's home folder at login"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by clutch68rs on 2007-11-02
Hi all,
I'm interested in deploying Ubuntu in a public library to replace aging Windows boxes.  Ubuntu fits the bill functionally, we love it.  We're trying to test a few desktops out in a public environment, and a few questions have been raised.

A public user account has been created and the desktop, browser, printers, etc. have all been configured for a public user (Gutsy w/ Gnome:  the new Gnome is amazing, by the way!).

These public user profiles get screwed with constantly.  Every changeable aspect of the UI will get altered sooner or later, and short of running a thin client kiosk (a la LTSP) we were wondering if the user's /home folder could simply be re-populated, at login, with the contents of the clean user we originally configured.  In essence, loading a clean profile (home folder) each time the user logs in or is automatically logged in, mimicking mandatory profiles in Windows.

So, I have 2 directories in /home: /home/public_user and /home/public_clean.  Is it possible to use a script to replace the public_user folder contents with the contents of public_clean, giving a "clean" environment to the next patron that logs in?  I've tried a few basic home-rolled scripts but run into errors here and there, not having much experience in this area.

We're aware of Pessulus and Sabayon, neither of which locks this user down to the degree we need.  We're set on using Gnome, as well, we're not too interested in going with KDE, it just hasn't worked well for us in the past.

I'm excited to offer this to the public and finally get these libraries moved away from Windows, but if I can't guarantee the staff that every time they log a public computer in that the environment will always look the same, I can't sell it to the powers that be.

Any help will be greatly appreciated!

---

### Post by w7kmc on 2007-11-02
Try  this procedure:

1. Set up the account just they way you like.

Then tar up a default configuration from the command line:

1. cd /home
2. sudo tar czvf public_clean.tgz  public_home


Your restore file is called public_clean.tgz and reside in /home
Enter the following into a script called restore_public_user.sh:

#!/bin/bash
# Restore script for "publc account"

cd /home
rm -Rf public_home
tar -xzvf public_clean.tgz
chown -R public_home:public_home public_home
exit

###End of script


You should run it from some admin type account other than public_home from the command line using sudo:

ex.
sudo restore_public_user.sh

There may be other more elegant approaches..I assumed the login for the account was public_user when I ran the chown command...here substitute the real user ID to change to the correct file owenership

like    chown -R guest:guest  public_home

Good Luck...

---

### Post by clutch68rs on 2007-11-05
w7kmc,
Thank you for that advice.  I look forward to giving this a try on Monday and I'll post my progress.  Thanks again!

---

### Post by clutch68rs on 2007-11-06
w7kmc,
Your advice and script worked flawlessly.  Thanks so much for the help.  Hopefully your post will help others who are thinking of using Ubuntu in a locked-down public environment :)

---

### Post by w7kmc on 2007-11-08
Thanks,

There may be a way to write this into a script and include it as part of public_user's logout script. I am just not too sure on how to do this though.

---

### Post by clutch68rs on 2007-11-08
To keep things simple for staff we just run the script at boot.  When in doubt, they simply reboot in between users.  

This is precisely what we needed, and works perfectly.  We rolled out a few test boxes today, with many more to follow if all goes well (and I feel it will).

Thanks again for the recipe...I'm going to try another of yours this weekend (grilled salmon)

---

### Post by hyper_ch on 2007-11-09
glad this is already solved :)

How many boxes are you using on ubunt now? (Just out of curiosity)

---

### Post by clutch68rs on 2007-11-09
Right now we have a dozen rolled out between 2 sites.  That number will increase to ~100 soon, across 8 separate libraries.

---

### Post by psusi on 2007-11-09
The chown is not needed since when tar is run by root, it extracts the files using the permissions stored in the tar file, so they will be owned by whoever owned them when you tared them up.

---

### Post by w7kmc on 2007-11-09
This sounds like an exciting project. I'm interested in hearing how it turns out, especially when someone (a library user off of the street) use Ubuntu for the first time, and what their reaction would be after using it. Have you had any feedback yet?

As for the chmod psusi...you're probably right, the chmod is not needed....I was not sure though  and thought that there may have been a permissions problem...but no worries! 

This is a great way to promote Ubuntu!

---

### Post by clutch68rs on 2008-02-28
Sorry for the late post, I must have missed the email notification.  This script setup has worked perfectly, and we're migrating public computers off of Windows 200/XP/Active Directory, onto Ubuntu Gutsy, at the rate of about 7 computers per week (I'm the only IT guy).

We're using this setup for both kiosk-type internet terminals with openoffice and a few other productivity/multimedia apps, and we're also using them as locked-down terminals to browse only our online library catalog.

It works great.  It's faster, more reliable, and easier than trying to maintain a Windows domain across a geographically diverse consortium of libraries and I was not looking forward to Vista in a public environment.  I couldn't be happier, and the help on this thread was invaluable.

I know I'm not the only library employee out there who had this question:  perhaps I should post a thread on how to set up and lock down a public access computer in a public library simulating Windows mandatory profiles, from start-to-finish.

EDIT:

As for feedback from the public, what we've found so far is that they hardly know the difference (Windows vs. Ubuntu).  Openoffice Writer is configured to use .doc as the default save format (our users are used to, and have documents in, Word formats), they like the mutlimedia (Totem) capability, and overall I think the reception has been very positive.  Our patrons browse the net and create/edit documents for the most part, and Gutsy has worked great.

---

### Post by warbird on 2008-02-28
I was looking around regarding this myself. Here is what ive found out:
/etc/gdm/PostLogin/Default is run as root, when the user logs in
/etc/gdm/PostSession/Default is run as root when user logs out.

So these can be used to reset the home folder for the user. (edit: hmm , would probably do the same for root, so another approach is necessary.(edit2: I guess if it script only touches the public_users home dir, it doesn't matter if it gets run after every logout.))

Also, this site: [http://www.coffeebreaks.org/blogs/?p=60&p=60](http://www.coffeebreaks.org/blogs/?p=60&p=60) has some useful info, autologout scripts etc.
Same goes for this site: [http://www.ehartwell.com/InfoDabble/HowTo:_Create_a_boot-from-CD_browser_kiosk_with_Firefox_and_Linux](http://www.ehartwell.com/InfoDabble/HowTo:_Create_a_boot-from-CD_browser_kiosk_with_Firefox_and_Linux)

edit3: I found a tool called pessulus ([http://www.gnomefiles.org/app.php?soft_id=1082](http://www.gnomefiles.org/app.php?soft_id=1082)) (you can apt-get it) that helps you lock down gnome too.

---

### Post by clutch68rs on 2008-03-04
warbird:  thanks for bringing up pessulus.  We use it to lock down the panel and a few other GUI elements.  It's quite handy and takes away some incentive for the public to mess with the desktop.

If a patron happens to leave the desktop in a state that is unusable by the next user, staff simply restarts the computer and walks away, everything resets itself.  That doesn't happen too often, surprisingly, and hasn't been a problem.

If gnome had a desktop setting, similar to KDE, that allowed you to lock the desktop icons, even the rare reboot wouldn't be necessary.  If anyone out there knows how to make the desktop icons un-movable, I would love to know how you did it.

(we have them reboot just because its easier for them, rather than remembering login/passwords)

---

