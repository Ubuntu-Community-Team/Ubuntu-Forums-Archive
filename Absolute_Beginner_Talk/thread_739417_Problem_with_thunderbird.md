---
title: "Problem with thunderbird"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ahurd on 2008-03-29
I am on Kubuntu gutsy. My thunderbird was working fine until I copied a backup "local folders" directory into the profile, unfortunately without keeping a backup of the original, and now I get no mail. I tried uninstalling and reinstalling but still no mail. I think I will have to totally remove all directories attached to thunderbird and start over, but I am not sure this is correct, and whether something will break if I do it. Could anyone help?

---

### Post by Victormd on 2008-03-29
Try typing  in the terminal > thunderbird -profilemanager

The default location of the thunderbird profile is on the local folders and by copying a backup, depending on how old the backup was, and whether or not you've re-installed thunderbird after the backup, the directory names may not be the same

---

### Post by ahurd on 2008-03-29
Thanks but didn't help.

---

### Post by rkd on 2008-03-29
There might be easier ways to fix it, but uninstalling, getting rid of the whole Thunderbird profile, then reinstalling certainly should fix the problem.  

If you have any important email saved in Thunderbird, you can go into the profile and copy out the individual mail data files, not whole directories, to keep them somewhere safe while you uninstall, wipe the profile, and reinstall.

After you get Thunderbird reinstalled, configured, and working properly again, you can shutdown Thunderbird, change the names of the mail data files you kept, copy them into the profile into the same directory as the other mail data files, then when you start up Thunderbird, you should see those saved files in Thunderbird's folders list on the left and you can either just leave the email in those new folders or move the messages from those folders to wherever you want to keep them and delete the now empty folders.

Of course, if you don't want to save any of your email, don't bother with any of that -- just uninstall, wipe the profile, and reinstall.

---

