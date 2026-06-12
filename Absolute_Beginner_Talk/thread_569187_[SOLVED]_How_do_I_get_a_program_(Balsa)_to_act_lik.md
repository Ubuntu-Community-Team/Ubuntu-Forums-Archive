---
title: "[SOLVED] How do I get a program (Balsa) to act like its the first time being run?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-10-06
I'm going crazy trying to get this to do what I want to do.

When I first installed Balsa (a GNOME email program) it ran through a starting Druid (I guess that's the GNU/Linux equivalent of a wizard).

I need to run that again!

I've tried marking it for complete removal. It was my understanding that when you do that, it removes every trace of that program, including configuration files.

But when I get it back on, it still has my old settings in there, with some settings that apparently can only be created the first time you run it (creating an mbox file in var/mail, etc.).

I find it a little troubling that there are so many scabs from things I thought I had removed completely, maybe that is just a misunderstanding of how Synaptic works. But I'll put aside my reservations if someone could tell me how I can just get this program to run the starting druid again, forgetting all the settings it has from me.

---

### Post by Dr Small on 2007-10-06
Did you run:
```
sudo apt-get remove balsa --purge
```
?

---

### Post by Lord Illidan on 2007-10-06
I'd ask in the balsa mailing list, too.
[http://mail.gnome.org/mailman/listinfo/balsa-list](http://mail.gnome.org/mailman/listinfo/balsa-list)

---

### Post by keyboardashtray on 2007-10-06
> **Dr Small said:**
> Did you run:
```
sudo apt-get remove balsa --purge
```
?

Just tried it, no luck. It still has my settings in there when I reinstalled. Also, it doesn't even download anything when I reinstall, it is like they are already there.

---

### Post by Lord Illidan on 2007-10-06
> **keyboardashtray said:**
> Just tried it, no luck. It still has my settings in there when I reinstalled. Also, it doesn't even download anything when I reinstall, it is like they are already there.

That's because apt caches its downloads, so it doesn't have to download them again.

---

### Post by RomeReactor on 2007-10-06
Hi. Try looking in your home folder for a hidden **.balsa** folder; if you find one, delete it and run the program again. Open Nautilus in your home folder and press CTRL+H to see the hidden files and folders.

---

### Post by keyboardashtray on 2007-10-06
> **Lord Illidan said:**
> That's because apt caches its downloads, so it doesn't have to download them again.

Ahh, thank you! That is good to know for future reference.

---

### Post by keyboardashtray on 2007-10-06
> **RomeReactor said:**
> Hi. Try looking in your home folder for a hidden **.balsa** folder; if you find one, delete it and run the program again. Open Nautilus in your home folder and press CTRL+H to see the hidden files and folders.

Thank you RomeReactor!! I did find a .balsa folder, and inside it I found a configuration file that had the paths to the directories I was trying to change, that it wouldn't let me change from within the program.. I didn't delete it and uninstall - I'm betting that would have worked too though, huh? But the bottom line is I got it set up now the way I wanted to.

Much appreciation, thanks again :)

---

### Post by GavinZac on 2007-10-06
just to clarify, the vast majority of your settings and configurations are in your home folder as those hidden/dot folders (e.g. ~/.wine, ~/.firefox), not just balsa's :)

---

### Post by RomeReactor on 2007-10-06
> **GavinZac said:**
> just to clarify, the vast majority of your settings and configurations are in your home folder as those hidden/dot folders (e.g. ~/.wine, ~/.firefox), not just balsa's :)

That's right; when you want a program to do a first run, in most cases deleting the hidden configuration folder in your home will do. No need to uninstall.

---

### Post by keyboardashtray on 2007-10-06
> **GavinZac said:**
> just to clarify, the vast majority of your settings and configurations are in your home folder as those hidden/dot folders (e.g. ~/.wine, ~/.firefox), not just balsa's :)

> **RomeReactor said:**
> That's right; when you want a program to do a first run, in most cases deleting the hidden configuration folder in your home will do. No need to uninstall.

Thanks guys - I'll keep that in mind. So is it safe to say, if it is in your home folder, it is usually safe (from a program stability standpoint) to delete those hidden folders if you don't think you need them? Edit: I mean, if you aren't afraid of losing settings?

---

### Post by GavinZac on 2007-10-06
> **keyboardashtray said:**
> Thanks guys - I'll keep that in mind. So is it safe to say, if it is in your home folder, it is usually safe (from a program stability standpoint) to delete those hidden folders if you don't think you need them?

Yes, it works 2 ways - you can delete those files if they are causing a problem, but also if there is a problem with the" program files" themselves in the other areas of the file system, it wont affect your own settings and configs in your home directory . e.g. during an upgrade

---

### Post by keyboardashtray on 2007-10-06
> **GavinZac said:**
> Yes, it works 2 ways - you can delete those files if they are causing a problem, but also if there is a problem with the" program files" themselves in the other areas of the file system, it wont affect your own settings and configs in your home directory . e.g. during an upgrade

Oh, cool. Good to know. Nice avatar by the way :cool:

---

### Post by GavinZac on 2007-10-06
> **keyboardashtray said:**
> Oh, cool. Good to know. Nice avatar by the way :cool:

:D thanks, i reckon you'll like my desktop too :)

[IMG]http://img172.imageshack.us/img172/6954/screenshotxh0.png[/IMG]

---

### Post by keyboardashtray on 2007-10-06
> **GavinZac said:**
> :D thanks, i reckon you'll like my desktop too :)


Ha - nice! Glad you left out this one:
[IMG]http://www.mobygames.com/images/i/10/49/345999.png[/IMG]

---

### Post by Mark76 on 2008-06-14
Has anyone noticed that Balsa sends new mail to a directory that doesn't exist (unless you create it)?

Luckily it's not too much hassle to redirect it to one that does :)

---

