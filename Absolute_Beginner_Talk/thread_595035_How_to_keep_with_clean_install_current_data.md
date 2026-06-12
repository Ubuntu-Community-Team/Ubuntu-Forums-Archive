---
title: "How to keep with clean install? current data"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by BoJon on 2007-10-28
I am getting ready to do a clean install, but want to save current data.  Know i need /home in separate partition but any other directories such as /user.  A manual install will let me not overwrite the separate partitions, right?  Any other suggestions?  Thanks.

---

### Post by MaximusTG on 2007-10-28
What is it that you are so intent on keeping? Installed applications? Config's? Are there any specific problems you faced that you fixed during the last installation that you don't know how you fixed them anymore?

Else you could simply backup your system as it is now. Then do a clean install. If you need any config files from your old system, simply copy them from the backup. 

Also, if you have your /home on a separate partition, all your user settings will be kept (theme etc.)

Maybe a good idea for next time, I always keep a installation log, in which I specify any fixes I had to apply. I also keep copies of important conf files, like my network configuration and my wpa_supplicant configuration.

---

### Post by BoJon on 2007-10-28
Thanks for the response.  I am wanting to keep my data--Bookmarks, Open Office, and Thunderbird. Just want to confirm that the data is in /Home which I am making into a separate partition.  And that a manual install, not upgrade, will not overwrite /home.  I just installed Feisty a short time ago, so don't have and settings that nee saving.  And how do you make the title bold?

---

### Post by qpieus on 2007-10-28
Bookmarks and thunderbird settings (and the mail) are in hidden folders in your /home. I'm not sure what you mean by openoffice data. If you mean the documents and stuff you've made, then yes, those should be in /home, but you might want to search around your home and make sure your stuff is there. I think the default save location is /home with OO, so unless you intentionally saved items elsewhere, it should all be in your /home.

You might also want to backup your /etc directory. There's configuration stuff in there like fstab, xorg.conf, etc. that it might come in handy to have a copy of. My entire /etc directory is only 10 MB, so you're not going to break the bank backing it up.

As far as the installation goes, make sure you select manual partitioning during the installation so you can select what partitions get mounted where and what gets formatted or not. So once you make your separate /home, the next time you install you can tell the installer which partition has /home on it and NOT to format it. I just did this with my clean install of gutsy, it worked great (I already had a separate /home).

---

### Post by BoJon on 2007-10-28
Thanks for the education.  Really appreciate your response and you all that help.

---

