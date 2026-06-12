---
title: "Downloads scheduler for Ubuntu: any recommendations?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by andriyr on 2008-01-16
Hi all!

What I need is application to do the following:
- add a download and scheduler it to start at, say, 23:00

I've tryed d4x but it seems to have bug with adding extra "/" to URL, so i'm looking for another application to use under my Ubuntu 7.10.

Any recommendations, please?

---

### Post by scizzo on 2008-01-16
This depends a bit on the actual things you want to download on schedule. One way is to use a script that does it for you if you are using a special protocol like SCP, FTP or the like.

Then set it up using crontab.

However it all depends on what the actual thing you want to download is and what protocol.

I suggest always to use scripts for things like this and then set it in the crontab to run.

---

### Post by andriyr on 2008-01-16
Well, most of downloads are multimedia files (like .mpg, .avi, .mp3 ets) mostly through http.

Can you describe how to create a script and then schedule it using crontab?

Thanks in advance :)

---

### Post by hyper_ch on 2008-01-16
> **andriyr said:**
> Well, most of downloads are multimedia files (like .mpg, .avi, .mp3 ets) mostly through http.

Can you describe how to create a script and then schedule it using crontab?

Thanks in advance :)

just write a bash script that will "wget" all the files you want and then set it up on cron to run at specific times.

---

### Post by kpkeerthi on 2008-01-16
Why do you want to add / at the end of an URL? Are you trying to download recursively from the remote folder or something?

---

### Post by scizzo on 2008-01-16
> **andriyr said:**
> Well, most of downloads are multimedia files (like .mpg, .avi, .mp3 ets) mostly through http.

Can you describe how to create a script and then schedule it using crontab?

Thanks in advance :)

For example you can do:

The best is to follow a guide to how you write the bash scripts. Like hyper_ch said before. You can look at the guide below:

[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

This will help you to understand the bash scripts.

For the Crontab inforation you can always check:

[http://www.crontabrocks.org/]("http://www.crontabrocks.org/")

Both the links will explain a lot to you. One thing to know is that you can actually just use the bash script to tell it what command to run.

---

### Post by andriyr on 2008-01-16
> just write a bash script 
ummm, show me how please, i've newer tryed to :(

---

### Post by andriyr on 2008-01-16
**scizzo**, thanks a lot! I'll try that guide :)

---

### Post by kpkeerthi on 2008-01-16
Remember that crons are "repetitive". If you want to schedule a download once only I suggest you use **at** command.

```

wget -r -N http://someserver/somefolder

```
The above command downloads all files and subfolders from the URL recursively (-r) with timestamps(-N) to your home folder.  

If you want to schedule that script at 23:00 hours, then open a terminal and type
```

at 11pm today <press enter>

``` and enter the wget command above and press <ctrl>+D

Use **atq** to query your scheduled jobs and **atrm** to remove the jobs.

The command
```

wget -i <input-file>

``` will download the files from the URLs listed in <input-file>

---

