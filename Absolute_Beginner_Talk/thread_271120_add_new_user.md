---
title: "add new user"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by mikl2 on 2006-10-04
I want to give my wife a seperate account to login to.  I would like her to boot into Ubuntu with her own username and password.  She only surfs the web and emails......some solitaire too.  I'm 3 weeks new into Linux, so please be kind.  I don't mind the command line, and willing to learn.  One concern would be:  Will she have "flash and java" in firefox?  I have the plugins on my account. Will the plugins work, if she logsin to her own account?  What about email? 
I've searced the forum (add user), but didn't find what I needed.
Will there ever be "wizards" in Ubuntu?  I guess I'm too MS orientated.
Can you help?
Thanks

---

### Post by bluefrog on 2006-10-04
system/administration/user

use this gui to add users, it will be simpler for the time being.

add a user, login with the new username and test firefox.

should be ok.

James

---

### Post by bswilson on 2006-10-04
Sir, bluefrog gave you all that you should need.  If Firefox isn't playing nicely, write back to let us know, and we can help you fix that part.  Good luck, hope you're enjoying Ubuntu!

---

### Post by mikl2 on 2006-10-04
Geez....that was too easy.  I was shocked to get a reply to use a gui resolution.  I expected a list of sudo commands.  Don't misunderstand me.  I'm not complaining!  Thank you.
Now.....Firefox did not import my profile to her account.  I kind of expected that.  I need to import Bookmarks and the flash and java plugins from my account.  Is this a difficult task?  I'm guessing a "import/profile" or something like that.  Can I get a walkthrough?

---

### Post by bluefrog on 2006-10-04
log in with your username.

open a terminal (applications/accessories/terminal)
write the following
gksudo nautilus
(enter your password)
(mind what you are doing, you are browsing your computer with super user account)

in nautilus menu click on view/show hidden files
righ-click on .firefox and select copy.
go to /home/wife/Desktop/  and paste

close nautilus
write in the terminal (change words accrodingly to your config)
sudo chown -R your-wife-account /home/wife/Desktop/.firefox     (mind capitals if any...)

then when you log in as your wife you will be able to copy paste whatever you want (bookmarks.html) using nautilus (the file explorer) from this /home/wife/Desktop/.firefox to /home/wife/.firefox

for the plugins sorry can't help you right now, I haven't a linux box running and I install the plugins differently from what you did.

James

---

### Post by pay on 2006-10-04
Try ```
cp -r /home/OLD_USER/.mozilla /home/NEW_USER/.mozilla
```I'm not sure but you may need to use that command as root. If so add sudo infront of the command and when your done do```
gksudo nautilus
```then browse to the /home/NEW_USER/.mozilla right click at select properties-->File Permisions and change it to NEW_USER. Btw .mozilla is a hidden folder (view--> show hidden)

---

### Post by pay on 2006-10-04
James and I said the same thing. Try his way. I seems better presented.

---

### Post by mikl2 on 2006-10-04
Mission accomplished as per bluefrog.  Thank you for the walkthrough.  I hit a few bumps on the way, probably human (me) errror, but all is well.  Thank you.  
I've been hitting this Ubuntu thing pretty heavy for 3 weeks now and I'm still  apprehensive about getting things done.  How long does it take to get somewhat proficient at Linux?  Not to the level of IT professionalism, just to navigate, customize, install in Ubuntu.  Thank God I'm not having to deal with networking!

---

