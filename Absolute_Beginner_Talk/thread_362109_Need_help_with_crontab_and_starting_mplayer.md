---
title: "Need help with crontab and starting mplayer"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by satrich on 2007-02-15
Hello,

I am a happy Xubuntu-user, using edgy, the 6.10 release.
I am trying to start mplayer with the crontab scheduler. And I am not getting it to do the job.
Basically, I am trying to schedule a recording of an radio-stream from the internet.

The stream is playing fine with mplayer when i start it from the command line. But when I add the command to crontab, mplayer is not starting at all. Nothing is happening. This is what I do in crontab:


# m h  dom mon dow   command
* * * * * mplayer [http://stream.garnierprojects.com/m-fm](http://stream.garnierprojects.com/m-fm)

When I save it is saved to   /tmp/crontab.FB8yOm/crontab. I don't know if that is right but it says:
crontab: installing new crontab, so i thought that would be ok.

For the test I left out any time stamps in the crontab. It doesn 't matter if I set any time in there

And the odd thing is, from the command line the command: mplayer [http://stream.garnierprojects.com/m-fm](http://stream.garnierprojects.com/m-fm) is just working fine.

also when i add:
* * * * * echo "hello" > /home/me/test.log

then crontab makes a file test.log with 'hello' in it. So crontab is working.

The only thing is I can't get any other command through cron. Even other programs will not start when I put them in crontab.

Anyone has an idea?? :confused: :confused:

---

### Post by Rippey on 2007-02-15
try adding the full path to mplayer in the crontab, on my machine it's /usr/bin/mplayer,
I don't think it'll be different on yours, but to be shure you can type "which mplayer" that should output the full path to mplayer.

---

### Post by satrich on 2007-02-15
doesn't help....

in crontab:

* * * * * /usr/local/bin/gmplayer

It doen't start gmplayer at all.

And in terminal:
gmplayer or mplayer [http://.](http://.)... does start up mplayer and play a stream.

Any other suggestions?

---

### Post by Rippey on 2007-02-17
/usr/local/bin/gmplayer url [http://stream.garnierprojects.com/m-fm](http://stream.garnierprojects.com/m-fm)
shoud do it

---

### Post by nbsharma on 2007-02-20
I am seeing a similar problem. The echo command works, but trying to run the following doesn't:

/usr/X11R6/bin/realplay ~/Desktop/some.mp3

I read the man page for crontab and it says that "\n" is _required_ at the end of each crontab entry. I did that, but to no avail.

Any ideas?

cheers.

---

### Post by nbsharma on 2007-02-21
After investigating a bit, I found out that we have to set the X screen variable to let cron know about X server's presence.

Here is a link where I found this solution:

[http://ubuntuforums.org/showthread.php?t=86112&highlight=crontab+X+variable+setting](http://ubuntuforums.org/showthread.php?t=86112&highlight=crontab+X+variable+setting)

cheers.

---

