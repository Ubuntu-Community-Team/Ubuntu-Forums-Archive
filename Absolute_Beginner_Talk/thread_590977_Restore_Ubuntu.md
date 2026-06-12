---
title: "Restore Ubuntu?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by HMartinho on 2007-10-25
Hi folks;

Here's the deal, I've unninstaled and installed lots of stuff in these couple of days since 7.10 came out.
Several attemps at compiz fusion from git and source compiling, more than enough bars and docks, and in the process I've also managed to install lots of KDE stuff wich now appear in a new menu even if I'm running gnome's gutsy version (not kubuntu), this catastrofic trick was done with a script i saw to install compiz, it installed a ton of KDE apps but no compiz, lol.

Is there an easy way to get everything back to default, with only the stuff that came with the installation?
Or is it better if I just format and install it over again?

In grub there are 4 entries to select from, two normal and two generic, one fault-safe (or similar) of each, what are these by the way?

Thanks in advance.

Cheers

---

### Post by mikeyphi on 2007-10-25
> **HMartinho said:**
> Hi folks;

Is there an easy way to get everything back to default, with only the stuff that came with the installation?
Or is it better if I just format and install it over again?

In grub there are 4 entries to select from, two normal and two generic, one fault-safe (or similar) of each, what are these by the way?

Short answer to first point is No - unless you made an image before the changes!! So consider a clean install.

Grub has two entries for each version of the kernel - the number shown depends on your setup. But it doesn't matter - you can boot into any of them, however, probably only the latest will support all the other software fully.

---

### Post by HMartinho on 2007-10-25
Thanks , thats all i wanted to ear, back to zero then, will re-install everything later on tonight.
This time however, one of the first things to install will be a backup manager and do a backup as soon as everything is working by default.
Could you recommend some backup apps?

Cheers.

---

### Post by mikeyphi on 2007-10-25
I use sbackup on a daily basis

If you like playing around - you might consider using partimage to store a full compressed copy of your system.

---

### Post by zeddock on 2007-10-25
I used sbackup to backup some of my most needed things.  Now I cannot recover them.
Here are some issues:
1. I thought I could name folders and files just about anything.  So, for high visibility I named a folder "|||MyDocs|||".  I am an idiot!
2. I can see some of the folders that I want to recover, but they are appearing now as files, not folders.  Can I change them back?  
3. When I try to run the recovery it takes a while, but when it finishes there is just an empty folder of same name.

Any help is obviously appreciated.

zeddock

---

### Post by bratliff on 2007-11-07
I would like to do that, but don't see how.

Ratliff


> **mikeyphi said:**
> I use sbackup on a daily basis

If you like playing around - you might consider using partimage to store a full compressed copy of your system.

---

