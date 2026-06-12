---
title: "[SOLVED] ndis&amp;gt;apt-get&amp;gt;hal failures... cant even start now"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Gripp on 2007-11-24
okay
i've tried being independent and searching and following instructions but all it has done is screw my comp... please help

full story:
i installed kubuntu with wubi 7.04 two days ago
and started following all the fun stuff to get ndiswrapper installed so that my linksys wireless-g card would work (wusb54g)
started by trying to uninstall any drivers and current installs of ndis per the post i was following
basically nothing worked with that, but i figured that just meant nothing was there for it to uninstall...
so i went about installing ndiswrapper-common (rather than the utils that the post said, being that the utils version didn't exist and all...)
and got the drivers for my card working - ndis was even showing the driver and hardware as present
but looking at ifconfig no wireless cards were running
i tried rebooting - nothing
so i followed the advice from the full ndis install help page that said to make sure that the defualt ndiswrapper is uninstalled when using ubuntu - yet i'm thinking, well, there weren't any
but so i unstalled everything again
but now, while trying to uninstall it tells me i need to manually run dpkg --configure -a
i did and rebooted and got the ndis uninstalled - it said reboot, i did
upon rebooting this time i couldn't use apt-get becuase it was saying some in a dpkg folder was in use... i had this info written in a notepad but i cant get to it right now
so i tried running adept to see if it wasn't what was cuasing the issue and it said the same error, but gave me option of it trying to resolve the issue - i tried, it crashed... tried again, it crashed again
i have that crash info on a file too - but, again, i cant get to it
so i let it sit for about 30minutes to see if whatever was being used gets finished doing its thing - no luck
so i restart the machine again and now it works except instead of a file being in use it errors out trying to use any apt-get command, saying something about dependencies... but i noticed the error starts with it trying to start the hald layer whatever whatever
i tried restarting a couple of time from this point but no luck
tried using adept to reinstall hal but no luck
tried running dpkg --configure -a again, but no luck (same errors)
found a thread saying to go to /etc/init.d/rc file and change concurrency=none in one post - looked and it was already set to none
then a few posts down it said to move a set of files from one dir to another and set concurrency=shell
i did
upon trying to reboot it couldn't finish the shutdown process saying that it didn't have permissions to the rc file i had just changed...?
hard booted the machine... :( upon restart got a different error but still relating to that file
wont even get to the point that i can login - it just halts after that error and gives me no other option to to kill the machine some more...

even more - now that i have gotten back into my windows install it is telling me that i don't have permissions to a number of things in windows......?? like change my screen resolution for example...
i was thinking of reinstalling from wubi altogether until my windows started giving me issue... now i dont know what to do
help?

---

### Post by markharding557 on 2007-11-24
i think installing linux mint which is based on ubuntu might be an option for you,this has a ndiswrapper gui installed by default.
you should not need to keep rebooting linux it usually is'nt necessary unlike windows.
moving the files that you moved from /etc/init.d/rc back to their origional location may resolve your permissions problem

---

### Post by Gripp on 2007-11-24
but i cant even get into linux to move those files...

---

### Post by Gripp on 2007-11-24
man the posts move quick on this site - a short 2 or 3 hours has passed and i'm on page 5..!
not sure if bumping helps... but TTT..

---

### Post by Gripp on 2007-11-25
FYI
i'm marking it solved not b/c it atually was
but b/c i just went ahead and did a fresh install

i think these problems may have had something to do owith me assuming that wubi installed the latest version - but i found it actually installed 7.04 - so i was following bad instructions


though, my newest post is also of a hald boot error... again
seems like a common issue and i cant find anywhere on the forums that provides a fix...

---

