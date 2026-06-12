---
title: "Which file to download and what to do with it"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Coomkeen on 2006-09-06
Hi All,

Being very new to Linux and Ubuntu (both great so far) I want to run NVU as I used to in windows.
The NVU site lists 3 files:

    *  nvu-1.0-pc-linux2.6.10-gnu.tar.bz2 - Tarball built on Linspire 5.0 (Debian k2.6.10), gcc/g++ 3.3.5
    * nvu-1.0-pc-fedora3-kde.tar.bz2 - Fedora 3 tarball (KDE)
    * nvu-1.0-pc-mandriva10.1-gnu.tar.bz2 - Tarball built on Mandriva 10.1

Any idea which one I need, and what to do with it after saving to disc?

Sorry for the silly newbie questions.

Ron

---

### Post by Uluen on 2006-09-06
Why don't you grab the one in the repos?

---

### Post by hw-tph on 2006-09-06
First enable the Universe repository (and Multiverse too, if you will install packages from there) as [described here](https://help.ubuntu.com/community/Repositories/Ubuntu#what), then you can install nvu using Synaptic, aptitude, or whatever Debian package management tool you like,


Håkan

---

### Post by empcrono on 2006-09-06
go to the top of the screen and click on Applications then go to accessories then go to terminal then  type this in.

sudo apt-get install NVU
then when it asks you for a password type in the password you made.

if that doesnt work then post that it didnt with as much info as you can and i'll see if i can help

---

### Post by Coomkeen on 2006-09-06
Thanks for all your help.
I'm not used to repositories and package managers so please excuse my stupidity.
However, I've managed to use Synaptic and installed nvu, but it doesn't appear on any list of applications to run it.
I tried Applications - add/remove, but nvu is not listed, not even when searched for.
Where's it gone?

Thanks again.

---

### Post by Druidor on 2006-09-06
try typing nvu in the terminal to see if it runs up

---

### Post by Blondie on 2006-09-06
> **Coomkeen said:**
> Thanks for all your help.
I'm not used to repositories and package managers so please excuse my stupidity.
However, I've managed to use Synaptic and installed nvu, but it doesn't appear on any list of applications to run it.
I tried Applications - add/remove, but nvu is not listed, not even when searched for.
Where's it gone?

Thanks again.

Have a look in Applications / Accessories / Alacarte Menu Editor Nvu should be listed under Programming (picture of a trowel). That's where it should be anyway.

---

### Post by Coomkeen on 2006-09-06
Downloaded the Debian file (first one on the list) and did:

 sudo apt-get install NVU

and it said:

nvu is already the newest version.
 which is fine. So Synaptic did it's stuff OK.

Tried typing NVU in terminal, and it said:

 Extension System Warning: Failed to set up default extensions files probably bec ause you do not have write privileges to this location. While you can run Firefo x like this, it is recommended that you run it at least once with privileges tha t allow it to generate these initial files to improve start performance. Running

and then it ran NVU.

Not sure what all that means.

And still no NVU on a menu?

---

### Post by Coomkeen on 2006-09-06
Many thanks all.
NVU is now under programming menu.

What was all that Extension System Warning about though?

And is there anything I should be doing about it?

---

### Post by empcrono on 2006-09-06
It means you should login to NVU as &#8220;root&#8221; to do so do the following. Go to System / Preferences / login screen. Then under the security tab click allow local admin login. then under  system / administration / Users and Groups  click root then properties and give &#8220;root&#8221; a password. then logout then login with username being &#8220;root&#8221; and password being what ever you set it to login start NVU and it should be happy from now on. however im not sure you have to but that is what that little prompt NVU gave you ment.

---

### Post by Coomkeen on 2006-09-06
Ah yes. Thanks.
That worked OK.
Perhaps it was because it thought I needed to be logged in as root to install NVU.
NVU works from my 'normal' login OK now.

Thanks everyone for all the help.

Ron

---

### Post by hw-tph on 2006-09-07
Don't enable root login and don't set a root password. Use **sudo -i** instead. Works just as well.


Håkan

---

