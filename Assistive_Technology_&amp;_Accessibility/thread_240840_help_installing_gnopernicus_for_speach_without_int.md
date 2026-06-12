---
title: "help installing gnopernicus for speach without internet"
date: 2006-08-21
forum: Assistive Technology &amp; Accessibility
---

### Post by krmane on 2006-08-21
hello I am Krishnakant from India.
I have just started to use ubuntu.
I havbe one question on version 6.06 update 1.
I have a couple of computers where internet connection is not working and will be disconnected for next 2 days because of a major technical problem.
now my problem is that I am a visually handicap person and want to use gnopernicus on ubuntu.
as I said above I don't have internet connection and I can't wait for 2 more days.
I already downloaded gnopernicus .deb package and festival deb package from the ubuntu web packages web site.
I want to know how I can install it when internet is not there.
I heard that if internet connection is not there, I will have to take care of the dependencies myself.
is there a way to create an artificial reposetory on a new blank cd and install the packages needed without connecting the to internet?
and yes, what dependencies should I download for nopernicus to work?
thanks.

---

### Post by Henrik on 2006-08-23
On a standard Ubuntu 6.06.1 Gnopernicus and Festival should already be installed. 

You need to activate the accessibility framework and the magnifier or screen reader in the Accessibility Preferences (under the System menu). 

Log out and back in and the tools should start automatically.

---

### Post by krmane on 2006-08-23
On a standard Ubuntu 6.06.1 Gnopernicus and Festival should already be installed. 
Yes I think so because when I try to install it I get a message that it is already installed.
You need to activate the accessibility framework and the magnifier or screen reader in the Accessibility Preferences (under the System menu). 
right now I don't find a way to do it with keyboard.  I am new to ubuntu and I don't quite know gnome also.  can you give me shortcut keys to setting up accessibility with festival and gnopernicus?
Log out and back in and the tools should start automatically.
again, I want some shortcut keys which I can use for this process.
thanks, krishnakant.

---

### Post by Henrik on 2006-08-24
> right now I don't find a way to do it with keyboard.  I am new to ubuntu and I don't quite know gnome also.  can you give me shortcut keys to setting up accessibility with festival and gnopernicus?

There is no direct way of doing it but these should work with a standard English setup:

Alt+F2 for the general application launcher
type gnome-at-properties and press Enter
Press space to activate the at-framework
Press Down and Space to select the screen reader
(Down and Space again if you also want the magnifier)
Alt+L to close and Log out

(this process will be simpler when we start using Orca in Edgy)

---

### Post by krmane on 2006-08-25
There is no direct way of doing it but these should work with a standard English setup:

Alt+F2 for the general application launcher
type gnome-at-properties and press Enter
Press space to activate the at-framework
Press Down and Space to select the screen reader
(Down and Space again if you also want the magnifier)
Alt+L to close and Log out
thanks a lot for those commands.
actually I finally got gnopernicus activated and it did speak.  but the problem now is that on the ubuntu 6.06.1 desktop it does not talk every thing I start ubuntu.  as soon as I log in on my gnome desktop the gnopernicus menu with startup mode and preferences etc comes up.  but it does not speak.  infact I just herd it two times.  first when I changed all things as per your suggestions and second when I had rebooted the next morning.  after that I had powered off and rebooted many times but gnopernicus only shows up visually but no speach.  I checked that my sound card is working because when I log in the startup sound can be heard.  even the menu selection sound set by my sited colligue (from the theems) is working.  so what could be the problem?  by the way when I got gnopernicus actually talking for the first time, I tried to change the rate and pitch but it had no effect.  is my sound card the problem?
I am using a creative vibra 128 sound card and it is selected as cyrus logic.  is that the problem?  any other things you will like me to check?
(this process will be simpler when we start using Orca in Edgy)
I don't mean to offend the developers of gnopernicus, but is orca any time better than gnopernicus?  will it also work with firefox and open office and other related tooles?
thanks, Krishnakant.

---

### Post by Henrik on 2006-08-25
You should try turning off ESD sound mixing under the sounds preferences. That might be causing a conflict.

Many people feel that Orca is already performing better than Gnopernicus. It works well with OpenOffice, but Firefox (itself) needs some work.

---

### Post by krmane on 2006-08-25
You should try turning off ESD sound mixing under the sounds preferences. That might be causing a conflict.
Henrik, can you please provide a short cut keys for this too!

---

