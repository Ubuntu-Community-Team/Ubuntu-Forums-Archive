---
title: "clamav running as a cron"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by hen3rz on 2006-01-16
Hello,

I set clamav to auto scan my computer as I plan on using it as a mail server that will recieve mail being viewd on a windows machine. I set it up using a cron job every 6hrs by doing the following:
```
sudo gedit /etc/crontab
```
Then entering this on the bottom of the file:
```
00 6	 * * * 	sudo clamscan -r /home/
```
Now i think that should make clamscan scan my whole home folder which is what i want it to do right now as I havent set up the mail server yet.

**My actual problem is** that when im on the computer and the scan starts how can i stop it??? when i run "sudo clamscan -r /home/" in the terminal i can simply close the terminal window but how do i do this when its running in the background and i cant see it? Is there a way i can get it to open a terminal window and run that pice of code?

Thank you for any help you can provide.

---

