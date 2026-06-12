---
title: "Firefox 2.0 Installation Problems"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by bobaj on 2006-12-20
I just followed the instructions to install firefox 2.0.  Now when I start firefox I get errors about the profile.  The error message indicates that SSL protocol has been disabled.  I'n preferences the SSL 3.0 radio button has been selected.  I can not connect to SSL sites.

This was working before with 1.5, not with 2.0.  How can I get Firefox 2.0 working?

Thanks
Bobj

---

### Post by aysiu on 2006-12-20
Can you explain exactly how you went about installing Firefox 2.0? Please be as specific as possible.

---

### Post by bobaj on 2006-12-20
I followed the instructions on this website:

[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

I can not go to that site because SSL not work.  I can't go to any site that has SSL protocol.  I ran the commands manually.  One of the commands after calling firefox from the terminal window failed because it could not find the directory ~/. moxilla??? something.  Where should that file be?  I don't understand the syntac ~/.mozilla

Thanks
Bobj

---

### Post by bobaj on 2006-12-21
Can anyone help me - or direct me to someone who can help??  My browser is down and I have to go to some one else's computer to get onto the internet.  The Ubuntu desktop is useless to me if I can not connect to the internet.

Please help!

Bobaj

---

### Post by aysiu on 2006-12-21
Well, why don't we solve the first problem, then? You don't have to use Firefox as a browser. Install and use another browser until you get Firefox working again: ```
sudo aptitude update && sudo aptitude install epiphany-browser
``` You can use Epiphany for now.

~/.mozilla means /home/bobaj/.mozilla
That is where your Firefox settings live, and any directory that starts with a . is a hidden directory, so if you went to /home/bobaj, you wouldn't see .mozilla unless you pressed Control-H.

To install Firefox 2.0 properly, use this script. I'm not sure what the deal is with your SSL protocol, but this script is much faster than copying and pasting all those commands:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by bobaj on 2006-12-21
Thank you for the lead.

I downloaded the psycocats script and ran it, but it bombed on the .mozilla/firefox commands.

When I checked my Unix books and recalled that the period in .mozilla indicated it was a  hiden file, I did an ls -al on the .mozilla directory and found that it was assigned to root root.  

I used chown and chgrp to reassign ownership and group to my username and reran the script - which got further but bombed, this time indicating that 3 files were inacessible due to permissions.  An ls -al verified that 3 files were assigned to root root.  I used chown and chgrp to reassign ownership and group to my username.  Maybe I should have used chmod to reassign rwx privledges.  But I assumed that those were set correctly- or hoped they were- by the program that placed them in the first place.

This third time the script ran fine and executed with the sucessfully installed message.  So far Firefox 2.0.0.1 is running on the Ubuntu desktop.  Hopefully it will tomorrow.

I don't know why there was a mixture in ownership and group assignments in the .mozilla directory.  Until your email pointed me to the Unix book, I had totally forgotten about hidden directories - so I have no idea how these got assigned (or changed) in the process.

Anyway changing ownership and group for all file assignments in .mozilla and .mozilla/firefox to username username  - and using the pyscocats script you mentioned - worked.  I don't know if I caused more problems down the road.

Thanks for your help. Time for some sleep.
Bobaj

---

### Post by _simon_ on 2006-12-21
You can just download Firefox from the mozilla site and extract it to your desktop and run it straight from there if you want to.

---

### Post by aysiu on 2006-12-21
> **bobaj said:**
> 
I don't know why there was a mixture in ownership and group assignments in the .mozilla directory.  Until your email pointed me to the Unix book, I had totally forgotten about hidden directories - so I have no idea how these got assigned (or changed) in the process. I don't know for sure either, but I suspect it might have something to do with this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

That's the only time I've seen ownership change suddenly.

---

### Post by aysiu on 2006-12-21
> **_simon_ said:**
> You can just download Firefox from the mozilla site and extract it to your desktop and run it straight from there if you want to.
You can, but then it won't use any of your plugins installed via the package manager. You'll also have to specify the directory path in order to run it instead of just using *firefox*.

---

