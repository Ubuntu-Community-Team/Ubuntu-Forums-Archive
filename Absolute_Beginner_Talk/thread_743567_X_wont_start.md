---
title: "X wont start"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-04-02
For some reason when I sat down at my computer today, I had a message from my email client saying it couldn't write to my inbox because the filesystem was readonly.  It seems like this readonlyness just "happened" at some random time after booting because after that, the programs running ceased to work, and new programs refused to open.  When I rebooted, X wouldnt start.  I thought maybe Unison messed up the permissions on my home folder and somehow that was causing it, but I've done "sudo chmod -R 700 /home/barrett/"  and the problem is still going on.

Right now when I boot, it boots into the blue screen like I was configuring X, and it asks me if I want to see the output to troubleshoot.  When I click yes, the errors are 
> 
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


Can anyone help me figure out whats wrong and how to fix it?
id be mucho greatful!

---

### Post by Iowan on 2008-04-02
A read-only filesystem *may* indicate a hard drive problem - but the reboot should have triggered a filesystem check.

---

### Post by tiga2001 on 2008-04-02
I don't know if chmodding your home directory to 700 is such a good idea. Doesn't the X server need to access some files in the home directory? I'm not familiar with how X works, so correct me if I'm wrong.

---

### Post by ghost_ryder35 on 2008-04-02
post the log files from the time this happens.
```
/var/logs/
```
give us
```
messages.log
```
```
faillog
```
```
xorg.0.log
```

these will help is figure out why X is not starting.
in the meantime of waiting for us to figure this out you could try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by apokkalyps on 2008-04-03
I'm not sure how I should post these, the're really huge.  I tried to attatch them but the filetypes were wrong so I saved them as .txt files but the limit for that is 19k so I can't do that.
it would be really nice if you could upload .log files or .txt files of a reasonable size.

  and when I try to dump it all in the post I get this error from Ubuntu forums >  The following errors occurred when this message was submitted:

   1. You have included 44 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
Even though obviously theres no images in there I dont know what tags they are talking about because theres WAAY more than 44 things in [brackets]

I think I'll save the raw text as .doc becuase of the higher file limit, if this is against forum rules or there is a better way, let me know and I'll fix them in an edit.





again i hope its ok to post like this
I'm pretty sure the problems started in the afternoon to evening on the 1st.
sorry for the length (mainly in "messages") I wish I could trim it down for you but I have no idea what I'd be looking for so I'd better just leave it


Also I did the "sudo dpkg-reconfigure xserver-xorg" and I ran through it all and it was fine but then I get the same error when I try to "startx".

---

