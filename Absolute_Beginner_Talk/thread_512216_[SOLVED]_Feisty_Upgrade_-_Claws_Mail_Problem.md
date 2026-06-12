---
title: "[SOLVED] Feisty Upgrade - Claws Mail Problem"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-07-28
I upgraded 6.10 to 7.04, then changed the Claws repository from edgy to feisty, then used Upgrade Manager to update Claws from 2.9.1 to 2.10.0.

It now takes 3 minutes and 55 seconds to start Claws, with the CPU pegged at 100%.

Seems to work otherwise, but that's badly wrong.

---

### Post by moore.bryan on 2007-07-29
[I]firstly, are you using the claws-mail repo?```
deb http://www.claws-mail.org/ubuntu/feisty/ ./
```
if so, i'd suggest reinstalling to see if it solves you problem...
```
sudo aptitude reinstall claws-mail
```[/I]

---

### Post by ofb on 2007-07-29
> **moore.bryan said:**
> *firstly, are you using the claws-mail repo?*

Yes.

> *sudo aptitude reinstall claws-mail*

No change, alas.

Small odd things that may not be related:

- that '*aptitude reinstall*' operation also said '*the following packages are unused and will be removed: kaffeine kaffeine-xine khelpcenter*'. I don't know why it would take Kaffeine away. I often needed that to play some file types. And khelpcenter? That's odd - I've often clicked for Help in my KDE apps and been told I didn't have khelpcenter installed...

- on this morning's boot, one drive needed it's scheduled 30 day scandisk. At the end of that was a brief mention: "*Warning: no final newline at /etc/fstab*"

- and, Ubuntu failed to shut down completely last night. It went right to the final moment of blank screen before powering off, then didn't. I had to unplug - bad memories of W98 there. Ubuntu did shut down properly on a test this morning.

Probably little of that is related, but since we're chasing a mystery I figure I should state everything.

Now let's look at fstab. Konq shows it was modified yesterday, and there is a backup called fstab.edgy.

the line
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
has been changed to
```
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

That's the only difference. I don't know what "final newline" means.

---

### Post by moore.bryan on 2007-07-29
> **ofb said:**
> - that '*aptitude reinstall*' operation also said '*the following packages are unused and will be removed: kaffeine kaffeine-xine khelpcenter*'. I don't know why it would take Kaffeine away. I often needed that to play some file types. And khelpcenter? That's odd - I've often clicked for Help in my KDE apps and been told I didn't have khelpcenter installed...
*now THAT is strange... does ```
sudo apt-get reinstall claws-mail
``` do the same thing?*
> - on this morning's boot, one drive needed it's scheduled 30 day scandisk. At the end of that was a brief mention: "*Warning: no final newline at /etc/fstab*"
*that's a new one for me... never heard of it.*
> Probably little of that is related, but since we're chasing a mystery I figure I should state everything.
*you're absolutely right... better to give all the info than not enough.*
> Now let's look at fstab. Konq shows it was modified yesterday, and there is a backup called fstab.edgy.
the line
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```has been changed to
```
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```That's the only difference. I don't know what "final newline" means.
*i don't know why it would read your cdrom as hdc... THAT'S strange... the new line is what it should be.  have you tried completely removing claws-mail?*

---

### Post by ofb on 2007-07-29
> **moore.bryan said:**
> *now THAT is strange... does ```
sudo apt-get reinstall claws-mail
``` do the same thing?*

Oh, that's sweet. Here's what that gets me:* E: Invalid operation reinstall*

> *that's a new one for me... never heard of it.*

I did some reading. Various people have mentioned* "no final newline at /etc/fstab*" in various years. Some think it means there's no blank line at the end of the fstab, and you should add one. Nobody says why. I think I'll just leave it alone till I have better information.

> *i don't know why it would read your cdrom as hdc... THAT'S strange... the new line is what it should be.  have you tried completely removing claws-mail?*

No, I haven't. Since it works except for the incredibly long start-up, I'm reluctant to experiment without solid advice. And now the error on apt-get reinstall really worries me. I've just done the aptitude reinstall successfully again with the same result on start.

Funny I can't find other people with Claws with the same problem.

---

### Post by moore.bryan on 2007-08-01
[I]that was my bad... apt-get doesn't have a reinstall option, just aptitude.
i would actually suggest you completely remove claws and reinstall from scratch. ```
sudo aptitude remove --purge claws-mail && sudo aptitude install claws-mail
```
it sounds like there's a dependency issue and that process should solve it....
[/I]

---

### Post by ofb on 2007-08-03
> **moore.bryan said:**
> [I]```
sudo aptitude remove --purge claws-mail && sudo aptitude install claws-mail
```
[/I]

Um, so how will that affect my config files, and plug-ins? 

Meanwhile I did try a reinstall with Synaptic -- searched 'claws', and selected Remove for the 27 items shown. (Did not select Complete Removal, as I think that would take out my config, yes?) Then searched 'claws' again and selected the same 27 for installation. Result - no change.

---

### Post by moore.bryan on 2007-08-05
> **ofb said:**
> Um, so how will that affect my config files, and plug-ins? 
*it would remove all that stuff... but, then again, that might be the stuff giving the issue...*

---

### Post by ofb on 2007-09-04
Found it - it's the ClamAV plug-in. Remove that and Claws starts up fine.

I suspect this is related to our repositories being out of date. If you 'sudo freshclam', your terminal will keep scrolling failed logon attempts. Probably Claws runs freshclam when it loads the plugin.

The out-of-date ClamAV & TK business  is a topic covered (though not resolved) in other threads, and other sources online. Bit of a mess, that.


EDIT: Even better solution - enable Backports and get a new enough ClamAV to solve that problem. So Claws is both fixed, and has ClamAV intergration again.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

