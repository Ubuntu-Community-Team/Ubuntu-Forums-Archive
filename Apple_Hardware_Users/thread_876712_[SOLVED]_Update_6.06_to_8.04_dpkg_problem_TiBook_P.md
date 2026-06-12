---
title: "[SOLVED] Update 6.06 to 8.04 dpkg problem TiBook PPC"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-08-01
I finally bit the bullet and tried a dist upgrade with Update Manager. things went well until the new software was being installed and I got an error saying there were too many errors and UpdateManager would run ubuntu dpkg --configure -a  to correct the problem but that my system may be unusable. It ran and installed a bunch of packages and then quit. I have a hybrid system running now and I have not restarted (UpdateManager never got that far).
I logged out and in and tried running synaptic and again got the error 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I ran the command and a bunch more packages installed then error
"dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted"
I ran dpkgagain, more installed packages then the error. I did this 6 or 7 timesand now no packages install as all of them have dependency problems, which was the case beforebut some other packages still installed.So these are orphans of some kind.
Example: 
"dpkg: dependency problems prevent configuration of foomatic-gui:
 foomatic-gui depends on python-foomatic (>= 0.7.7ubuntu1); however:
  Package python-foomatic is not configured yet.
dpkg: error processing foomatic-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pgsql:
 python-pgsql depends on python-central (>= 0.5.8); however:
  Package python-central is not configured yet.
dpkg: error processing python-pgsql (--configure):
 dependency problems - leaving unconfigured"

I have searched the lists and forums and googled but the only examples I get are foreign languages that don't translate too well and aren't that relevant anyway.
Any ideas? Thanks so much. I am marginally encouraged so far but I'm not restarting my box yet unless this is unresolvable.

---

### Post by ubuntubrian on 2008-08-01
I finally found this:
[http://irclogs.ubuntu.com/2008/01/31/%23edubuntu.txt](http://irclogs.ubuntu.com/2008/01/31/%23edubuntu.txt)

which has reference to similar problem here:
"[11:17] <Nubae> i cant do dpkg --configure -a anymore, so I'm sorta stuck...
[11:17] <ogra> looks like a broken dpkg
[11:18] <Nubae> how could I check to see which one?
[11:18] <ogra> i mean the program dpkg
[11:18] <Nubae> dpkg: error processing libgdl-1-0 (--configure):
[11:18] <Nubae>  thats the last one before the error
[11:18] <Nubae> ah... oh
[11:18] <ogra> dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
[11:18] <ogra> looks serious
[11:18] <Nubae> dpkg: too many errors, stopping
[11:19] <Nubae>  I get that just before
[11:19] <ogra> can you check the scrollback for the very first error ?
[11:19] <ogra> i suspect thats not the first
[11:20] <daya> ogra, which list in repo
[11:20] <daya> ogra, its from ubuntu
[11:21] <ogra> its identical
[11:21] <Nubae> GC Warning: Couldn't read /proc/stat
[11:21] <Nubae> Couldn't read /proc/self/stat
[11:21] <Nubae> Aborted (core dumped)
[11:21] <ogra> Nubae, heh
[11:21] <ogra> mount proc in the chroot
[11:21] <ogra> some packages require it
[11:21] <Nubae> doh, makes sense"

But it doesn't really seem to apply. Here's what I get when I run the command:
" sudo dpkg --configure -a
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                   ALSA lib confmisc.c:768:(parse_card) cannot find card 'Headset'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
                                                                         [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-central (0.6.7ubuntu0.1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-central (--configure):
 subprocess post-installation script returned error exit status 1..."

<snip>

dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted

Any help? I have read that a clean install may be the only solution but I'd probably revert to my backed up Dapper and keep my many customizations.

Many thanks again!!

---

### Post by ubuntubrian on 2008-08-01
I solved this with the help of my local users group, NMGLUG. I'm posting the solution as it was written to me. I knew that dpkg was choking on python-central but didn't know how to get past it. I ran and re-ran the commands below, a little differently. I ran 
"dpkg -P python-central"
and when that completed I ran:
"apt-get install python-central"
the package installed and then the upgrade continued on its own in terminal. It borked at another python package so I did the same thing for that one and it installed the package but no further running of the upgrade.
I then ran the commands below for apt-get, ran update manager and synaptic, screwed up some permissions and fixed those (don't have a clue how that happened! I wasn't setting permissions)
It all works, everything! 
From my group:

"If it's still the timidity and python-central errors, try purging
those packages:

dpkg -P timidity
dpkg -P python-central

You might have to purge a few dependencies, too.  Then:

dpkg --configure -a

That's the basic idea anyway for a way to correct this problem that
has worked for me in the past.

Once the configure completes successfully, I'd try:

apt-get -f install

until it does nothing, then finish the upgrade:

apt-get dist-upgrade

repeatedly until it is done.  After all that, reinstall timidity and
python-central if you need them."

---

