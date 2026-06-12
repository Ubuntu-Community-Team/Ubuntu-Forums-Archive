---
title: "Copy /home backup to Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-10-22
I have made a backup of my /home directory in Feisty.  "WHEN" I decide to upgrade to Gutsy, is it possible to just copy that backed up of the  /home directory to the new Gutsy to retain all my previous programs and preferences? This is my first upgrade and want to make sure I don't blow it.

If so, is there any special way to do that or can I just copy over the new Gutsy /home directory?

Thanks!
Tony

---

### Post by philinux on 2007-10-22
The best way for this is to have home on its own partition.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Tony3286 on 2007-10-22
I had previously read that link. Basically my question is  - when you download Gutsy is your /home directory basically empty and a previous backup can be copied to it to retain all your previous information?

OR, by putting your /home directory on a separate partition , avoid the need to backup  /home and then have to copy that in the original Gutsy partition?

---

### Post by shad0w_walker on 2007-10-22
The short answer is: Yes

You can copy your home folder across without any major issues. You won't retain all your programs unless you install everything to your home folder (Which is fairly doubtful) so you will need to reinstall them but your settings will be preserved in the home folder.

---

### Post by mikeyphi on 2007-10-22
Your personal configuration is on the hidden folders in your Home folder. If you Upgrade - successfully!! - most of you configuration will be OK - (there will be some new stuff from changed packages)

If you just do a fresh Install - you will, of course, loose your old configuration info.

You could 'save' your home folder and just overwrite the 'new' home folder - I haven't tried that so don't know if there any issues. (Which is basically what you asked!)

I think most people just save personal data from the home folder (not config data) - theer's no problems importing that into a new install.

---

### Post by Tony3286 on 2007-10-22
Thanks so much for your replies. I was planning to do an upgrade in about a month, but noticed a lot of people recommend fresh  installs. I was just thinking ahead if I did do a fresh install, how I could get
back to all my preferences, etc the easiest way. Looks like theres no real easy way.

Thanks again!
Tony

---

### Post by akiratheoni on 2007-10-22
Well, some programs allow you to export your preferences... so if the program allows you to do that, that's the best you can do to back up I guess.

---

### Post by shad0w_walker on 2007-10-22
Pretty much every program stores its preferences in your home folder, in hidden folders. Just backup the whole home folder and you should get your preferences as well. You will need to reinstall the applications though.

---

### Post by philinux on 2007-10-22
The sep partition is the best way to go. It still needs backing up just in case of hard disk failure. 

You can just drop the config files back into home or just the whole home folder,  just do it from a live cd

---

