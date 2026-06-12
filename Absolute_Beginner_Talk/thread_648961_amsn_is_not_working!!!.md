---
title: "amsn is not working!!!"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-24
Amsn is acting very weird!!

Take a look at the screenshot, please. As soon as I start up Amsn, that's what I get. Just blank.. 

It happened after I tried to change font and set up to automatically log in when starting amsn. I think it has to do with automatic log-in thing. I tried to undo the change in setting but can not do it in preference.

I uninstalled it by aptitude uninstall amsn...   also package manager (competely uninstall) .... then reinstall it 4 times..  I still get the blank.. on the front page

anyone has the same problem???  What's wrong with it?

---

### Post by seshomaru samma on 2007-12-24
I don't know what is wrong. But you probably have amsn's settings saved in some dotfiles in your home directory so even after you uninstall it it keeps getting back to the old settings 
After you uninstall go to your home folder and delete the folder named .amsn. It's a hidden folder so you will need to enable viewing hidden files, in nautilus and thunar you can do it with ctrl+h or view>show hidden files.
I had a similar problem with font changing , I had to reinstall

---

### Post by taekr on 2007-12-24
Thanks a lot. I remove the hidden folder of amsn but reinstalled it. It's working now.

---

