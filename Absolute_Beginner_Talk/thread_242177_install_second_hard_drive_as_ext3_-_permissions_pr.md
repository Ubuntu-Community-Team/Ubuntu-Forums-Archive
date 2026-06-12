---
title: "install second hard drive as ext3 - permissions problem"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by cgreulich on 2006-08-23
I just installed a second hard drive in my system.  I was successful in partitioning it and mounting it, but I couldn't write any files to the drive.

Based on some other posts, I thought it was a permissions problem, so I did this command:

sudo chmod 777 -r /home/amy (my wifes computer:) )

When I reboot the computer, I can now write to the new drive, but I'm getting error that says something like this upon log in:
'users $home /.dmrc file is being ignored.....file should be owned by user and have 644 permission"

I then set the /home/amy directory to 644 and I wasn't able to log into the system.  I went into the terminal mode to reset it to 777, but I'd like to get rid of the error.

ANyone know how to fix this?  Thanks for your help!

---

### Post by treborblack on 2006-08-23
i've got the same problem it seems. not tried your fix as i'm still new to linux. but my running kdesu konqueror. i can then drag and drop files. at least that shows i've mounted it right which is reason to smile a little.:confused:

---

### Post by bodhi.zazen on 2006-08-23
I am not sure, but try:

```
sudo chmod 777 -r /home/amy
```
to set the permissions you would like on this folder.

Then
```
sudo chmod 644 /home/amy/.dmrc
```
The second comand may not need sudo if you are amy.

If that does not work check (and fix if needed) ownership/permission of /home/amy/.dmrc
```
ls -l /home/amy | grep .dmrc
```

---

### Post by cgreulich on 2006-08-31
Thanks for the response.

I tried your sugestion, and when I rebooted I still recieved the same error.

When I tried ls -l /home/amy | grep .dmrc, it said I didn't have permission.

I checked the owner of the file by launching 'gksudo nautilus', and it said it was owned by "amy".

Is there anything else I can do to troubleshoot this?

---

### Post by bodhi.zazen on 2006-09-01
Try this thread:
[http://www.ubuntuforums.org/showthread.php?t=91455](http://www.ubuntuforums.org/showthread.php?t=91455)

---

