---
title: "Installing an IRC client,  and gnochm in UBUNUTU 6.10"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by guitarra1809 on 2007-04-08
Hi.
First of all, I would like to state a desclaimer: I am a total newbie to UBUNUTU, and the last Linux I have used was something like RedHat 8 back then...

Anyway, while trying to install the gnochm viewer,  I got the following sequence of messages:
```

$ sudo apt-get install gnochm
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnochm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnochm has no installation candidate

```

What should I do to make apt-get work? I have never used it successfuly (well, I am only using UBUNUTU for a few hours now...)



And now, for a different issue: how can I obtain an IRC client, and what are the UBUNUTU support channels, if any?
I used to use the Xchat client because it was installed by default in my system (back then, in the far past, remember? :) ), but now I'm opento suggestions (and would be thankful for some instructions...)

Thanks!!!

---

### Post by ardchoille42 on 2007-04-08
Xchat is a nice gui irc client and may already be on your system. If not, you can get it with
```

sudo apt-get install xchat

```

I use irssi, it's a text-based irc client and I love it. You can get irssi with
```

sudo apt-get install irssi

```
If you're interested in irssi, you can find the homepage [here]("http://irssi.org/").

The main Ubuntu support channel is #ubuntu on the irc.freenode.net irc network. There are other Ubuntu channels as well, including #ubuntu-offtopic (for social chat), #ubuntu+1 (for the dev ubuntu release), #ubuntu-effects (for beryp/compiz/xgl in ubuntu) and lots of Ubuntu channels for different languages.

---

### Post by guitarra1809 on 2007-04-08
I tried the xchat solution before, but it doesn't work.
I think that there is something wrong with where UBUNUTU searches for packages.
I haven't touched that file, It remains as in default.

The output of the xchat install command was
```

sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xchat

```


The irssi installation succeeded.
I prefer the xchat to it, but I can get used I guess.
Still, I think something is wrong with my package installation mechanism, as I fail to install both gnochm and xchat.

---

### Post by ardchoille42 on 2007-04-08
I forgot to mention that xchat is in the universe repo. If you enable the universe repo, you should be able to install xchat and gnochm - gnochm is also in the universe repository. I don't think anything is wrong with your APT, it's just that some repos (like the universe repo) are not enabled by default.. you have to enable them and then do "sudo apt-get update" to update your sources, and then you can install things from the new repos. [This page]("https://help.ubuntu.com/community/Repositories/Ubuntu") deals with adding and removing repos from your sources.list.
Sorry about that.

---

### Post by guitarra1809 on 2007-04-08
Thanks, I'll try that.
BTW, the #ubunutu channel seems to be quite empty...
Or is it live and kicking, and I somehow joined the wrong one? (I used the  irc.freenode.net  server and  #ubunutu channel you wrote above...)

---

### Post by ardchoille42 on 2007-04-08
> **guitarra1809 said:**
> Thanks, I'll try that.
BTW, the #ubunutu channel seems to be quite empty...
Or is it live and kicking, and I somehow joined the wrong one? (I used the  irc.freenode.net  server and  #ubunutu channel you wrote above...)

It's #ubuntu, I think you may have misspelled it, and it has 987 people in it right now. It's usually quite busy.

---

### Post by guitarra1809 on 2007-04-08
I think you are right...
However, enabling the universe repository, did not help much, and the same error messages returned...

This is my /etc/apt/sources.list file:
 ```

  GNU nano 1.3.12                                    File: /etc/apt/sources.list                                                                    Modified  


deb http://il.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://il.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe





```

---

