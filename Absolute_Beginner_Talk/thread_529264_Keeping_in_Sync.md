---
title: "Keeping in Sync"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Raptor45 on 2007-08-19
Is there any way to keep things (Pidgin logs and buddylist for example... or regular documents even) in sync between multiple computers? I've got a desktop with both Ubuntu and Windows, in addition to a laptop and its just annoying to have to copy over folders every now and then.

I could symlink the desktop's folders I guess, but I'd rather not... and that wouldn't help with the laptop, so, any other ideas?

---

### Post by chrisphiz on 2007-08-19
You could set up rsync: sudo apt-get install rsync

On Windows there is a nice rsync package called cwrsync that will install rsync and openssh.  So you can either rsync from the linux machine to the windows, vice versa, or both.

[http://www.itefix.no/phpws/index.php?module=linkman&LMN_op=visitLink&LMN_id=1](http://www.itefix.no/phpws/index.php?module=linkman&LMN_op=visitLink&LMN_id=1) is the link to cwrsync.

Chris

---

### Post by Raptor45 on 2007-08-19
Thanks for the tip, I'll look into it.

---

### Post by msak007 on 2007-08-19
rsync is pretty much your only choice right now. If you're feeling up to the task of compiling from source, there is a Novell app called "iFolder" that seems like it has a real nice GUI for keeping multiple systems all synced together (even multiple OSes - it supports Linux, Mac, and Windows). The problem is it's not in the repos and you need to compile it to get it working (you need a server and client installed for syncing - the install procedure is very lengthy), but there are tutorials out there on installing it on Ubuntu / Debian. I saw a Launchpad bug where someone was working on (possibly) getting it included in the Gutsy repos, with the possibility of backporting to Feisty or even Edgy.

Launchpad bug:
[https://bugs.launchpad.net/ubuntu/+bug/87122](https://bugs.launchpad.net/ubuntu/+bug/87122)

I personally haven't tried it (don't have the time to mess with the compiling right now) and would be very excited if this were included in the Gutsy repos.

---

### Post by Raptor45 on 2007-08-19
iFolder seems to be the solution I'm looking for. Unfortunately, after trying for the past few hours, it seems to be a bit too complicated to install... 

I guess i'll look into rsync

---

### Post by Raptor45 on 2007-08-19
It seems rsync has good functionality for making backups, but wouldn't actually be as useful for me in this situation.

It doesn't seem like there is any way to let it handle file creation and deletion. Meaning if I have file.blah synced, and then I delete it on my laptop... when I run rsync again the file will reappear since its still on the desktop.

Any ideas how I can get around this?

EDIT: This would work for the Pidgin logs all right I suppose, since things are only added. But how about keeping home directory files in sync?

---

### Post by beuno on 2007-08-19
[[IMG]http://bugs.ubuntustats.com?id=87122[/IMG]]("https://bugs.launchpad.net/bugs/87122/")

---

### Post by msak007 on 2007-08-19
> **Raptor45 said:**
> It seems rsync has good functionality for making backups, but wouldn't actually be as useful for me in this situation.

It doesn't seem like there is any way to let it handle file creation and deletion. Meaning if I have file.blah synced, and then I delete it on my laptop... when I run rsync again the file will reappear since its still on the desktop.

Any ideas how I can get around this?

EDIT: This would work for the Pidgin logs all right I suppose, since things are only added. But how about keeping home directory files in sync?
I've never used rsync so I can't be 100% certain, but from everything I've read it only supports one way sync. There's an older project called Unison that does two way syncs, but it's not longer being updated / maintained. I searched the repos and there are packages for it (and it's GTK GUI interface). But another project I remember seeing for syncing is Conduit. It's also a Gnome app, but from what I can tell there are only Gutsy packages so once again you'll be compiling from source for Feisty. So for now unless you want to compile from source, it's either rsync or Unison. Sorry I can't be of any further help.

[http://www.conduit-project.org/](http://www.conduit-project.org/)

> **beuno said:**
> [[IMG]http://bugs.ubuntustats.com?id=87122[/IMG]]("https://bugs.launchpad.net/bugs/87122/")
Already referred him to the Launchpad bug for iFolder a couple posts up. Albeit yours is in a cooler format :)

---

### Post by Raptor45 on 2007-08-20
Thanks for the tip on conduit! I'll have to try that out. Unison seemed outdated, and.. kind-of worked but didn't really seem to have full functionality.

Found conduit on getdeb:
[http://www.getdeb.net/app.php?name=Conduit](http://www.getdeb.net/app.php?name=Conduit)

---

### Post by Raptor45 on 2007-08-20
Conduit certainly seems pretty cool. Its possible to easily set up a group of computers to sync together (ie: the home folder on 3 computers, not just two way). And it looks like theres a whole lot of other handy things to come. Unfortunately theres still a lot of development needed... so its not actually useable for me yet. Two main missing features:

-Syncing folders isn't recursive; only the top level files get synchronized. 

-No way to set up ignore rules.

Its still early in development, but Conduit certainly seems worth watching. I look forward to seeing how its improved in a few months.

---

### Post by joselin on 2007-08-20
You can try [unison,]("http://www.cis.upenn.edu/%7Ebcpierce/unison/") it's fast, easy to configure and you can pick up via apt.

Regards

---

### Post by msak007 on 2007-08-20
Yea I never used Unison either but that seemed to be the only one that would do what you wanted in its current state. Glad that Conduit seemed to be a better fit, but yea it seems pretty early in development. Unfortunately Conduit is a heavily Gnome-dependent app and wouldn't work so well for me in Kubuntu / KDE, so I'm keeping an eye on iFolder and hoping the packages make it into Gutsy. Good luck!

---

### Post by gorgor_bay on 2007-08-21
Is it possible to sync via ssh using conduit ? because I can't seem to find this option.

---

### Post by vanadium on 2007-08-21
The way you can mirror using rsync is

```

rsync -av --del source/ destination/

```

This will create a mirrored copy at the destination. The --del option will delete files at the destination that do not exist (anymore) at the source (use with care! If you inadvertently switch source and destination, or specify a wrong source, the destination will be wiped!).

After the first time, rsync is lightning fast: it only applies the changes to the destination.

---

### Post by ShirishAg75 on 2007-08-22
There is also a package called Grysnc the only trouble again it has GNOME/GTK dependencies but atleast it has the stuff. You could well do to also install ssh-askpass with it. Both are in gutsy, dunno about feisty

---

