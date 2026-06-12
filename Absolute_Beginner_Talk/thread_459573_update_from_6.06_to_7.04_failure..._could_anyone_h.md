---
title: "update from 6.06 to 7.04 failure... could anyone help please?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by toughgamer on 2007-05-30
Greetings from a total newbie :)

I m sorry this could be a bit complex to explain, basically, I installed ubuntu 6.06 on a notebook** without CDROM or floppy drive** at all. Then I tried to update it directly (with an internet connection) to 7.04, then I failed... 'system halt'. So I restarted the notebook only to find that I can't get into the system anymore, it stopped at the welcome screen of edubuntu (as I chose this for the startup screen, well, accidentally, as I don't even know how I did it...). 

I tried to restart it again and somehow got into the screen sorta like DOS, where I saw a list of options like system.... 6.10, 6.10 (recovery), 6.11, 6.11 (recovery), anyway, I chose the oldest one (6.10 recovery), and waited till everything's loaded and it actually gave me a login window!!

So I entered the username and pass, got in, the mouse was working, but that was it - only the mouse was working, I could move it anywhere on the screen, but the screen itself is just a big yellow block... nothing on it.

Anyone has any idea how to fix this? thanks! it's actually my wife's notebook and she needs it urgently for uni assignments... please help, thanks a lot!

oh, btw, like I mentioned before, this is a special situation: i don't have CDROM drive (actually I busted it accidentally) or floppy on the notebook, I succeeded in installing ubuntu 6.06 from the original windows xp home edition preinstalled on the notebook with the alternative iso I downloaded, but now there's no way i can boot that thing again... i am guessing here that maybe I can type in something under the terminal mode (the DOS-like window I guess?), then bring it back to life? Thanks a lot!

---

### Post by dbbolton on 2007-05-30
when you turn on the computer, does GRUB show up? it's a black screen with a list of systems in white letters.

---

### Post by toughgamer on 2007-05-31
> **dbbolton said:**
> when you turn on the computer, does GRUB show up? it's a black screen with a list of systems in white letters.

yes, i think so... that's what i called the DOS screen I guess. 

so when i start it up, i get a list of options like core 6.10, core 6.10 recovery, core 6.11, core 6.11 recovery, that's why i thought there might be some way i can somehow reinstall the thing, or at least restore the system to the state before i ran the update...

---

### Post by dbbolton on 2007-05-31
if you choose Recovery Mode from GRUB, it should take you to a command line interface. a bunch of white text will fly by, then it will just say something like "root@computer:#". when that comes up, type: ```
aptitude update
```this will update your list of software sources. then do ```
aptitude upgrade
```
this will update any packages that you have an old version of.

---

### Post by toughgamer on 2007-05-31
> **dbbolton said:**
> if you choose Recovery Mode from GRUB, it should take you to a command line interface. a bunch of white text will fly by, then it will just say something like "root@computer:#". when that comes up, type: ```
aptitude update
```this will update your list of software sources. then do ```
aptitude upgrade
```
this will update any packages that you have an old version of.

thanks a lot! i will go home and try it after work, i might still need your help later on though~~~ thanks a lot dude!

---

### Post by dbbolton on 2007-05-31
> **toughgamer said:**
> thanks a lot! i will go home and try it after work, i might still need your help later on though~~~ thanks a lot dude!
i'll be keeping an eye on this thread ;)

---

### Post by toughgamer on 2007-06-01
great! now i m back in and i m not gonna update again~~~ not without a disc drive or something i think,

thanks so much for the help!

and i did encounter some problems half way - the system said it couldnt get the update right, but suggested me with "you must manually run dpkg --configure -a", so that i did, and after lots of white characters flying by (not in the matrix style, pity...), it gave me that root@ubuntu line again, this time i chose to run aptitude upgrade like you said, and it started fixing everything automatically, after restarting the machine, it's back to life! 

thanks so much man, and I am thinking of getting a few books on ubuntu now :), I am really amazed how a system could just fix itself with just 3 lines of codes:KS

---

### Post by zvacet on 2007-06-01
I´m glad that in your case all end as happy end,but reading just one page will save you trouble.

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

And yes it is amazing OS.

---

### Post by dbbolton on 2007-06-01
> **toughgamer said:**
> great! now i m back in and i m not gonna update again~~~ not without a disc drive or something i think,

thanks so much for the help!

and i did encounter some problems half way - the system said it couldnt get the update right, but suggested me with "you must manually run dpkg --configure -a", so that i did, and after lots of white characters flying by (not in the matrix style, pity...), it gave me that root@ubuntu line again, this time i chose to run aptitude upgrade like you said, and it started fixing everything automatically, after restarting the machine, it's back to life! 

thanks so much man, and I am thinking of getting a few books on ubuntu now :), I am really amazed how a system could just fix itself with just 3 lines of codes:KS
you're quite welcome.

---

