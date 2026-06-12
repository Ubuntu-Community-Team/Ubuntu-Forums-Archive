---
title: "Migrate RH system to Ubuntu"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by buntu_hugenewbie11 on 2008-04-18
I need to install Ubuntu on a multiproc Quadcore.
The system currently runs Red Hat but I am more familiar with Ubuntu and want to change it over.
How can I keep all the programs the user has while still making a complete switch?

Is there any hardware compatibility issues with 4 processors?

---

### Post by unutbu on 2008-04-18
I recently migrated from RH to Ubuntu and only had one problem:
my .bashrc did not contain the line
```

[ -z "$PS1" ] && return

```

because that's the way I rolled on RH :). Not knowing any better, I just copied my .bashrc into my home account under Ubuntu and expected it to work. Mainly it did work, but bash completition did not work until I added the line above.

In general I would suggest letting Ubuntu install its default .bashrc and other little config files and then letting users add back what they want from their RH config files. I don't know if that's reasonable, depending on your user base, but hope this helps.

If you have a concern about a particular app I'd be glad to try to recall if there was any issue, but at the moment I can't recall any other problem at all.

---

### Post by buntu_hugenewbie11 on 2008-04-18
So do you just have to copy the home folder?

---

### Post by unutbu on 2008-04-18
In general, yes, that should work. I would be a little concerned about config file issues that might arise however. For example, maybe your RH users use a program XYZ. So they may have a .XYZ config file in their home accounts. 
Now when you install Ubuntu, suppose you also install a newer version of XYZ. Sometimes an old config file with a newer software will cause strange errors. Usually the problem is minor, often the software will make you aware of the problem (either gracefully or rudely). Occassionally it causes people to pull their hair out.

Data is what most people store in their home accounts, and that stuff should all be fine.

Sometimes people create symlinks to applications or other stuff outside their home account. The RH file structure is very similar to Ubuntu's file structure, so in general there should be no problem, but there might be minor snafus cause by files being located in slightly different places. 

Some apps that come standard on RH may not come standard on Ubuntu and vice versa. 

In general, any program that runs under RH can be made to run under Ubuntu.
However, sometimes people post that XYZ (such as video, sound or networking) worked under one distro, but they could not get it to work under another distro, but this could have to do with different versions being installed with different distros, so in theory, anything you can get working under one distro should be possible under any other distro. But it's hard to predict what problems, if any, you will run into before you install, especially without knowing your hardware. 

If you post your hardware, maybe some reader will have experience and comment, but I would suggest you google "hardward XYZ Ubuntu" first. If you have a hardware question I suggest you make another thread so the subject line will attract the right type of reader. (Sorry, I have no experience with quad processor machines.)

---

### Post by buntu_hugenewbie11 on 2008-04-30
How can I test for symlinks?
I will post the hardware shortly.
Thanks for the insight.
Are there others out there that have switched over?
Benefits?

---

