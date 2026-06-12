---
title: "Uninstalling unneeded programs"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-03
Bittorrent--is this needed by the OS at all (not sure if this is used when downloading critical system updates?)  If not, I'd like to uninstall it because I've never used it on my Windows system and can't think of a reason to start using it.  I don't really download much except for the occasional driver, demo, patch, etc.  Not knowing how critical bittorrent is to Ubuntu, I don't want to uninstall it til I'm sure it's not needed.
Evolution--how do I uninstall this?  When I do a search for the title in Synaptic a whole bunch of things pop up that are related, but more like plugins (ie, OpenOffice).  What can I safely uninstall without breaking something else?  There were little a dozen items that were flagged as related to Evolution--don't know if I can safely remove them all??

Thanks

---

### Post by Cypher on 2007-05-03
Bittorrent isn't used by Ubuntu per say, it can be used by you to download Torrents from the web. If you don't do that kind of stuff, by all means remove it.

Evolution is the default mail program that comes bundled with Ubuntu. Unless you're using a different email program and never intend to use this one, I see no real reason to remove it..

---

### Post by timzak on 2007-05-03
> **Cypher said:**
> Bittorrent isn't used by Ubuntu per say, it can be used by you to download Torrents from the web. If you don't do that kind of stuff, by all means remove it.

Evolution is the default mail program that comes bundled with Ubuntu. Unless you're using a different email program and never intend to use this one, I see no real reason to remove it..

I use Tbird.  Won't be using Evo and would like to free up the resources/space it uses.

Thanks.

---

### Post by Cypher on 2007-05-03
OK, then go to the Synaptic Package Manager and find search for "Evolution" and find the package just by itself with nothing else in it's name, this should be the main package. Mark it for removal and all of it's dependencies should be marked for removal as well. Now apply and everything that is no longer needed should get un-installed..

---

### Post by rsambuca on 2007-05-03
Don't remove Bittorrent as it will cause you to remove the ubuntu-desktop, which I am pretty sure you want.  If it bugs you to keep seeing it in your Applications menu, you can easily remove the icons from your applications menu by right-clicking on the applications button, then selecting 'edit menus'.

Is there a reason you need to remove these programs?

---

### Post by timzak on 2007-05-03
> **rsambuca said:**
> Don't remove Bittorrent as it will cause you to remove the ubuntu-desktop, which I am pretty sure you want.  If it bugs you to keep seeing it in your Applications menu, you can easily remove the icons from your applications menu by right-clicking on the applications button, then selecting 'edit menus'.

Is there a reason you need to remove these programs?

Call me a neatfreak, but I just don't like having programs taking up resources and space if I'm never going to use them.  Plus, a smaller footprint makes backing up quicker.  Why is bittorrent tied into the ubuntu desktop?

---

### Post by galvatron1983 on 2007-05-03
why would removing a BitTorrent app cause the entire Ubuntu desktop to be removed???

---

### Post by chalex on 2007-05-03
He means the "ubuntu-desktop" meta-package, which depends on a bunch of packages that are considered the core of the distribution.

Removing the "ubuntu-desktop" meta-package will likely cause you problems down the line when you upgrade releases.

---

### Post by rsambuca on 2007-05-03
If you don't want all of these extra programs that are part of the ubuntu desktop, then you will have to do a barebones server installation, and then select individually what packages you want installed on your system.

You can find very good instructions on how to do this [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/minimal#barebones").

---

### Post by rsambuca on 2007-05-03
You know bittorrent is only 291kb, and it's not like it is running all the time?  Do you have a tiny hard drive or something?

---

### Post by timzak on 2007-05-04
> **rsambuca said:**
> You know bittorrent is only 291kb, and it's not like it is running all the time?  Do you have a tiny hard drive or something?

This IS the absolute beginners forum.  I wouldn't be posting here if I wasn't a newbie.  Cut me some slack.  What's wrong with uninstalling apps you won't ever use?

I did ask in my opening post if it was needed by the OS--and apparently it is from what you say, so I guess I'll leave it alone.

Thanks.

---

### Post by rsambuca on 2007-05-04
Hey no sweat!  I'm sorry if I came across the wrong way.  I was just trying to let you know that it isn't a big program.

---

### Post by underwatercow on 2007-05-10
There are other reasons that one might want to uninstall bit torrent. I was trying to install a newer version of bit torrent and I can't without removing bit torrent and the ubuntu-desktop.

---

