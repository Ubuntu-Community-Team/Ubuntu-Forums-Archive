---
title: "run script.pl every 30mins.."
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by hen3rz on 2006-01-14
Hello,

How would i go about running a perl script on startup then every 30mins from then on..???

I read some where you could do this with a cron job? I've looked into them but im still a little confused.

---

### Post by adwait on 2006-01-14
Yup.....use
```
sudo gedit /etc/crontab
```

At the end of the file (before the # though) enter the name of the script you want to run. If you need to run it as root user it, the lines you add will be something like this:
> 00 * <TAB> * * * <TAB> root <TAB> <perl script>
30 * <TAB> * * * <TAB> root <TAB> <perl script>

You'll have to reply <perl script> with the command with which you run script so it will probably be something like /home/xyz/./script.pl

Please note that the first coloumn is the MINUTES and the second is the HOURS. The three * after that are to tell the computer that the command should be run on any day month and year. you can replace the word "root" with any other user so that the script is run as that user.

---

### Post by hen3rz on 2006-01-15
Thanks heaps. Ive done all the steps and It went smoothley. I gues time will tell if it all works.

Thank you again.

---

