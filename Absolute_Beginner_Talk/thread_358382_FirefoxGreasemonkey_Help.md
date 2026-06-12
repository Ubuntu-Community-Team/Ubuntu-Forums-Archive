---
title: "Firefox/Greasemonkey Help"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-02-10
I need to edit one of my user scripts for Greasemonkey, but for that, I need to find Kate or Kwrite and where the .exe (or whatever extension for it is in Kubuntu) for one of them is so that I can edit. Telling me where in my directory the Firefox profiles are located would also help since I can edit from there.

---

### Post by Happy_Man on 2007-02-10
Your Greasemonkey scripts should be located in home/Username/.mozilla/firefox/gm_scripts. Hope this helps!

---

### Post by i-am-me on 2007-02-11
Thanks a whole lot! It's slower than just clicking the edit button in the "Manage User Scripts" dialog, but at least I can actually edit them. I would prefer finding where Kate is (I'm lazy) since it's easier and quicker, but for now, this'll do.

---

### Post by tc101 on 2007-03-07
I installed grease monkey.  When I click "Tools/Greasemonkey/New User script" a pop up box asks me to choose and executable text editor.  I want to use gedit but do not know how to select it (I am new at ubuntu).  Where is gedit located and how do I select it?

When I select the properties box for it, I see the command gedit %U.  What does that mean?  Does the U% tell me where it is, or tell me something else?

---

### Post by i-am-me on 2007-03-07
> **tc101 said:**
> I installed grease monkey.  When I click "Tools/Greasemonkey/New User script" a pop up box asks me to choose and executable text editor.  I want to use gedit but do not know how to select it (I am new at ubuntu).  Where is gedit located and how do I select it?

When I select the properties box for it, I see the command gedit %U.  What does that mean?  Does the U% tell me where it is, or tell me something else?

I was able to find kate (the KDE editor) later on in the binaries. You could look in /bin, /sbin, or any other folder in the system that contains the abbreviation *bin* (for *bin*ary). If you're too lazy or busy to look, then you can always go to your home directory, view the hidden folders (if you type in a  "."  (period) in the little browsing area at the top, (I'm not sure if nautilus does this, it should though), it should show you all the folders that begin with  a  "." These are the hidden folders. You could also go into a menu at the top (it's probably under the view menu) and check off view hidden files). There should be one called ".mozilla". In there it should contain your profile (usually default********). In that folder you can browse to your extensions, then greasemonkey scripts and edit the script that you need to edit as long you know the name of the script.

---

### Post by tc101 on 2007-03-08
Thanks.  I found it.  It is under usr/bin/gedit

---

### Post by tc101 on 2007-03-08
I am using Ubuntu linux,  firefox 2.0.0.2, and the newest version of Greasemonkey which I just installed.

I downloaded and opened the helloworld.user.js in my browser.  
I clicked tools/greasemonkey/install new script.  Nothing happened.  There is an install button just above the script.  I clicked that get a message saying "Error installing Userscript. Type Error: Script has no Properties"

What am I doing wrong?

---

### Post by i-am-me on 2007-03-08
> **tc101 said:**
> I am using Ubuntu linux,  firefox 2.0.0.2, and the newest version of Greasemonkey which I just installed.

I downloaded and opened the helloworld.user.js in my browser.  
I clicked tools/greasemonkey/install new script.  Nothing happened.  There is an install button just above the script.  I clicked that get a message saying "Error installing Userscript. Type Error: Script has no Properties"

What am I doing wrong?

Are any of your scripts working? When I first installed Greasemonkey, my scripts worked, but a day or two later, things stopped working for me. I don't think Greasemonkey has full support for (K)Ubuntu/Linux yet. Our best bet would be to email the creator of Grasemonkey and ask them to fix this problem in a future release. In fact, I'll try that right now......

---

### Post by tc101 on 2007-03-09
The scripts that I install from the web site work fine.  My problem is installing my own scripts.  I know this is not caused by syntax errors because even if I make an EXACT  copy of another script and try to install it I get the same error.

---

### Post by i-am-me on 2007-03-09
I can't help you on that then. Maybe it's it's just that Greasemonkey isn't fully compatible with Linux. Try placing the [scriptnamewithoutspacesorcapitals].user.js directly into the scripts folder I mentioned in the profile folder.

---

