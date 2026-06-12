---
title: "Evolution doesnt start - resolution"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by mavila on 2007-10-22
I had a recent issue in Gutsy that Evolution would not start, hanging with the issue "CalDAV Eplugin starting up". I have several IMAP accounts configured, two POP and an exchange account as well.

I had "just" made a change to the exchange account (added a Global Catalog server name" that was not valid. This completely locked up evolution to the point it wouldn't start at all.

The resolution was to, from a console, do a;

"sudo evolution" 

and see if that will open any type of screen (mine was the beginning configuration. If thats a go, then simply close it out (yopu know that evolution isnt "that" broken). Then again, from the command line, enter the following;

"sudo evolution --disable-eplugin"

That started up evolution for me! I then went BACK to the preferences and deleted the 'bad' Global Catalog server name, closed out with "okays" and restarted evolution from both the Command line and the menu-bar shortcut.

Hope this helps (searching for a fix was a nightmare for me)

Cheers

---

### Post by red_five on 2008-03-03
I had a slightly different symptom and cause, but this worked for me as well. Evolution would hang on startup when prompting for a new Exchange password (due to AD-enforced password change interval). It would display the password dialog, allow me to enter 2 characters of my password, then would display the main window with indications that it was attempting to connect to the server and download mail. At that point, it was done, and I could only kill the process.

--disable-eplugin (I found I didn't need sudo) did the trick. I was able to change the saved password in Evolution, then close out and open again to reenable Exchange, and Bob's your uncle.

---

