---
title: "Security!"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-27
Hi everyone,

What a brilliant, brilliant operating system... WOW!  Windows is fast becoming a thing of the past for me.  I am just plucking up the courage now to delete it entirely from my system once I have figured out how to run the likes of Half Life 2 in Ubuntu.  

At the moment, however, I am looking for a suitable replacement for an excellent program I used in XP called Steganos.  It was a fantastic encryption program/password manager and I was also able to create a secure safe with it.  Does anyone know of a suitable linux package that would do the same job?  Also, when I viewed internet pages in XP, I was able to delete temporary internet files (using steganos) from the temporary internet folder.  Is there an equivelant file in Ubuntu?  And finally, is there a defrag tool available in Ubuntu or is this not necessary? 

Thank you for any help with these questions.

---

### Post by aysiu on 2006-03-27
[QUOTE=Norfolk 'n' Good]
At the moment, however, I am looking for a suitable replacement for an excellent program I used in XP called Steganos.  It was a fantastic encryption program/password manager and I was also able to create a secure safe with it.  Does anyone know of a suitable linux package that would do the same job?[/quote] *kgpg* or *gpgp* maybe? You'll need [extra repositories](http://www.psychocats.net/ubuntu/sources) for those. > Also, when I viewed internet pages in XP, I was able to delete temporary internet files (using steganos) from the temporary internet folder.  Is there an equivelant file in Ubuntu? Are you using Firefox? Control-Shift-Delete will delete private data.  > And finally, is there a defrag tool available in Ubuntu or is this not necessary? It's not necessary. Ext3 doesn't fragment significantly.

---

### Post by IYY on 2006-03-27
> Also, when I viewed internet pages in XP, I was able to delete temporary internet files (using steganos) from the temporary internet folder. Is there an equivelant file in Ubuntu?

Well, there is an a button you can click on firefox that completly clears the cache, history and passwords. 

> And finally, is there a defrag tool available in Ubuntu or is this not necessary? 

As long as your system has a reasonable amount of free space, defrags are not necessary at all.

---

### Post by colo on 2006-03-27
1.) Games may be run by Transgaming's Cedega.
-> [http://www.transgaming.com/](http://www.transgaming.com/)

2.) There are numerous ways of encrypting a filesystem on the fly in GNU/Linux. One of the more user-friendly approaches is EncFS. Try doing a forum- or google-search, I'm sure you'll find something suitable.

3.) In Mozilla Firefox 1.5.x, there's a quick shortcut to delete all your private data from the caches. Just wait for ubuntu Dapper to be released (06-01-2006, I believe), and update your system, so Firefox 1.5.0.1 is installed. For the time being, you may want to delete your ~/.mozilla-directory. This, however, reverts ALL your personal browser settings to the system's default, and annihilates your saved passwords, form data, bookmarks(!) and the like.

4.) There IS a proprietary, commercial defrag-equivalent for Linux-filesystems, it is regarded as absolutely not needed, however.

---

### Post by Norfolk 'n' Good on 2006-03-27
Thank you for that... I shall explore those recommendations.

---

### Post by derelict on 2006-03-27
If you're looking for an easy to use app: [http://www.canudo.net/derelict/freesecurity](http://www.canudo.net/derelict/freesecurity)

---

### Post by aysiu on 2006-03-27
[QUOTE=colo]
3.) In Mozilla Firefox 1.5.x, there's a quick shortcut to delete all your private data from the caches. Just wait for ubuntu Dapper to be released (06-01-2006, I believe), and update your system, so Firefox 1.5.0.1 is installed.[/quote] You don't have to wait two months for Dapper's release. You can install Firefox 1.5.0.1 in Breezy quite easily using [this](http://www.psychocats.net/ubuntu/firefox) or [this](https://wiki.ubuntu.com/FirefoxNewVersion). > For the time being, you may want to delete your ~/.mozilla-directory. This, however, reverts ALL your personal browser settings to the system's default, and annihilates your saved passwords, form data, bookmarks(!) and the like. That's rather extreme. I wouldn't advise deleting the ~/.mozilla directory unless you have a corrupt profile, and then only after having backed up your bookmarks.

---

### Post by colo on 2006-03-27
[QUOTE=derelict]If you're looking for an easy to use app: [http://www.canudo.net/derelict/freesecurity](http://www.canudo.net/derelict/freesecurity)[/QUOTE]

This thing is NON-FREE and does NOT offer filesystem-transparent en- or decryption. I'd recommend any viable alternative over this one.

---

### Post by derelict on 2006-07-06
[QUOTE=colo]This thing is NON-FREE and does NOT offer filesystem-transparent en- or decryption. I'd recommend any viable alternative over this one.[/QUOTE]

It's free for personal use (it's one of the reasons why it was made). As to FS transparent encryption, that's a feature that may be added later on.

---

