---
title: "Broken Early Update. 7.04 ==&gt; 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by gkjohn on 2007-10-18
Hi all,

I realize that the forum is going to be slammed today with posts regarding the update and I'll post my problem here and hope that someone can help out.

I updated from 7.04 to 7.10 a few days ago, ostensibly to avoid the rush using:

```
sudo update-manager -c -d
```

It downloaded and installed up to a point, it looked close to done, going by the progress bar.  Then I got an error message and it asked me to run:

```
sudo apt-get --fix-broken install
```

to try and fix the installation. 

So I rebooted and it booted in to some very basic graphic mode, I uninstalled the Nvidia drivers and reinstalled them and it looks okay.

I ran said command but it did not find anything to fix. 

I'm left with broken user accounts, where you can log in to them however none of the icons respond to clicks nor is there the power button to log out/power down etc. I can, however, click the trash can. 

The Admin account seems to be functional but I have dual instances of some of the menu items, such as Printing. 

I think I'm running some borg hybrid of 7.04 and 7.10.

Is there anyway to force an upgrade or to re-apply an upgrade?

The output of: 

```
cat /etc/issue
```

is

Ubuntu 7.10 \n \l

---

### Post by jimbren on 2007-10-18
I ran into a slightly similar situation when I did an upgrade of Kubuntu 7.04 to 7.10 a few days ago, though my system wasn't quite as broken as yours.  

I was unable to run most apps, though the upgrade supossedly completed successfully.  I didn't thoroughly document what was going on, but one thing I noticed that is different from what you're reporting is that my system reported that it was 7.04 despite also reporting the upgrade as being successful.  

So here's what I did:

1) Reboot.  Started up normally with no apparent issues.  At the KDM login manager, I logged in using console mode.  

2) checked /etc/apt/sources.list to make sure that it was changed for gutsy, which it was.

3) apt-get update--no problems.

4) apt-get -f install--there were no packages to fix, though it found over 700 that were upgradeable.  

5) apt-get upgrade--installed all packages without a problem

6) apt-get dist-upgrade--nothing to install

7) apt-get -f install--nothing to fix

8) Rebooted again--clean reboot again.  Logged in normally, and just about everything worked without a problem.  One exception to this was my Ubuntu installation of Firefox.  It would appear to start and then bomb out without error, and the process would appear running but idle.  I tried to fix it several times without success, and ended up just downloading and installing directly from Mozilla.

Now I'm downloading a new CD so I can do a fresh installation.  Because I'm a dork like that.

jimbo.

---

### Post by juantovarm on 2007-10-18
You could try this in the terminal

sudo do-release-upgrade

see if it helps

---

### Post by gkjohn on 2007-10-18
> 2) checked /etc/apt/sources.list to make sure that it was changed for gutsy, which it was.
3) apt-get update--no problems.
4) apt-get -f install--there were no packages to fix, though it found over 700 that were upgradeable.  
5) apt-get upgrade--installed all packages without a problem
6) apt-get dist-upgrade--nothing to install
7) apt-get -f install--nothing to fix

Followed all of these steps, it found nothing to upgrade or update. Sources were for Gutsy. 

Did the:

```
sudo do-release-upgrade
```

as well but it reported:

> Checking for a new ubuntu release
No new release found


Thank you for your quick replies. Much obliged.

---

