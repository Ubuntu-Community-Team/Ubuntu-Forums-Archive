---
title: "Firefox Error: Security Component"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by duckchik on 2007-03-13
Whenever I open Firefox when no other Firefox windows are already open it comes up with this error:

"Could not initialize the browser's security component. Most likely caused by problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features."

I also noticed at about the same time that the Help button is missing from my Panel and Add/Remove is missing from Applications. 

I am still learning Ubuntu. I tried to find out which version I have but when I clicked on "About Ubuntu" under the System menu it came up with "Could not launch menu item. Failed to execute child process 'yelp' (No such file or directory)"

Thanks for your help!

---

### Post by overkillm on 2007-03-15
I'm getting the same error with Firefox, after following the guide here:

[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

to install the Mozilla distribution of Firefox instead of the standard Ubuntu one.

I've attached a screenshot of the error dialog I get whenever I start Firefox now... but duckchik's post pretty much gives the text verbatim.  I'm not having the same issues with yelp or Synaptic, though.  Anyone out there able to help us?  Please?  :?

Thank you!

---

### Post by overkillm on 2007-03-16
Oh... hah... whoops.  I realize what I did wrong.  I skipped the step in the FirefoxNewVersion instructions where you restore your backup profile to the new install directory.  :oops:   Everything's peachy now.

duckchik, I'm a total noob, so I wouldn't take anything I say as gospel, but I did notice the following in the instructions I was using to replace Ubuntu's Firefox with the version from the Mozilla site:

> 
Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine.


It sounds almost exactly like the issue you're having.  Did you try to uninstall Firefox at any point?  Or, I don't know, do an incomplete install of something else that uses the Gecko engine?  I'm not sure how to go about fixing the broken packages... maybe using apt-get or aptitude from the command line to repair or re-install the packages?  Seriously, I'm just taking stabs here.  But maybe it's worth checking into.  Wish I wasn't so green and could be of more help.

---

### Post by ranamalo on 2008-03-17
I have found a solution for the following error in ubuntu and debian

Could not initialize the browser's security component. Most likely caused by problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behavior when accessing security features

Go to your user's profile:
cd /home/user/.mozilla/firefox/profile  (note:profile is usually some crazy number, letter combo followed by .default.  However if you have made your own profile, it will just be the name you gave your profile)

then give your user read/write access to the .db files

chmod +rw *.db

that's it.  it worked for me

---

### Post by Bankofengland on 2008-05-12
I had the Security Component error message. 
Tried uninstalling / reinstalling.
Tried changing read write permissions.
Tried Deleting User Profile.
Even tried sudo apt-get purge firefox.

Nothing worked.

Then I went to my home folder and changed view so it would show hidden items.
I went into the folder called .mozilla
And deleted the firefox folder.

Upon restarting firfox it worked fine.

I know it may delete your bookmarks and preferances. 
I know it's not very elegant.

But it works for me now.

---

### Post by kblcuk on 2008-07-04
Nothing above worked for me. ):
no cert8.db file around, it even doesn't get generated with the new profile!

anyone else had similar problem?..

**upd:** installing Firefox using the package from Mozilla and following [FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion") guide worked just fine. Same thing for the Thunderbird.

---

