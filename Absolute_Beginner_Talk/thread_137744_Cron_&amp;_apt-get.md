---
title: "Cron &amp; apt-get"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-02-28
OS: Ubuntu 5.10 in terminal mode.

How can I set Ubuntu to run apt-get update every week?

Is it cron or crontab?

---

### Post by pbaehr on 2006-02-28
Use
```
crontab -e
```

That opens the cron schedule for editing in your default text editor.

Next add the line:
```
m h * * d apt-get update
```

Replace the 'm' with the minute of the hour you want it to run on (0-59)
Replace the 'h' with the hour of the day you want it to run on (0-23)
Replace the d' with the day of the week you want it to run on (0-6) (0 = Sunday)
The two asterisks will make it run on any day of any month.

Exit the text editor, saving.

That's it!

---

