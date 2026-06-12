---
title: "Uninstall apache2?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-12
I cant get apache2 to work out, so is it possible to cleanly uninstall it so that I can re-install with a clean install to work on?

---

### Post by spizkapa on 2005-11-12
Use Synaptic and the option to completely uninstall a program, including config files. You can then reinstall it as if it was never on your system.

---

### Post by Todd_Z on 2005-11-12
Tried that, not workin out so well for me.  I think that everything is uninstalled.... but then apache2ctl is still a valid command....

---

### Post by kelsey23 on 2005-11-12
[QUOTE=spizkapa]Use Synaptic and the option to completely uninstall a program, including config files. You can then reinstall it as if it was never on your system.[/QUOTE]
**No.** Synaptic is one of the worst package managers out there. Use the command line.

try:

sudo apt-get install apache2

However, you could always try Apache 1. In fact, if you are going to be serving PHP pages, there won't be too muhc of a difference between Apache 1 and Apache2. To install Apache 1, type:

sudo apt-get install apache

Also it's been a while since I installed Apache, so I forgot, but you may have to install Apache2ctl seperatly.

---

### Post by spizkapa on 2005-11-12
[QUOTE=kelsey23]**No.** Synaptic is one of the worst package managers out there. Use the command line.

try:

sudo apt-get install apache2[/QUOTE]

I hate to burst your bubble here but I'm afraid that, in the background, synaptic is doing just a dpkg with the purge flag when you ask it to remove a package. So, doing it from the command-line, while more l33t, makes no difference in this case.

---

### Post by spizkapa on 2005-11-12
[QUOTE=Todd_Z]Tried that, not workin out so well for me.  I think that everything is uninstalled.... but then apache2ctl is still a valid command....[/QUOTE]

That's because apache2ctl is a command that comes with the apache-common package. You have to completely remove that one before you no longer have it.

In practice, often, a package is removed and some config files remain behind. This is particularly the case for user-edited files. So, if you've fiddled with apache's files, you may have to remove those separately after doing a purge from the command-line or from synaptic.

---

### Post by kelsey23 on 2005-11-12
[QUOTE=spizkapa]I hate to burst your bubble here but I'm afraid that, in the background, synaptic is doing just a dpkg with the purge flag when you ask it to remove a package. So, doing it from the command-line, while more l33t, makes no difference in this case.[/QUOTE]
No, duh. Synaptic is very bloated way of installing applications. It is also slower, and in my experiance has a *very* hard time when just one other user-invoed application is running. Out of both apt-get and Synaptic, I personally prefer to downlaod the deb and install it via dpkg, but that's just me. And, no, I am not a "zomg I'm 1337" script kidde. Those are the people who use Synaptic :-)

---

### Post by spizkapa on 2005-11-12
[QUOTE=kelsey23]Out of both apt-get and Synaptic, I personally prefer to downlaod the deb and install it via dpkg, but that's just me.[/QUOTE]

Valid choice, I'm not criticising you on this.

You're clearly an experienced user. For the new user, the same strategy is complete nonsense though because he/she wants to just click on a new app and have it running. That's why synaptic is nice and so is the new "Add Applications" command.

---

### Post by spizkapa on 2005-11-12
[QUOTE=Todd_Z]Tried that, not workin out so well for me.  I think that everything is uninstalled.... but then apache2ctl is still a valid command....[/QUOTE]

Here is what I would do in this case, you may or may not want to follow my advice:

1. open synaptic

2. do a find (Ctrl-F) for apache. You will see a list of packages.

3. right-mouse click and completely remove those that you want.

4. click apply

5. wait, shortly you will have a clean system

6. now install what you need and configure

I haven't installed apache recently so I don't know what files you've been editing to get it to work like you say. I'd be tempted to avoid the uninstall-reinstall cycle if I were you though, it's too reminiscent of windows.

One thing that you can do to really help yourself with this is to get apt-file installed (again, use synaptic). Once configured, you can do:

apt-file search apache2ctl

and it will return which package contains that file so you know which package to install, uninstall or reinstall.

HTH.

---

### Post by Todd_Z on 2005-11-12
Not that I'm amused at that conversion and hurt that n00blets like me aren't interested in learning the commands for installing/removing, etc, but my problem is still here:

```

E: phpmyadmin: subprocess pre-removal script returned error exit status 127

```

I feel like that may be an issue becuase when i try to completely uninstall apache2-common i get that error.  Thanks for the help and stimulating debate

---

### Post by kelsey23 on 2005-11-12
[QUOTE=Todd_Z]Not that I'm amused at that conversion and hurt that n00blets like me aren't interested in learning the commands for installing/removing, etc, but my problem is still here:

```

E: phpmyadmin: subprocess pre-removal script returned error exit status 127

```

I feel like that may be an issue becuase when i try to completely uninstall apache2-common i get that error.  Thanks for the help and stimulating debate[/QUOTE]
I hate n00bs. I don't mind newbies though. I would classify you as a newbie, so your OK in my book lol. Your problem appears to be related to PHP now, not Apache.

---

### Post by spizkapa on 2005-11-12
[QUOTE=Todd_Z]
```

E: phpmyadmin: subprocess pre-removal script returned error exit status 127

```
[/QUOTE]

Aha, you've hit a snag in the whole deb package business. You're in some trouble now but don't despair. Each package comes with various scripts, a preinstall one, a post-install one, a pre-removal one and others. A well configured package shouldn't break like this.

But, at least we know what your problem is. You need to fix up your package list. Try:

apt-get -f update

This should tell you what packages need to be removed/reinstalled in order to get your package list right again. If it asks you to remove a whole load of packages that look serious, don't do it, it will get you in a mess.

While this is quite bad, normally, it's easy to fix it with the command above. But, before you do this do:

man apt-get

and pay particular attention to the check, -f (--fix-broken) flags. You'll be up and running again in no time.

---

### Post by Todd_Z on 2005-11-13
```

Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy Release
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Fetched 19.8kB in 2s (9793B/s)
Reading package lists... Done

```

Its a real nice list, but idk what to do with it...

---

### Post by Todd_Z on 2005-11-13
Still not having any luck with this - I have no idea what to do to fix phpmyadmin

Solved: [http://www.ubuntuforums.org/showthread.php?t=79934](http://www.ubuntuforums.org/showthread.php?t=79934)

---

