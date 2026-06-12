---
title: "Reconfigure CUPS everytime I log on ????"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-02-25
I downloaded the hplip self extracting archive from the sourceforge website, and the printer install went off without a hitch. Printer works just fine and everything looking rosy  -- untill I log in the next day and got error message saying "The  CUPS server could not be contacted". I used the script "sudo dpkg-reconfigure cupsys" and "sudo /etc/init.d/supsys restart" to get things started back up again and running fine, once again untill I logged back on. Same problem, over and over again. What am I doing wrong? I did the same install proceedure on my Compaq 5900Z and things still working perfectly. On my Toshiba Satellite Pro (dual boot Dapper and XP) I can't seem to get it to work unless I reconfigure CUPS everytime. Any ideas how to go about fixing this problem?? Or is it maybe due to XP dual boot ?? Not too comp literate so hold my hand and be gentle, shiny newb here!! Thanks for the help ---   again!!

---

### Post by tgalati4 on 2007-02-25
It could be that the CUPS daemon is crashing which requires a restart as you have done.  We need to see the error files (/var/log/cups) to see what is going on.

As I am using Dapper as well, I installed hplip from the repositories.  Is there a reason why you installed it from sourceforge?  Perhaps you have a later version of the driver that is not compatible with the Dapper build?

Search for hplip in synapic shows that 0.9.7-4 is the current driver version for Dapper.  If yours is different then that may be the problem.

Good luck

---

### Post by jerrynewt on 2007-02-25
Thanks for the quick response. I found that I didn't have samba configured properly so gotta get that configd right. I think the version is compatible, it worked great on my Compaq machine with Dapper. The only diff between the two machines (other than specs) is this laptop is dual boot Dapper and XP. I reconfigured the samba file to match the file on the Compaq (with different netbios name) and was wondering if I have to uninstall the cups files that were extracted and installed when I ran the hplip .run file, and reinstall them or not?

---

### Post by jerrynewt on 2007-02-25
By the way how do I get the error logs to come up. I went to the /var/log/cups location and saw some error files but can't get them to open. There were 7 of them.

---

### Post by tgalati4 on 2007-02-26
gedit mycupserrorfile.log

You need to associate *.log with gedit.

more mycupserrorfile.log           (this will page it to the screen, q to quit)

Samba is a file server system and is completely separate from CUPS.  I cannot think of any situation where samba would foul up CUPS.  

In a browser:

localhost:631

Keep your printer page up and it will refresh its status every few minutes.  If your CUPSD crashes, it will show up on the web page.


Search CUPS in the forums for more detailed configuration information.  Master CUPS and you will look at printing differently.

Good luck.

---

