---
title: "firefox wont save bookmarks [Resolved]"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by kroiz on 2006-12-16
hi,
 I noticed my firefox wont save bookmarks and sites login info.
I found a firefox folder under opt.
this folder has root as a owner and group and other have r_x.

should I just change the permission of the firefox folder so that everybody would have write permission?
Or should I change owner of firefox folder to my user?

BTW, is the firefox under opt is the firefox that executed when I click the icon on my gnome upper pannel?

---

### Post by aysiu on 2006-12-16
Firefox in /opt is where all the program files live. The bookmarks file in there is the default set of bookmarks.

Your own personal bookmarks are stored in ~/.mozilla (also known as /home/kroiz/.mozilla). Any folder starting with a period is a hidden folder, so you'll have to press Control-H to see it.

To be sure you have ownership of your ~/.mozilla folder, paste this command into the terminal: ```
sudo chown -R kroiz:kroiz /home/kroiz/.mozilla
``` If *kroiz* isn't your username, substitute in your actual username.

---

### Post by kroiz on 2006-12-16
)-:, that did not help. I run the command and also looked in that folder I Am the owner of all the content there.
could it be because of execute permission? most of the files under ./mozilla dont have x permission.

---

### Post by kroiz on 2006-12-18
The problem was indeed that there was no execute permission.
once I added the recursively to all .mozilla subdirs all my problems were gone.

---

### Post by stuartbh on 2007-05-31
To whom it shall concern:

It is of interest that I had a problem with saving bookmarks in FireFox under MacOS, and found that the reason was that a ".parentlock" file needed to be deleted in the ~/Library/Mozilla/Profiles/default/ndvs2o88.slt directory.


V/R,

Stuart

---

