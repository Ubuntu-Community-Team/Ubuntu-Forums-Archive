---
title: "Firefox bookmarks new folder abort, also Check If Already Posted button abort"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-27
I have used Synaptic to completely uninstall then install twice.  But the problem is persistent.

When I post new thread then click "Check If Already Posted" button then program aborts.  No message, no firefox.  I have to restart the program.  This also happens I click Bookmarks > Bookmark this page > Show all bookmarks folders > New folder > Type any letter.

If someone would help with this I would be grateful.

Thank you

---

### Post by Moop on 2007-05-27
Maybe your profile is corrupted. When you uninstall firefox it doesn't delete your profile. The profile is stored in your home folder. You will need to enable hidden files to see it. Try uninstalling firefox and then deleting your profile folder. Reinstall firefox.

---

### Post by ICUR2Ys on 2007-05-27
OK

I will give that a go.  Thank you very much.

---

### Post by ICUR2Ys on 2007-05-27
Well I don't think I accomplished anything.

I moved to trash the directory firefox from my home directory.  That was the only thing that I could associate with firefox.

However, upon install all plugins are still there and the problems as well.

I need more direction, I guess I can't figure it out on my own yet.

---

### Post by ICUR2Ys on 2007-05-27
Fortunately I had just ordered an external hd.  So if I can't fix this somehow by the time the hd arrives, then I will copy all of my files to the ext hd and reinstall the entire system.  I think that will cure the problem.
So now I wait :)

---

### Post by Moop on 2007-05-28
I don't know why that didn't delete your profile. You can run the profile manager from terminal
```
firefox -profilemanager
``` and create a new profile and or delete your old one. 

Also if you haven't you can update to the latest firefox by using the script found here.
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox")

---

### Post by ICUR2Ys on 2007-05-28
Thank you, I will try that right now.  I will do a complete uninstall first.

---

### Post by ICUR2Ys on 2007-05-28
Thank you.

That worked.  I just entered the command without uninstalling firefox as I intended.  It didn't give me any options as I expected.  I just wanted to see what it was before I uninstalled firefox.  After running it I decided to check the problem not believing that if would be fixed yet.  Boy was I pleasantly surprised.

I can't thank you enough for your help.  I will sleep well tonight.

---

