---
title: "Anti Virus"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-10-10
What is the recommended anti-virus for Ubuntu?

---

### Post by whizbaby on 2006-10-10
What for? Do you run a mail-server? Otherwise you don't need.

---

### Post by mumebuhi on 2006-10-10
My organization requires me to run an anti-virus application if I want to have my Linux box in its network. :(

---

### Post by Andrew1234 on 2006-10-10
Clamav Anti-Virus -- load via Synaptic Package manager and scan with Clamtk.

---

### Post by rfruth on 2006-10-10
If you use the internet ya need a virus tool, clamAV works well and the price is right :) [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by whizbaby on 2006-10-10
O.K., you're in corporate network. Clamav is the way to go.

---

### Post by equal on 2006-10-10
To install the antivirus, type this in the Terminal:

```
sudo apt-get install clamav
```

Then to set up the anti-virus to scan each night at midnight:

```
export EDITOR=gedit &&  sudo crontab -e
```

and in the window that pops up, add this to the end and save the file.
```
00 00 * * *  sudo clamscan -r /
```

If you want to set it to a different time, change the numbers at the beginning (minute, then hour, not the expected inverse). The stars represent Date, Month, and Year. It would be best for it to scan each night though.

---

### Post by whizbaby on 2006-10-10
Sylpheed-claws-gtk2 (mailing program) has a clamav plugin maybe others like thunderbird and evolution have one,too?

---

