---
title: "removing pidgin"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by xdarkgokux on 2007-08-14
K  guys, i am telling u rite now.. i am really new to ubuntu... and i am using kopete and want to uninstall pidgin but when i ran apt-get remove pidgin it said it could not find the package..

---

### Post by Kingsley on 2007-08-14
Try sudo apt-get remove pidgin-data.

---

### Post by kelly.seay on 2007-08-14
Did you install with a .deb or did you install it from source?  If you did it with a .deb, you might want to try going to adept and doing a search for pidgin to see if anything comes up that you can remove, but since the apt-get didn't see it, i doubt it.  If you did it from source, i think you can go back to the source directory you installed it from and do a make uninstall or a make remove, something like that i think.  I hope someone with more experience can help you better than me.

---

### Post by xdarkgokux on 2007-08-14
same thing cannot find the package for pidgin-data

---

### Post by xdarkgokux on 2007-08-14
i did it from source WITH A DETAILED GUIDE..lol, i have no clue how to do that

---

### Post by amazingtaters on 2007-08-14
try
```
sudo apt-get remove pidgin*
```

---

### Post by xdarkgokux on 2007-08-14
Wow, i did the make uninstall thign and i think it is working.. THX A LOT.. i will post the results..linux is awesome.. never going back to xp xD

---

### Post by xdarkgokux on 2007-08-14
Yup it worked.. the make unsintall.. so one more question, if it is not a deb package.. i have to go to the folder in the terminal and say make instlal ot install and make uninstall to uninstall>??

---

### Post by amazingtaters on 2007-08-14
I guess it would have helped if I had read that you installed it via the source code and not via apt-get. Anyway, glad you (apparently) got things going.

---

### Post by R0B071CxN1NJ4 on 2007-08-14
why would you want to remove pidgin? in my expirience kopete on gnome is extremely buggy

---

### Post by xdarkgokux on 2007-08-14
ohh i thought pidgin was good, but i could not do voice.. i mean if u can hook me up with some way to do voice and webcam for yahoo and aim.. i would keep it

---

### Post by kelly.seay on 2007-08-15
> **xdarkgokux said:**
> Yup it worked.. the make unsintall.. so one more question, if it is not a deb package.. i have to go to the folder in the terminal and say make instlal ot install and make uninstall to uninstall>??

I am glad that it worked for you.  

To answer your next question, I hope this helps.  Yes.  .deb's are software packages that your package manager can handle, makes it easy to handle dependencies and stuff like that.  Most people say it is best to install software only from official repositories, but not all the good stuff is in the official repositories.  So, sometimes you have to find unofficial repositories or .debs for the software you want.  So, when choosing between source (tar.gz) and a package (.deb), choose the .deb so it is easier to install and uninstall.  And when installing from CLI, use aptitude instead of apt-get, it handles tracking dependencies better.

I hope i answered your question.

---

### Post by Maverickprowls on 2007-11-23
First, I used the synaptic package manager to completely remove pidgin, an libpurple.  Then, in order to remove all trace from my system, I use the following commands. 

```
locate *pidgin* > pidginfiles.txt

``` and
```
locate *purple* > purplefiles.txt
```

to create a text file of all the locations on my machine which contained pidgin program files and the associated libpurple linked files (some people have reported that leaving libpurple as it is causes problems with the install from the deb package), and then removed all the ones which weren't from my /home directory.

It may not may not be good practice, infact I 'm almost certain it isn't, but it does prove very effective in purging pidgin from my system.

To make it easier, I then opened a sudo-ed nautilus to let me delete at will using

```
gksu nautilus
```

[COLOR="Red"]WARNING:  If you're not careful you can damage your system.  Only delete the pidgin files and nothing else.[/COLOR]

I'm not saying it's the best way to do it, but it worked for me.

---

### Post by pgb on 2008-03-11
Why not just search for pigdin and the pidgin-data file in Synaptic? It's what I did and is very simple for someone who has trouble with CLI.

---

