---
title: "Beryl and conky"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-02-22
Hi guys, I recently changed my conkyrc file and now when I load up my computer, Conky displays for a brief second but when Beryl loads and Conky disappears. It is still running as a task, but it's not visible on the desktop. Any ideas on what I need to add or change to make it permanently there?

Thanks. :guitar:

---

### Post by ScottFW on 2007-02-22
Try this...

Create a script that delays the startup of conky.

$ gedit ~/.conky_start.sh

Then paste the following two lines:

#!/bin/bash
sleep 15 && conky;

Save the file. Then add the script (in my case it's /home/scott/.conky_start.sh) to your startup programs in session options.

The number 15 is the delay time in seconds. You can experiment with shortening it as much as possible without conky disappearing on you.

I've also found that regardless of the delay script, conky will disappear if my computer can't connect to the wireless router. I have my conky configured to display network info like IP, router name, link quality, up & down rates, etc., and I think conky gets upset it when this info is unavailable.

---

### Post by erkki70 on 2007-02-22
> **ScottFW said:**
> Try this...

Create a script that delays the startup of conky.

$ gedit ~/.conky_start.sh

Then paste the following two lines:

#!/bin/bash
sleep 15 && conky;

Save the file. Then add the script (in my case it's /home/scott/.conky_start.sh) to your startup programs in session options.

The number 15 is the delay time in seconds. You can experiment with shortening it as much as possible without conky disappearing on you.

I've also found that regardless of the delay script, conky will disappear if my computer can't connect to the wireless router. I have my conky configured to display network info like IP, router name, link quality, up & down rates, etc., and I think conky gets upset it when this info is unavailable.

Hi and thanks for this useful info :-)
I've a similar problem. I think it's happening when I receive DHCP lease renewal but not sure though... I usually restart conky until the next time...

---

### Post by orb9220 on 2007-02-22
Another conky Beryl bug is if conky starts up before my wallpaper is applied then it is invisible unless I log out then back in.

If my screens are all orange when conky shows then I know it will be invisible when the  wallpaper is applied. I think it is a transparency issue. 

Thanks ScottFW Will try the script thing and see if that solves my problem.

---

### Post by Bagboy23 on 2007-02-22
Perfect. It worked like a charm. Thanks Scott. I also learn't that I could add scripts to session startup.

Thanks ;)

---

### Post by Bagboy23 on 2007-02-23
Actually guys it didn't work. I rebooted and waited,conky is running but just not visible on Desktop. Also I have no desktop icons.

---

