---
title: "Serious startup error"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by KevNice on 2007-11-10
I was at a cafe using the wireless and installing an Ubuntu package, but the cafe closed for the night so I had to terminate the install mid session. I didnt know how to do this correctly so I just closed Terminal and shut off the computer.

When I went to log on again, I got the following message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

And it wouldn't let me log in.

So next, I went into restore mode session and logged in, and typed:

```
sudo chmod 644 home
```

Then restarted and tried to log back in. This time it said that the home directory didn't appear to exist, and suggested I log in as root user. I hit yes, but then I got the same message as above, and it wouldn't let me log in again.

So I went back to restore mode, and typed:

```
sudo chmod 777 home
```

Now when I went to log in, I still got the same message, but then Ubuntu started up. I restarted it to test and see, and again I get the error message, but it allows me to fire up Ubuntu.

But obviously something is still wrong, so how do I fix this?

Cheers,
Kev

---

### Post by steve.horsley on 2007-11-10
First put the home directory bach how it should be with
**sudo chmod 755 /home**
Then remove the offending dmrc file with:
sudo rm /home/your-user-name/.dmrc

That should do the trick.

---

### Post by KevNice on 2007-11-11
> **steve.horsley said:**
> First put the home directory bach how it should be with
**sudo chmod 755 /home**
Then remove the offending dmrc file with:
sudo rm /home/your-user-name/.dmrc

That should do the trick.

I did what you said, but I still get the same error message (although Ubuntu does load).

---

### Post by matthewcraig on 2007-11-11
I thought I would help out here today, because I was a new user once, too.  But it seems like most people asking questions in this forum are like you -- having used Ubuntu longer than I have!

---

### Post by steve.horsley on 2007-11-11
Try also 
**sudo chmod 700 /home/your-user-name **
in case its the permissions on your home folder that's the issue.

---

### Post by KevNice on 2007-11-16
> **steve.horsley said:**
> Try also 
**sudo chmod 700 /home/your-user-name **
in case its the permissions on your home folder that's the issue.


yep that did the trick, thanks man!

kev

---

