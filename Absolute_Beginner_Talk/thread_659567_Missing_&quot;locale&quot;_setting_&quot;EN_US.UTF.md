---
title: "Missing &quot;locale&quot; setting &quot;EN_US.UTF-8&quot;, system down"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by RustyWyatt on 2008-01-05
Hi Folks,

Well I'm a pretty happy new user and unfortunately not well versed in Linux or Ubuntu (as in I don't have a clue!).

For the last week I have been getting errors and incomplete software updates as automatically offered and usually completely uneventful for me.

So, this morning I tried the update function again and continued to get the error msg that basically said it was going to do a partial update and then later failed to even complete that.  However, it seemed to me that I was making progress so I just ran it a number of times...

Well, the last time I ran the updater, my screen wiped out (random red stripes) and the system locked up.  The update problems seemed to be related to OpenOffice.

When I tried to reboot, first I ended up on a brown screen with a partially opened terminal window and a msg saying that a "child process could not be started" system locked up requiring a hard reboot.

I finally ended up in the terminal mode (via Recovery) and it seems like I have a "language" problem and there is no "EN_US.UTF-8" set in my system.

I spent the day trying to solve this, all to no avail. Whenever I try to "apt-get" I get a fail to retrieve file from an archive. When I try to configure "locale" I get a no such command response.

Can anyone help me get this system back up?

All thoughts GREATLY appreciated!

PS Am checking in via WinXP and can run command line pretty reliably.

Thanks again,
Tom

---

### Post by empthollow on 2008-01-06
you could try one of these:
```
sudo dpkg-reconfigure locales
```
```
sudo apt-get install --reinstall language-pack-en
```

---

### Post by RustyWyatt on 2008-01-06
Thanks empthollow!

For the first time "sudo dpkg-reconfigure locales" ran a configuration application which  I used to select "EN_US.UTF-8".

Which got me back to my brown screen and a partial terminal screen...

However, I have discovered that I am not connecting to the internet from the Recovery command line. I have tried both wireless and a cable connection to my router. Therefore "apt-get" cannot work...

I have three questions"

1 - Can I download what I need and burn it to a CD/DVD or write it to one of my other working drives that I can see in Windows?

2 - Will one of the linux disk rescue boot programs help here?

3 - Can I copy my home structure to another drive then simply reinstall 7.10 and then recover my home dir?

Once again, thanks for for all of your thoughts and help!!

Tom

---

### Post by empthollow on 2008-01-06
1.  you can download the ubuntu live cd in windows and burn it to disc.  you can boot off the disc and you will have a fully working system.  

2. i'm not familiar with the rescue programs so i can't really answer that.

3.  you can copy your home directory and all hidden files and that will contain all of your preferences for all your programs.

---

### Post by RustyWyatt on 2008-01-06
Thanks for the info Jeremy!

I wonder if I can fix my problem on the hard drive using the live CD?  

I was referring to " http://www.sysresccd.org/Download" a great hard drive utility I have used in the past.

Well, if nothing else I'll copy my "home" structure and reinstall 7.10 from scratch if, the live cd can read the hard drive (my next test project)...

Thanks for all of the help!

Tom

---

### Post by empthollow on 2008-01-06
i've fixed all of my curcial system problems using the live cd.  don't forget about the chroot command. it will get you into the broken system. :)

---

### Post by RustyWyatt on 2008-01-07
Thanks Jeremy,

Well today I have proven that this is a software problem in Ubuntu and not a hard drive configuration problem!

And, the Live cd will not install on my Lenovo T60 in any install mode because of the video card... Murphy was an optimist!

It's been awhile since I have installed Ubuntu from scratch on the T60 so I'll work on getting it up and then I'll use your chroot tip!

Thanks again,
Tom

---

### Post by RustyWyatt on 2008-01-07
Well no luck yet so I'm going to move this discussion over to installation/upgrade.

I still can't connect to the internet from recovery so I can't rebuild languages.

Thanks for the help Jeremy!

Tom

---

