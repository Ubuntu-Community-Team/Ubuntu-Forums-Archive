---
title: "Firestarter as a startup program?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-13
I tried editing my "sessions" to make the command ```
sudo firestarter
``` start when I logged on (i have to use sudo because it says an administrator can only edit the firewall), but it doesn't do anything when I log in. How do I fix this?

---

### Post by Ziox on 2006-08-13
> **kbsuperstar said:**
> I tried editing my "sessions" to make the command ```
sudo firestarter
``` start when I logged on (i have to use sudo because it says an administrator can only edit the firewall), but it doesn't do anything when I log in. How do I fix this?

use:

gksu firestarter

sudo is for the terminal only, while gksu (gui) displays a dialog box prompting for your password...

---

### Post by msak007 on 2006-08-13
[FireStarter FAQ]("http://www.fs-security.com/docs/faq.php")[URL="http://www.fs-security.com/docs/faq.php"]
[/URL]

---

### Post by bhoughton on 2006-08-13
Instead of "gksu", I used "gksudo".  Any harm in that?

---

### Post by foolsh on 2006-08-13
firestarter runs automaticlly on boot but the GUI does not unless you 
#sudo firestarter 
and leave it running when you shutdown your computer it will run automaticlly the next time you boot but will ask for your password

---

### Post by Ziox on 2006-08-13
> **bhoughton said:**
> Instead of "gksu", I used "gksudo".  Any harm in that?

I doubt there's any harm, gksu is just "su" with GUI, and gksudo is just "sudo" with GUI. But I find it funny that you can't accesss su within the terminal, yet you can use gksu...can some one explain?

---

