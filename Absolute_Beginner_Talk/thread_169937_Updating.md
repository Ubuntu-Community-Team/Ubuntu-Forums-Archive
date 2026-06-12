---
title: "Updating"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by pug_205 on 2006-05-03
I've recently switched to Ubuntu, so I haven't yet had to deal with the process of updating to the latest version. Can anyone explain to me what is involved in the whole update process? Is it quick and painless or will I have to download the cd and do a complete reinstall, and possibly have to reinstall some of the software that was previously installed.

---

### Post by aysiu on 2006-05-03
Here are instructions for upgrading:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

It's painless and will keep all your settings and software (well, for the most part) you have installed... if you have a broadband connection. If you have dial-up, it'll be painful.

You can always do a clean reinstall, though. If you find yourself preferring a clean reinstall, you may want to create a separate /home partition for yourself so that you can reinstall every six months without losing your data and settings.

---

### Post by nanotube on 2006-05-03
[QUOTE=pug_205]I've recently switched to Ubuntu, so I haven't yet had to deal with the process of updating to the latest version. Can anyone explain to me what is involved in the whole update process? Is it quick and painless or will I have to download the cd and do a complete reinstall, and possibly have to reinstall some of the software that was previously installed.[/QUOTE]
once the dapper official release is made, you should be able to upgrade to it through the update manager, afaik.

---

### Post by pug_205 on 2006-05-03
Ok, thanks alot for the help guys. 
Just wanted to make sure before I installed it here at work.

---

### Post by Jagot on 2006-05-03
There is also this method as described in the release notes for the Dapper beta:

[http://www.ubuntu.com/testing/dapperbeta#head-ab14ca6ed574c075d6fca55646707133e6a68110](http://www.ubuntu.com/testing/dapperbeta#head-ab14ca6ed574c075d6fca55646707133e6a68110)

---

### Post by centyx on 2006-05-03
I've tried running 'gksudo "update-manager -d,' and then clicking the "upgrade" button next to Dapper release, but the following error message is displayed:

"Could not find the release notes.
The server may be overloaded."

Any ideas?

---

### Post by Jagot on 2006-05-03
Well, I would assume that, as it says the server is overloaded, so just try again a bit later.

---

### Post by centyx on 2006-05-05
I get this message no matter what time of day I attempt to upgrade. I'm not sure which apt source or server it's referring too, but I am able to get breezy updates without any problems. Somehow I doubt that it is that the server is overloaded, though. Can you upgrade with the usual apt-get dist-upgrade like in debian?

---

### Post by djsroknrol on 2006-05-06
Aysiu's never steered anyone wrong yet...

It's working fine for me..I haven't lost anything yet that I've seen...

Aysiu, you should be a moderator with your experience...thank you sir :)

---

### Post by centyx on 2006-05-06
Oops, I totally missed that. apt-get dist-upgrade was the way that Aysiu was suggesting. So far, no major problems. It didn't upgrade xorg-driver-fglrx for some reason, but besides that and X consequently not starting on its own, everything seems OK.  I'm not terribly concerned, since I upgraded a duplicate partition of my Breezy installation anyway.

---

### Post by djsroknrol on 2006-05-06
I had the same problem with x not restarting...just did a 3 finger salute, and it came back fine...

---

### Post by djsroknrol on 2006-05-07
Oh, man...gota eat some crow here!! I really haven't had the time these last few days to really check the upgrade, so here's the whole story on dist-upgrade on a up to date breezy install to 6.04...

1) all but wrecked smbfs..uninstalling it and re-installing it put it all back together real quick (good thing I backed up).

2) Of all the things to go...my eye candy, dual monitors, to name a few...It wiped my openoffice !!??......go figure...I would say, all in all, it's a 98% sure thing, which is great.

3) I realized afterward that I didn't uninstall Automatix...my bad !...it did not effect the upgrade in any way...In fact I tried to run it after it was all over, and got a message to the effect of "This program runs in Breezy, not Dapper". 

It took all of 7 1/4 hrs on a ave. 50 kbs download...people have said this way is pretty slooooow...:(  I using the k-7 kernal and I kind of notice a bit of sluggishness to it...maybe it's Nautilus...not sure yet...time will tell...

Well, I'm off to change my user status in CP.  ;)

---

