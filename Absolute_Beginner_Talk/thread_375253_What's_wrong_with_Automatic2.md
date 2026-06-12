---
title: "What's wrong with Automatic2"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-03
[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.10-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.10-6.06dapper_i386.deb)

I have tried three time to download the Dapper 6.06 version of Automatix from the above URL.

I copied/pasted/<entered> each of the six command prompts into Terminal. Afterwards, I locate Automatix2 via Applications->System Tools->Automatix and click on it, It opens. I press the "yes" and then it tells me that I have version 6.10 and is meant for Edgy. What happened to the 6.06 that should have downloaded? 

Each time I have opened Synaptic and "completley" removed Automatix. I tried installing Automatix2 for Dapper 6.06 again. I keep getting the same result. I did this on my first install of Dapper 6.06 about two weeks ago. It worked just fine then. I uninstalled Dapper and tried Edgy. I didn't like it and came back to Dapper 6.06. Before I reinstalled Dapper, I reformatted my hard drive to make sure that it was clean.

Has anyone else had this problem? If you have, what did you do to correct it?

Thank you for any assistance you can give me on this problem.
kh

---

### Post by stokedfish on 2007-03-03
> **kittyhawk63 said:**
> Before I reinstalled Dapper, I reformatted my hard drive to make sure that it was clean.
Uhm, why don't you use Edgy?

---

### Post by oilchangeguy on 2007-03-03
the question is why use a test version, which is what edgy is. when you can use dapper and get support for 3 years, not 3 months, as in edgy. 

in answer to the automatix question, their website has been having problems off and on for the past several weeks. so being able to get it to download is going to be a crap shoot. just keep trying.

---

### Post by stokedfish on 2007-03-03
Sure, but you'll also get old software on Dapper, like an outdated Amarok, KDE, and so on.

A test version? It runs beautifully here... :)

---

### Post by taurus on 2007-03-03
What does your /etc/apt/sources.list look like then?

```
cat /etc/apt/sources.list
```

---

### Post by stokedfish on 2007-03-03
Mine? I'm on Edgy, not on Dapper.

Not sure who you mean and why this question... *confused*

---

### Post by taurus on 2007-03-03
> **stokedfish said:**
> Mine? I'm on Edgy, not on Dapper.

Not sure who you mean and why this question... *confused*

I am talking about the original OP, kittyhawk63, not you!

---

### Post by kittyhawk63 on 2007-03-03
[quote=taurus;2242254]What does your /etc/apt/sources.list look like then?

Sorry, Taurus, my wife called me away for a few minutes.

Here is what you asked for:

kittyhawk63@kittyhawk63:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
kittyhawk63@kittyhawk63:~$

---

### Post by taurus on 2007-03-03
> **kittyhawk63 said:**
> ## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
kittyhawk63@kittyhawk63:~$

Your /etc/apt/sources.list is completely wrong.  You cannot mix repos (breezy and dapper) or things will break and trash your machine.  Also, you cannot use edgy with Automatix since you are using dapper.

Therefore, edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
and replace the word breezy with the word dapper in these two lines.

```

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **breezy**-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) **breezy**-extras main restricted universe multiverse

```
Then, remove these lines, leaving only one line for Automatix (with dapper in it).

```

deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt dapper main
deb http://www.getautomatix.com/apt dapper main
deb http://www.getautomatix.com/apt dapper main
deb http://www.getautomatix.com/apt dapper main

```
Save the changes.  Then, run

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by kittyhawk63 on 2007-03-03
[quote=taurus;2242362]Your /etc/apt/sources.list is completely wrong.  You cannot mix repos (breezy and dapper) or things will break and trash your machine.  Also, you cannot use edgy with Automatix since you are using dapper.

[B]I posted a "complete" reply to your request. I missed some on the post reply to your request. Reload and you will see it. I don't know how Breezy got onto the list. I have not tried installing it. If I did, I don't remember doing it. I will remove the lines as you have instructed. Again you may want to look at my edited post again.
Thank you Taurus.[/B]

---

### Post by cantormath on 2007-03-03
> **stokedfish said:**
> Uhm, why don't you use Edgy?

Dapper is LTS and is probably more stable.

---

### Post by cantormath on 2007-03-03
> **stokedfish said:**
> Sure, but you'll also get old software on Dapper, like an outdated Amarok, KDE, and so on.

A test version? It runs beautifully here... :)

not true

you can install that stuff on dapper if you wish.

---

### Post by kittyhawk63 on 2007-03-03
[quote=taurus;2242362]Your /etc/apt/sources.list is completely wrong.  You cannot mix repos (breezy and dapper) or things will break and trash your machine.  Also, you cannot use edgy with Automatix since you are using dapper.

Here is the reply to your first line:

kittyhawk63@kittyhawk63:~$ **sudo /etc/apt/sources.list**
Password
sudo: /etc/apt/sources.list: **command not found**
kittyhawk63@kittyhawk63:~$

---

### Post by taurus on 2007-03-03
Try

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-03-03
> **taurus said:**
> Try

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```

Here is the reply to the first line. I took off the # before the "deb" line and save. Again, here is the reply;

kittyhawk63@kittyhawk63:~$ gksudo gedit /etc/apt/sources.list

(gedit:10953): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:10953): WARNING **: Could not load python module modelines


** (gedit:10953): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

---

### Post by Doomedelite on 2007-03-03
I actually had more problems with dapper (Gaim didn't work, firefox shutting down, etc.) than with edgy. I feel edgy is just a big bug update, kind of like SP2 for windows. Some things that work on edgy do _not_ work on dapper. It's not a "beta" or anything, it's a fully fledged upgrade, and I can't wait for feisty fawn to be released. I never try the betas, but once they're released, I'm all on it. Worst thing that will happen, is that you must start booting from edgy again, and just re-install feisty.

---

### Post by taurus on 2007-03-03
> **kittyhawk63 said:**
> Here is the reply to the first line. I took off the # befroe the "deb" line and save. Again, here is the reply;

kittyhawk63@kittyhawk63:~$ gksudo gedit /etc/apt/sources.list

(gedit:10953): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:10953): WARNING **: Could not load python module modelines


** (gedit:10953): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

In that case, use nano from a terminal then.

```
sudo nano -w /etc/apt/sources.list
```
When you are done, do <Ctrl>o and <Ctrl>x to save and exit.

---

### Post by kittyhawk63 on 2007-03-03
> **Doomedelite said:**
> I actually had more problems with dapper (Gaim didn't work, firefox shutting down, etc.) than with edgy. I feel edgy is just a big bug update, kind of like SP2 for windows. Some things that work on edgy do _not_ work on dapper. It's not a "beta" or anything, it's a fully fledged upgrade, and I can't wait for feisty fawn to be released. I never try the betas, but once they're released, I'm all on it. Worst thing that will happen, is that you must start booting from edgy again, and just re-install feisty.

I read so many threads telling novices to stay with Dapper. It seems quite clear that you don't agree. When I can figure out some of the ways to fix bugs, like the one in this thread, I may decide to move on to Feisty. I will forgo Edgy altogether. Thank you for your input.
kh

---

### Post by kittyhawk63 on 2007-03-03
> **taurus said:**
> In that case, use nano from a terminal then.

```
sudo nano -w /etc/apt/sources.list
```When you are done, do <Ctrl>o and <Ctrl>x to save and exit.

Sudo nano worked. What's next? Is there a list of these sudo commands somewhere that explain them good?

---

### Post by taurus on 2007-03-03
After you've made the changes, run

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by kittyhawk63 on 2007-03-03
> **taurus said:**
> After you've made the changes, run

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```

I removed the # from the "deb" lines. 

Ran all three of the above sudo commands.

Still getting Automatix2 for Edgy. Grrrrr!

---

### Post by kittyhawk63 on 2007-03-03
Taurus, GetAutomatix.com must be having a problem with their server. What do you think?

---

### Post by taurus on 2007-03-03
I can connect to [http://www.getautomatix.com](http://www.getautomatix.com) just fine right now.  Can you post your /etc/apt/sources.list again and the output of this command?

```
locate automatix2
cat /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-03-03
> **taurus said:**
> I can connect to [http://www.getautomatix.com](http://www.getautomatix.com) just fine right now.  Can you post your /etc/apt/sources.list again and the output of this command?

```
locate automatix2
cat /etc/apt/sources.list
```

Here you go:
I see it now, I need to get rid of Breezy and Edgy.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by kittyhawk63 on 2007-03-03
Taurus, do I need all those repetitive lines at the end? Can I just have one of them?

I'm going to run those three sudo commands again.

---

### Post by kittyhawk63 on 2007-03-03
**Eureka**! Got it working. Thanks alot Taurus. Three gold stars. :KS:KS:KS
kh

---

### Post by taurus on 2007-03-03
Looks to me like you haven't done anything to your /etc/apt/sources.list at all!  Again, you need to replace the word breezy with dapper and remove those lines at the bottom regarding automatix, leaving only the last line, deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main, in there.

```
sudo nano -w /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-03-03
> **taurus said:**
> Looks to me like you haven't done anything to your /etc/apt/sources.list at all!  Again, you need to replace the word breezy with dapper and remove those lines at the bottom regarding automatix, leaving only the last line, deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main, in there.

```
sudo nano -w /etc/apt/sources.list
```

Read my last post. I finally understood what you wanted me to do, I am so new to this. Got Automatix installed for Dapper. Thanks again.

---

