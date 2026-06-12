---
title: "Another messing up of the permissions"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Epperly on 2006-11-09
I was installed Bitpim and I ran "sudo usermod -G bitpim -a your_user_name" without the -a and now when I go to users and groups I get an error:
Failed to run users-admin.
Automatix doesn't work, I can't sudo and edit things... this sucks.

[desperation]Please help me!![/desperation]

---

### Post by jpkotta on 2006-11-09
Reboot in recovery mode.  It should automatically login as root.  Then you can run any command you need to fix it.  You may want to give root a password so you don't have to reboot in the future, but that may not be a good idea.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

BTW, to use sudo, you have to be in the admin group:

```
gpasswd -a jpkotta admin
```

---

### Post by Epperly on 2006-11-09
eh thanks for the help but my internet turned off and since I couldn't sudo I couldn't fix it... had to reformat(like 5th time this month :()
Thanks anyway, though

---

### Post by CatKiller on 2006-11-09
For the future, you can do as jpkotta says and reboot in recovery mode if you can't use sudo in your normal environment. This will make you root automatically, without having to use sudo.

---

### Post by Epperly on 2006-11-09
If I did that, and was always in root, would I be able to edit my user groups to fix the error I made?

---

### Post by dannyboy79 on 2006-11-09
yes of course, there is almost never any reason to reformat, that's the easy way out and you'll never learn anything. when you boot into recovery mode, you are logged in as root, which allows you do ANYTHING, which is a good thing when you need to fix stuff but a bad thing if you aren't careful cause you could royally screw up linux. next time, just do what the guy above stated.

oh yeah, also, if you don't have a another computer and you're inet access is out, you could always boot to a live cd and go online and print out instructions to fix your box, you can even do that from the live cd, but sometimes it's easier just running from recovery mode, i think you get into that by when your computer is booting, you hit f1 or something like that (i am sorry I forgot exactly but I am sure some1 will correct me in a second or 2) then there will be a list of stuff you can boot to (this is basically grub if I am correct) there should be like, recovery mode, a couple of different kernels, and maybe even check memory unless that's only on the livecd. so next time instead of reformating and giving up, dig your heels in and plow forward the best you can, then if all else fails and you really messed up your box, you'll get satisfaction knowing you did try to fix it and then you can simply reformat at that point. good luck for the future. also, anything you ever want to know if you don't have inet, you can try to check the linux manual, so if you wanted to learn about fstab, then within a terminal, type man fstab, and you'll get a wealth of info. I just started doing that myself and I love it cause instead of getting biased help online that may or may not be correct, man fstab is gonna give me the CORRECT answer.

---

### Post by Epperly on 2006-11-09
aw man, that really sucks because I've already formatted 5 times between oct and this month, 3 being my fault 1 being getting rid of windows and 1 for HD failure.

and damn I didn't think of going online with live CD, duh me.. thats a good idea haha.
I'm an idiot.

The reason I format though is because I don't know like advanced code by heart to get me out of trouble, I have to post up and ask, wait for a response and all and sometimes I just wanna get it over with.
Thanks for the help!

---

### Post by CatKiller on 2006-11-09
It's ESC to enter the GRUB menu that has the recovery console option, I believe.

Actually, for a fixing a lot of the ways you can break your computer, booting the Live cd and mounting the hard drive is sufficient to enable you to fix it - broken config files are a prime example - and then you can look at the Internet at the same time that you're fixing it.

---

