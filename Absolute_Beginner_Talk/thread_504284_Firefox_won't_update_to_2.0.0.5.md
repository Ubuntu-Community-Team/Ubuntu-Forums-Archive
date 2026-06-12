---
title: "Firefox won't update to 2.0.0.5"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-07-19
I can't seem to get Firefox to update to 2.0.0.5 today in Ubunu. 
Earlier I booted into XP and the Firefox browser updated fine.
Can someone help.
Thanks

---

### Post by Gabn on 2007-07-19
Firefox will automatically update when the update comes through the ubuntu package server. 

if you wait a couple days i'm sure it will show up. otherwise reload your package list and make sure you have security update enabled.

---

### Post by deadlikeoscar on 2007-07-19
If you are using the version of Firefox that came with Ubuntu, Firefox will not have the option to update. You can  wait until the next version comes out from Ubuntu or you can remove the Ubuntu version and build the Mozilla version from source I believe.

---

### Post by ev5unleash1 on 2007-07-19
try the firefox website, if it is not there for linux it may not be out if it is download it. Ubuntu updates firefox though it's updates so check there. There is a poassablitys that they did not add it or they fell not to yet.

---

### Post by aysiu on 2007-07-19
Read this:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

---

### Post by the.phantom on 2007-07-19
i agree with aysiu 100%

just read the instructions ( no speed reading) and it will work find !

i used the old scripts but the new ones work great!
have 2.0.0.5 and will be able to easily upgrade it !
and when t-bird comes out with 2.0.0.5 with just one command i will update it !

---

### Post by urvaksh on 2007-07-19
does firefox not update automatically in ubuntu, like it does  in windows?

---

### Post by aysiu on 2007-07-19
> **urvaksh said:**
> does firefox not update automatically in ubuntu, like it does  in windows?
Read the link.

---

### Post by urvaksh on 2007-07-19
Is it possible to download 2.0.0.5 from the Mozilla website. If I download it to the desktop, what do I do next to overwrite the current version on my lappie and execute it.
sorry, for what might seem an overly simple question.

---

### Post by the.phantom on 2007-07-19
think Aysiu said it !

> Read the link.

if you want to be current with firefox and t-bird that way works

i am sure a lot of time and effort went into the info and the script !

you can downgrade back to the original version or easily upgrade to the latest version

---

### Post by keitare on 2007-07-19
> **urvaksh said:**
> does firefox not update automatically in ubuntu, like it does  in windows?
if you would of read the link you would of noticed this in the second or third paragraph > Due to the way Ubuntu packaging system is structured, once a release of Ubuntu is made, the Firefox and Thunderbird versions are frozen, and no updates are released except for security patches (this is true for the other packages as well, not just for the Mozilla ones). The security patches are usually several days or even a week or more behind the official Mozilla releases. Moreover, it is frequently desirable to run the latest versions of Mozilla software, due to the new features and improvements. Thus, this update script was born.

---

### Post by urvaksh on 2007-07-19
i can't seem to download the script from Ubuntuzilla. Either that, or it's taking very long.
 where does the script download to
Thanks

---

### Post by davidsrsb on 2007-07-19
The main security fix in 2.0.0.5 is the one caused by the combination of IE and Firefox, so it is Windows platform only unless you are running IE on wine

---

### Post by stinger30au on 2007-07-19
this thread will help.
in there is a repo for thunderbird 2

[http://ubuntuforums.org/showthread.php?p=3048141#post3048141](http://ubuntuforums.org/showthread.php?p=3048141#post3048141)

---

### Post by Flyvapnet on 2007-07-19
I've got Firefox 2.0.0.5 all nicely installed in Ubuntu 7.04 Feisty Fawn.  Try these steps and see if it'll work for you:

Follow the path System > Administration > Software Sources, then check all the boxes in all the tabs on the Software Sources window.  When you click on the "Close" button, you should get a re-load reminder; so click on that as well to start the re-load.

Then, follow the path System > Administration > Update Manager.  After it cycles through the usual sources and declares everything's up to date, click on the "Check" button.  If you're lucky, the update to Firefox 2.0.0.5 will be in there!

:)

=^..^=

---

### Post by Jonne on 2007-07-19
On my box firefox updated fine, (it showed up in update-manager and all), but help>about claims it's still firefox 2.0.0.3. Anyone else have this?

---

### Post by octathlon on 2007-07-19
I didn't have to do anything.  The FF update appeared in my list of automatic updates tonight, so I just had to click Apply Updates as usual. :)

---

### Post by alienexplorers on 2007-07-19
I just download the official linux version from mozilla and un-tar it into my /home directory.  I then set up a shortcut to it for on my desk top.  This way I still have the old version in case something goes wrong with the new version.  I also migrate all important from the old profile to the new profile.  Instructuctions for migrating the data can be fiund here:
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by benditlikebecker13 on 2007-07-19
OK, so I didn't have the problem the OP did, my Firefox updated just fine when I got home.... BUT, now Firefox is taking some tottaly random craps on me.  I thought it was maybe the theme I was using so I reveted back to the basic.  Still craps out on me.  And when I say random, I mean random.  Anyone else having this problem or anything I should be looking to to fix this?

---

### Post by crimesaucer on 2007-07-19
This is sort of off topic, but Swiftweasel 2.0.0.5 is ready: [http://swiftweasel.sourceforge.net/](http://swiftweasel.sourceforge.net/)

---

### Post by urvaksh on 2007-07-19
Just wanted to close the loop. the 2.0.0.5 update showed up in the update manager tonite. I downloaded the updates and all is well.
I still can't figure out ubuntuzilla. But I'm glad firefox automatically updates to the latest version

---

### Post by daktari on 2007-07-21
Re:  [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

( See "Usage Instructions" section )

Great work - a magic-bullet-fix for the  Firefox lock-down in LTS.

---

### Post by lotuseclat79 on 2007-07-22
Hi folks,

I use the Live CD of Ultimate Ubuntu with Fiesty Fawn release + Firefox 2.0.0.4.  Having looked at this thread and tried one of the solutions - i.e. Update Manager - I don't recommend it if you have a 56K dialup connection like myself.

Since Ultimate Ubuntu comes with the Synaptic Package Manager, I first used the Check function of the Update Manager (but not the Install function), and then updated Firefox 2.0.0.4 to version 2.0.0.5 with the Synaptic Package Manager.  It required one other package, firefox-gnome-support.  Just 9.262KB for firefox 2.0.0.5 and 86.2KB for firefox-gnome-support.

By tarballing and compressing the files contained in the following lists
1) /var/log/dpkg/info/firefox.list
2) /var/lib/dpkg/info/firefox-gnome-support.list
3) /var/lib/dpkg/info/firefox.conffiles
and saving them to disk, you can quickly integrate them into an initialization script on every boot up with the Live CD before connecting to the Internet.

-- Tom

---

### Post by daktari on 2007-07-23
> **daktari said:**
> Re:  [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

( See "Usage Instructions" section )

Great work - a magic-bullet-fix for the  Firefox lock-down in LTS.

/

Addendum for Mozilla Build Firefox 2.x on LTS ONLY:  

1- Firefox 2.x crashes / shuts down frequently on even simple low-code web sites particularly when two or more windows are open. 

2 - Firefox 2.x unpredictably opens a new tab OR a new window for multiple page views with no user intervention.  No observable pattern to which opens (tab or window).

I rolled back to 1.5 using the same Ubuntuzilla script url'd above.  The script worked flawlessly, both for update and rollback.  

But the *Mozilla* build of Firefox 2 doesn't work seamlessly with LTS.  I suspect this isn't a surprise to the Ubuntu build-ers.

**Is there an Ubuntu [B]LTS** build of a Firefox 2.x update on the horizon?[/B]

.

---

### Post by daktari on 2007-07-23
> **benditlikebecker13 said:**
> OK, so I didn't have the problem the OP did, my Firefox updated just fine when I got home.... BUT, now Firefox is taking some tottaly random craps on me.  I thought it was maybe the theme I was using so I reveted back to the basic.  Still craps out on me.  And when I say random, I mean random.  Anyone else having this problem or anything I should be looking to to fix this?

See previous post re: my experience with Firefox 2.x **_on LTS_** - it shuts down frequently and unpredictably.  No pattern or reason observed.  So I rolled back to 1.5.

---

### Post by boozereaper on 2007-07-23
yup, firefox went downhill after i installed the update.

---

### Post by daktari on 2007-07-23
-> ITEM: One other Firefox post-update / -rollback issue (LTS):

I now get periodic (roughly once-daily) pop-ups notifying me of available updates to Fox 1.5.0.12 - the version now on my box.  The pop-ups are 1.5 inches square and contain a link to info on the update.  In each instance, three of these identical pop-ups appear on the bottom right corner of the screen, each above the other (three high).  Clicking on the links produces no observable reaction - browser or otherwise.

---

### Post by nanotube on 2007-07-23
> **daktari said:**
> -> ITEM: One other Firefox post-update / -rollback issue (LTS):

I now get periodic (roughly once-daily) pop-ups notifying me of available updates to Fox 1.5.0.12 - the version now on my box.  The pop-ups are 1.5 inches square and contain a link to info on the update.  In each instance, three of these identical pop-ups appear on the bottom right corner of the screen, each above the other (three high).  Clicking on the links produces no observable reaction - browser or otherwise.

post the output of "crontab -l"
i suspect you have installed the automatic update checking functionality when you were installing with ubuntuzilla?

---

### Post by daktari on 2007-07-24
> post the output of "crontab -l"

0 0,4,8,12,16,20 * * * python /home/me/ubuntuzilla.py -p firefox -a checkforupdategui | logger -p user.notice -t "UBUNTUZILLA" -- >> /home/me/.ubuntuzilla.log 2>&1

> i suspect you have installed the automatic update checking functionality when you were installing with ubuntuzilla?

Negative - that was shown in the instructions as a separate command-line routine.  
**python ~/ubuntuzilla.py -a installupdater -p firefox**
I did not use that.  

I only used the primary for both update and rollback:
update to 2.x:   **python ~/ubuntuzilla.py -a install -p firefox**
rollback to 1.5:  **python ~/ubuntuzilla.py -a remove -p firefox**

---

### Post by nanotube on 2007-07-24
> **daktari said:**
> 0 0,4,8,12,16,20 * * * python /home/me/ubuntuzilla.py -p firefox -a checkforupdategui | logger -p user.notice -t "UBUNTUZILLA" -- >> /home/me/.ubuntuzilla.log 2>&1



Negative - that was shown in the instructions as a separate command-line routine.  
**python ~/ubuntuzilla.py -a installupdater -p firefox**
I did not use that.  

I only used the primary for both update and rollback:
update to 2.x:   **python ~/ubuntuzilla.py -a install -p firefox**
rollback to 1.5:  **python ~/ubuntuzilla.py -a remove -p firefox**

heh well, the output of your "crontab -l" speaks for itself - you have indeed installed the automatic update checker. 

the instructions also say, if you read carefully, that it is possible to emplace the update checker at the end of a regular install by saying "yes" in response to "do you want to install the automatic update checker". clearly, you have done just that. :)

anyway, it is easy to remove. enter command
"crontab -e"
and it will let you edit the crontab - just delete that line, hit ctl-x to exit, and say 'y' to save the file.

---

### Post by daktari on 2007-07-24
> heh well, the output of your "crontab -l" speaks for itself - you have indeed installed the automatic update checker. 

the instructions also say, if you read carefully, that it is possible to emplace the update checker at the end of a regular install by saying "yes" in response to "do you want to install the automatic update checker". clearly, you have done just that. :)

anyway, it is easy to remove. enter command
"crontab -e"
and it will let you edit the crontab - just delete that line, hit ctl-x to exit, and say 'y' to save the file.


I elected NO for the update checker option.  I followed your instructions above.  Pop-ups persist.

If anything was clear, easy or self-evident about most things digital, there wouldn't be hundreds of user guides on the same subject in bookstores, forums like this one wouldn't exist, and this thread wouldn't occupy three pages.

Anyway, I appreciate your effort.

---

### Post by nanotube on 2007-07-24
> **daktari said:**
> I elected NO for the update checker option.  I followed your instructions above.  Pop-ups persist.

If anything was clear, easy or self-evident about most things digital, there wouldn't be hundreds of user guides on the same subject in bookstores, forums like this one wouldn't exist, and this thread wouldn't occupy three pages.

Anyway, I appreciate your effort.

did you check again with crontab -l to see if that item was actually removed?

also, try a "sudo crontab -l" to see if it maybe got into root's crontab?

also, open up system log (system>administration>system log), and see what you've got under user.log, marked with UBUNTUZILLA. just to make sure it is ubuntuzilla doing the popups and not something else... 

if it is ubuntuzilla doing the update notifications, we'll get to the bottom of this, eventually. :)

---

### Post by daktari on 2007-07-26
> **nanotube said:**
> did you check again with crontab -l to see if that item was actually removed?

also, try a "sudo crontab -l" to see if it maybe got into root's crontab?

also, open up system log (system>administration>system log), and see what you've got under user.log, marked with UBUNTUZILLA. just to make sure it is ubuntuzilla doing the popups and not something else... 

if it is ubuntuzilla doing the update notifications, we'll get to the bottom of this, eventually. :)

Clear on all counts - it was removed; didn't make it to root; and now, no pop-ups.

I'll take a stab at an accurate technical explanation of how the pop-ups stopped.

I re-booted the system eleven times - just out of angst - each time re-testing the browser until the problem disappeared.  I did this under the theory that if you do something the same way repeatedly, eventually the action will produce a different result (yuk-yuk).  Probably out of nothing other than pity for me, this probably prompted the Digital Spirits to cast clean-up spells on my system... or eleven was the magic number after which my box actually purged the removed update.

There were other browser issues that existed and persisted as well (after the "upgrade") - such as extension / add-on malfunctions.   Those too disappeared after the eleventh re-boot.  And just in case there is any doubt about the seemingly unrelated browser malfunctions, I'm pasting here an excerpt from the author of one of those extensions in which he had something *unsolicited* to say about OS-centric browser builds.

//

*Did you recently upgrade your copy of Firefox?*

[I]Typically, the error you see occurs on Linux systems when an official
Mozilla build of Firefox 1.5 is not used (many people use the builds
provided by their Linux distribution, which is usually fine). The
problem is caused by an incompatibility between a compiled library
that is used by Page Saver on Firefox 1.5 and the Firefox executable
itself. Your choices are either to upgrade to Firefox 2 (where
Page Saver does not need to use the compiled library) or to try a
Linux build provided by Mozilla.[/I]

//


There endeth the story (so far).  Go figure.

---

### Post by nanotube on 2007-07-26
hehe, go figure, indeed. :)

---

### Post by daktari on 2007-07-27
> **nanotube said:**
> hehe, go figure, indeed. :)

Guided strictly by the Mystic Eleven-Reboot Rule, I read the extension / add-on author's reply eleven times.  Now I'm thinkin' I should try the *upgrade* eleven times.

N-O-T.

So back to **one** of my original questions:

Do Ubuntu and Mozilla intend to come to terms and release an Ubuntu'd Firefox 2.x (and / or subsequent versions) which auto-updates with the rest of **LTS** components ???

Or are we stuck with 1.5 as the last Ubuntu'd auto-update version for **LTS** ???

I know, I know:  that was ** two** questions, not **one**.  

Maybe if I ask eleven times...

:)

Oh well, at least I don't get Windows pop-ups on my Ubuntu box like this one.

---

### Post by daktari on 2007-08-01
Addendum

Today on a lark, **I ran an *unprompted* update**:
sudo 
apt-get clean
apt-get update
apt-get upgrade

**The update grabbed these**:

Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1 [76.6kB]

Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1 [149kB]

Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libnss3 2:1.firefox1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1 [715kB]

Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.13~prepatch070731-0ubuntu1 [7970kB]

My firefox still shows version 1.5.0.12, though the above update shows a 1.5.0.13 "prepatch".

Don't get it, but there's a hint of progress.

---

