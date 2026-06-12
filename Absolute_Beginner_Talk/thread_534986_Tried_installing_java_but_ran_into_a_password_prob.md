---
title: "Tried installing java but ran into a password problem"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by MS-DOS4 on 2007-08-25
Well I've been having trouble installing Java on my Xubuntu computer. 

I need java to run online programs that I want and I was wondering if somebody could debug this problem for me. 

I tried following phossal's guide on installing it but 

A) The .bin file I downloaded is a new version so I don't know if his commands will work
B) The damn password won't work.

Alright so I download the latest linux java .bin file and place it on my desktop (BTW I'm logged in as my "charles" account. It won't let me log into root if that's even possible. I have no idea what I'm doing here)

Anyway I open up a terminal, follow the steps to install (i.e. type in cd ~/Desktop)
then I type in sudo chmod +x *.bin and click enter. It asks me for my password so i hit enter and as fast as I can (because of the stupid 2 second time limit) and I click enter but it says "Bad password" or something along the lines of that. So I try setting my root password to something else and try it all again but once again bad password. So this time I try with my "charles" account password. STILL nothing.

Help!

EDIT: Wow there's another thread JUST like this only a few minutes apart. Lemme see if that thread helps.
2nd EDIT: Nope. I get an error message.

---

### Post by sumguy231 on 2007-08-25
Might I ask why you need to install it from Sun's installer? It's in the repositories, you can either install sun-java5-jre or sun-java6-jre from Synaptic. (You will need to enable the multiverse repository from Settings -> Repositories)

P.S. Or sun-java5-plugin if you want the Java browser plugin.

---

### Post by MS-DOS4 on 2007-08-25
> **sumguy231 said:**
> Might I ask why you need to install it from Sun's installer? It's in the repositories, you can either install sun-java5-jre or sun-java6-jre from Synaptic. (You will need to enable the multiverse repository from Settings -> Repositories)

P.S. Or sun-java5-plugin if you want the Java browser plugin.

I don't have a Settings > Repositories.

Also I just want to install the browser plugin.

---

### Post by RomeReactor on 2007-08-25
Try this from a terminal:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```
Then:
```
sudo update-alternatives --config java
```
and select **/usr/lib/jvm/java-6-sun/jre/bin/java**. Or to install just the plugin:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by MS-DOS4 on 2007-08-25
Nope. I got this error:

```
charles@charles-desktop:~/Desktop$ sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
Password:
fishss
charles@charles-desktop:~/Desktop$ fishss
bash: fishss: command not found
charles@charles-desktop:~/Desktop$ 

```

I give up. I don't think linux is right for me. Thanks for your help though.

---

### Post by sumguy231 on 2007-08-26
> I don't have a Settings > Repositories.
Really? It's there in Synaptic 0.57.11 for me.

> I give up. I don't think linux is right for me. Thanks for your help though.
Sorry to hear that. If you reconsider then I can still help.

---

### Post by st33med on 2007-08-26
> **MS-DOS4 said:**
> Nope. I got this error:

```
charles@charles-desktop:~/Desktop$ sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
Password:
fishss
charles@charles-desktop:~/Desktop$ fishss
bash: fishss: command not found
charles@charles-desktop:~/Desktop$ 

```

I give up. I don't think linux is right for me. Thanks for your help though.

Actually, you don't see the password, but it is being put in. Just, put in your password, and it will go.

Next, the root account is locked. You can access it, however, it's a good idea not to because you could screw up files. To get limited access, use 'sudo' before your command, but only use it on programs that need it, NOT on GUIs. Example: Never do this:
```
sudo firefox
```

It won't really do anything, however, use sudo only when necessary, like copying root files.

---

### Post by MS-DOS4 on 2007-08-26
Thanks.

But oooh man I got soo close. I finally got past the password part and did the guideline for it but I guess it didn't work because that tutorial was created for a older version of java.

---

### Post by some_random_noob on 2007-08-26
> **MS-DOS4 said:**
> Thanks.

But oooh man I got soo close. I finally got past the password part and did the guideline for it but I guess it didn't work because that tutorial was created for a older version of java.
Keep at it - it may be annoying, but it's definitely worth trying. Installing Java is a fairly easy task in comparison to other things. Do what other people here have said: Try installing it from the Multiverse repositories so that you have less problems, that way, you shouldn't need to use the command line or tutorials - it's more automated if you install it via a package managing tool (such as synaptic or apt-get). 

Installing Java can be done, it's a pretty common task. Just try to keep your installation clean and don't mess around - otherwise you'll create even more problems (I learnt this the hard way!)

---

