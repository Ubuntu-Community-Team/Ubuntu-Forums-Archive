---
title: "The Upgrade to Gusty"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by monsieurdozier on 2007-10-06
So I've never experienced a Ubuntu upgrade, and I'm a little excited, but what should I be looking for?

Is my Feisty going to upgrade itself to Gusty?  What will change if/when I do upgrade?  Will it be just starting from stratch again, or will only a few things change?


Basically, what's exactly going to happen?

Monsieur Dozier

---

### Post by Jimmyfj on 2007-10-06
To upgrade Feisty to Gutsy you can type this code in a terminal:

```
gksu update-manager -c -d
```

Hope you have a fast internet connection otherwise be patient.

There are many things to look for. One is the menu Places which holds more folders than Feisty. Others you'll be able to find surfing this forums many pages.

---

### Post by adamorjames on 2007-10-06
Most things I'm guessing will stay the same since it's not a total wipe out. Your prefrences and such will be the same. I think the theme may stay the the same. Just do it and find out!. :lolflag:

---

### Post by old_geekster on 2007-10-06
If you are going to upgrade to Gutsy, I would think about doing it now or wait until the rush has slowed after the final release.  It took about three days for the servers to get back to normal when we upgraded from Edgy to Feisty.  I upgraded early and beat the rush.  Once you upgrade, if you simply update your distro when they are available , then you will automatically have Gutsy final on release day.

This time, however, at this point I can't get Feisty to upgrade to Gutsy.  Something is not the way it should be.  I have all of the updates to Feisty, so I am not certain why it is not working.  I will figure it out and "git'er done", however.

---

### Post by Stall on 2007-10-06
Should I back up my home folder for an upgrade? 

I also have never experienced an Ubuntu upgrade. I am really looking forward to it.

---

### Post by Incense on 2007-10-06
> **Stall said:**
> Should I back up my home folder for an upgrade? 

I also have never experienced an Ubuntu upgrade. I am really looking forward to it.

Never hurts to back up your data. Do it often, upgrade or not. Though to answer your question Ubuntu upgrades are mostly smooth and painless.

---

### Post by metalpancake on 2007-10-06
I tried typing in the code metioned above, but it didn't work properly:```
gksu: invalid option -- c
GKsu version 2.0.0

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
dylan@dylan-laptop:~$ 


```

---

### Post by kshane on 2007-10-06
What is "gksu"???   I haven't ever used that.  GKSUDO or SUDO...  I noticed some of the errors in the one post had to do with that command...

Kevin

---

### Post by Frak on 2007-10-06
> **kshane said:**
> What is "gksu"???   I haven't ever used that.  GKSUDO or SUDO...  I noticed some of the errors in the one post had to do with that command...

Kevin
gksu is the graphical version of su, though gksudo would be safer to use.

---

### Post by monsieurdozier on 2007-10-07
Feisty Fawn uses GNOME, and Gusty uses Compiz-Fusion.  When I upgrade will my GNOME become Compiz-Fusion?

Monsieur Dozier

---

### Post by adamorjames on 2007-10-07
> **monsieurdozier said:**
> Feisty Fawn uses GNOME, and Gusty uses Compiz-Fusion.  When I upgrade will my GNOME become Compiz-Fusion?

Monsieur Dozier

Umm... Compiz-fusion is just added effects for Gnome... or so I think :)

---

### Post by Frak on 2007-10-07
> **adamorjames said:**
> Umm... Compiz-fusion is just added effects for Gnome... or so I think :)
You are correct.

---

### Post by autocrosser on 2007-10-07
Compiz-Fusion is the extension/fusion of the "old" Compiz & Beryl projects--a bit of both to make the project better....If your hardware will support it, Desktop-effects will start by default.

There are several other "under-the-hood" upgrades & in my case, Gutsy is much smoother than Feisty---both in speed & having some of the rough edges polished a bit. Of course, your mileage may vary.

I dual-boot Feisty & Gutsy, but for the last 2 months I haven't started Feisty at all. I would recommend you following the "HowTo Move your /home" 

[http://ubuntuforums.org/showthread.php?t=46866&highlight=%2Fhome](http://ubuntuforums.org/showthread.php?t=46866&highlight=%2Fhome)

This will make future upgrades very painless.......You can reinstall or upgrade without worry.

---

### Post by om1 on 2007-10-07
to upgrade just run
```
update-manager -d
```
be warned that it is still beta..... but it is pretty stable but you never know
just back up your data first .... then run the command and you will be good

---

### Post by mtgrocks04 on 2007-10-07
I have been trying to update using that code, but it tells me that I don't have "kubuntu-desktop" or "Gnome-Desktop" or something to that effect and that it cannot continue. I tried to install the package but it gives me a "break"   how do i get past this?

---

### Post by om1 on 2007-10-07
do you use kubuntu? 
if you do use this like it should help you
[https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52](https://help.ubuntu.com/community/GutsyUpgrades#head-3cb12417f0af7f24d4a34f2ae4040bf791c42f52)

---

### Post by misfitpierce on 2007-10-07
Just wait until Oct. 17th and it will show on update manager and give option to upgrade.

---

### Post by mtgrocks04 on 2007-10-07
I am aware that it will be available then, I would like to upgrade now to avoid the rush, so what would be the way to fix this issue?

---

### Post by AsokInIndy on 2007-10-11
Question, why not just vi /etc/apt/sources.list and change everything from saying from Feisty to Gutsy.  Then init 1, then run apt-get update and then install the updates?  Then reboot.

---

### Post by adamorjames on 2007-10-11
> **AsokInIndy said:**
> Question, why not just vi /etc/apt/sources.list and change everything from saying from Feisty to Gutsy.  Then init 1, then run apt-get update and then install the updates?  Then reboot.

That's what I first did which was very buggy but not too bad after some messing around. A day or so later I messed up my Alsa so bad trying to fix the soft sound prob... had to reinstall, used Tribe 5 CD since the Beta CD doesn't work for me (install doesn't work, yes I tried the both the live and alternative CDs), then upgraded from there. :) Oh by the way, upgrading took a long time for me, my internet download speed is 300kb/s but the download speed for upgrades wasn't close to that. I'd say for the normal Ubuntu users it's best to just wait for the Final release of Gutsy.

---

