---
title: "[SOLVED] I have messed up both opera and firefox and I need to start over"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-04-20
OK, I am runnint 7.10 on a two-year-old Presario V2000 and recently I tried experimenting with beta versions of both Firefox and Opera. They are both buggy as heck (at least it seems so to me) and I want to revert back to the way things were but no matter how many times I try to uninstall and re-intall or force version I am stuck. I need actual help here, not "use synaptic" or "just download them again", please.  :-)

The thing is I have been messing with this for quite a while not and things have gotten progressively worse. I feel like all my attempts to follow flippant advice or do things myself have just dug me deeper and deeper into a whole. For example, whatever I have done to Opera has made it so that I have to  type an entire sentence and then wait for a second for the text to appear, and  I can no longer  access websites that use flash. 

I have tried marking for complete removal and then reinstalling and that did not work, the same buggy betas are still the ones that come up when I click on the icons. I was able to download the stable version of Firefox to my desktop and I can actually get it to work but I can't get it to install the proper plugins and the only way I can run it is to click on the proper folder, when I click on an icon it is the 3.4 beta that comes up.

I am completely effed.

---

### Post by LaRoza on 2008-04-20
I am not sure what the problems are (I use Opera 9.50b for months now).

Uninstal them and delete the .mozilla and .opera directories in your home folder (press Ctrl + h to see them)

Then reinstall the versions you want.

---

### Post by zvacet on 2008-04-20
For Opera 9.27 you will need older flash.

---

### Post by ajgreeny on 2008-04-20
I think LaRoza has probably got the problem for you.  Doing a complete uninstall gets rid of everything except your own configuration changes in /home/user/.mozilla and /home/user/.opera folders.  Try renaming these and then reinstall the apps again and see if a new profile without all the addons etc makes things work better.  You may have just been unlucky andf changed something in your own configs that the system won't put up with.

---

### Post by TenPlus1 on 2008-04-20
To re-install Opera 9.27 you will need to delete the hidden directory .opera in your home folder before doing so, this will reset everything back to defaults, but remember you have to use an older version of flash for it to work... r48

Deleting the same .opera folder and installing the NEW opera 9.50 will allow you to use the current flash plugin that Firefox uses, here is the link to the latest version:

[http://snapshot.opera.com/unix/snapshot-1929/intel-linux/opera_9.50-20080417.6-shared-qt_i386.deb](http://snapshot.opera.com/unix/snapshot-1929/intel-linux/opera_9.50-20080417.6-shared-qt_i386.deb)

---

