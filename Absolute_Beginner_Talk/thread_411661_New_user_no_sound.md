---
title: "New user no sound?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ghostie on 2007-04-17
hi all,

I'm a total newbie in linux with some question and probably sound most stupid.

I'm currently using Ubuntu LTS 6.06. I find it serves better for me then compare with other linux distributions.

But, I just had a problem which I have not a single clue about.

I was practicing, creating a new user
> useradd newUser

then, password
> passwd mysecretkey

I logged off root and restarted this machine.

I already had another user account working previously and it is still working.

Now, the problem is, the new user account doesn't allows me to control the volume with error message as "No volume control GStreamer plugins and/or devices found." after I'm seeing the default gnome desktop wallpaper.

I have read this link [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but I got totally lost. I also read that there are fellow forumate chmod 777 on /dev and /lib and sound works after that magic spells... I have yet taken any steps. I wish to hear from experienced and pros before I proceed with rumors... thanx in advance!

---

### Post by JockeTF on 2007-04-17
You should try adding the new user to the audio group.
Just type:

sudo addgroup <username> audio

After that you should try to login (logout if the user is logged in) with the new user and try changing the volume.

Also, if you go to System --> administration --> Users and groups (or something similar) you should be able to give the new user other rights as well.

// JockeTF :D

---

### Post by ghostie on 2007-04-17
JockeTF, thanx dude, it works!

BTW, how do you know this? I mean, is this documented anywhere?

Is there an autoscript to do all this instead of me doing line by line (which is good for practise but slow in production environment). I believe there is, because my other account was created during the post-installation which didn't happen to have such issue.

Again, Thank you very much!!! :)

---

### Post by JockeTF on 2007-04-19
You're welcome. :)

I know all this because of that I run a server and work a lot with the terminal.

You got most of the things documented in your system already.
Try "man addgroup" for example and you'll see everything that the addgroup command can do.

When you add a new user you could use the parameter --add_extra_groups to the adduser command
```
sudo adduser --add_extra_groups <username>
```
That will add the user so all of the specified groups in /etc/adduser.conf .

If you want to learn about writing simple scipts which automates tasks you should have a look at this guide:
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")

Oh and don't forget that you can add users with Gnome and KDE too.

//JockeTF :mrgreen:

---

### Post by nekator on 2007-04-28
Check this out...I had the same problem today (6.06) opened my wife a new account on the comupter and I (administrator) lost all my rights in the user privliges...it had nothing to do with the sound card, or anyother piece of hardware...Cool...especially interesting as I unconfigured the printer driver, unistalled gnome-desktop and gdm in the process of troubleshooting this one out....perhaps the ubuntu troubleshooting guide for sound problems should include as a very first step "Have you checked if your sound use priviliges have changed"...Anyways...of to sleep. Best to you all.

---

