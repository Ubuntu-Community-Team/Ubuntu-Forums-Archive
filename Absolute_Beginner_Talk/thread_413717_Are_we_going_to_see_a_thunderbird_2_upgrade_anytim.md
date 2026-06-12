---
title: "Are we going to see a thunderbird 2 upgrade anytime?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-04-19
Any chance we'll see an upgrade to Thunderbird 2.0 sometime before Gutsy?

---

### Post by igknighted on 2007-04-19
> **Iamalex said:**
> Any chance we'll see an upgrade to Thunderbird 2.0 sometime before Gutsy?

Doubtful, since they didn't do a Firefox 2 upgrade for Dapper before edgy came out, I highly doubt they would backport the mail client.  You can download the 2.0.0.0 Thunderbird and extract it to /opt, then make launchers and menu icons if you want to upgrade yourself.  Shouldn't be difficult since it comes precompiled.

---

### Post by TimJBart on 2007-04-19
> **igknighted said:**
> Doubtful, since they didn't do a Firefox 2 upgrade for Dapper before edgy came out, I highly doubt they would backport the mail client.  You can download the 2.0.0.0 Thunderbird and extract it to /opt, then make launchers and menu icons if you want to upgrade yourself.  Shouldn't be difficult since it comes precompiled.

That's what I did.  thanks for the tip.  Thunderbird is very impressive!

Out of interest, what is /opt used for and what does it stand for?

---

### Post by drs305 on 2007-04-19
> **igknighted said:**
> Doubtful, since they didn't do a Firefox 2 upgrade for Dapper before edgy came out, I highly doubt they would backport the mail client.  You can download the 2.0.0.0 Thunderbird and extract it to /opt, then make launchers and menu icons if you want to upgrade yourself.  Shouldn't be difficult since it comes precompiled.

Can you elaborate on the installation once you have downloaded the tar.gz fle and extracted the Thunderbird folder?  (I'm trying to update 1.5)

Thanks.

(Listening to Pete and Joe play-by-play as I type.)

---

### Post by tehkain on 2007-04-19
> **TimJBart said:**
> That's what I did.  thanks for the tip.  Thunderbird is very impressive!

Out of interest, what is /opt used for and what does it stand for?
It is for storing items that logically do not belong anywhere else. Or even better its for placing things that seem to not fit anywhere else.

---

### Post by igknighted on 2007-04-19
I primarily use /opt to install apps that have a self contained folder.  Firefox comes like this, if you install swiftfox it goes there, and may other non-repo apps.  It is a lot easier for a user without an install script to drop a folder there than it is to try to put everything in the proper /usr/bin, /usr/lib/, etc. folders.

To install it, you really just need to extract there and make menu entries and launchers.  Instead of the command being "thunderbird" (which implies /usr/bin) you use /opt/thunderbird/thunderbird.  It should pick up your current .thunderbird folder and keep your settings.

---

### Post by drs305 on 2007-04-19
Thanks - I got tbird to run with the op/thunderbird/thunderbird command. I can open a current profile but don't seem able to save it. I have to designate the profile each time. 

I know this isn't supposed to be a thunderbird forum, so thanks for your help. I'll figure out the rest or go to the appropriate online resources to finish this up.

---

### Post by aysiu on 2007-04-19
Here are instructions for installing Thunderbird. It also includes a link to a script that will install the newest Thunderbird for you.
[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by ricardisimo on 2007-04-20
The script ended badly, as I believe it did for several others:
```
Unzipping the .tar.gz file

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
Previous command did not complete successfully. Exiting.
```
No big deal... I'll go the long route. Still, I believe it backed up my profile, which may or may not include backing up old emails. That would be a rather large file in my case, and a waste of disk space. If it did, where would I find this to delete it later? Thanks.

---

### Post by ricardisimo on 2007-04-20
Wait a second... can I just create /opt and run it again?

---

### Post by kolinab on 2007-04-20
> **ricardisimo said:**
> Wait a second... can I just create /opt and run it again?

That's exactly what I did. There was another little hiccup - I forget what it was. I think I had to go back and delete the .thunderbird folder it created elsewhere in the script - starting over from scratch. Of course making sure first I had my backup someplace safe.

It's working now.

---

### Post by aysiu on 2007-04-20
I tried it yesterday, and it worked just fine.

But I had upgraded to Feisty. I didn't do a fresh install. Does Feisty not have an /opt folder by default?

If so, I'll have to contact *nanotube* to modify the script.

---

### Post by Quillz on 2007-04-20
> **Iamalex said:**
> Any chance we'll see an upgrade to Thunderbird 2.0 sometime before Gutsy?
It might be a few weeks, but I think Thunderbird 2 will hit the repos before Gutsy Gibbon. Keep in mind that 6.06 was a LTS, and 6.10 only came out four months later, the same time as Firefox 2 was released. As 7.04 is not a LTS release and is also released just a day after Thunderbird 2, it would make sense for it to be ported sooner rather than later, especially as 7.10 will also not be a LTS release.

---

### Post by ricardisimo on 2007-04-20
> **aysiu said:**
> I tried it yesterday, and it worked just fine.

But I had upgraded to Feisty. I didn't do a fresh install. Does Feisty not have an /opt folder by default?

If so, I'll have to contact *nanotube* to modify the script.

My Feisty was, as I recall, from scratch, with no /opt folder. I was thinking someone should let the guy know as well.

By the way, created /opt, deleted symlink .thunderbird folder, and all went very well with the script. Thanks to nanotube et al.

P.S. - I deleted and then created menu items for "thunderbird". Was that necessary, or would the old menus have worked just fine?

---

### Post by aysiu on 2007-04-20
The old menus should have still worked.

We'll have to work on fixing the lack of an /opt folder in Feisty.

Thanks for bringing this to my attention.

---

### Post by kolinab on 2007-04-20
Thanks Aysiu and others for what makes these scripts work and keep working. I have used this script a couple of times and have been glad for it, small hiccups aside. It's the hiccups I learn from, forsure. 

For the record, I fresh installed the Beta of Feisty and it came with no /opt folder. But I guess I already said that.

Cheers,

K

---

### Post by ricardisimo on 2007-04-20
This question might be better off in a new thread, but has anyone had any luck installing addons and dictionaries for T-bird 2.0? The direct "web" install isn't working... keeps saying that app-x,y or z isn't compatible with Firefox. Of course it's not - it's for Thunderbird, but something isn't allowing it to see that.

Do you think the problem is related to the new /opt folder? Or perhaps the old /.mozilla-thunderbird folders? Thanks again.

---

### Post by ricardisimo on 2007-04-20
As I suspected, you have to save the installer file to your hard drive and choose that file via Thunderbird's Add-on installer. It's not a big deal, but many other noobs are most likely going to be very frustrated when they left-click "Install" in the Mozilla Add-on pages and nothing happens.

---

### Post by explemonk on 2007-04-20
> **ricardisimo said:**
> This question might be better off in a new thread, but has anyone had any luck installing addons and dictionaries for T-bird 2.0? The direct "web" install isn't working... keeps saying that app-x,y or z isn't compatible with Firefox. Of course it's not - it's for Thunderbird, but something isn't allowing it to see that.

Do you think the problem is related to the new /opt folder? Or perhaps the old /.mozilla-thunderbird folders? Thanks again.

I don't think you can do a direct "web" install with Thunderbird, because Firefox sees that the extension is .xpi and thus thinks it's for Firefox.  You have to save the xpi to your hard drive and then install it from the Tools -> Add-ons menu in TB 2 (or Tools -> Extensions in TB 1.5).

I just barely installed the en-us dictionary using this method.

---

### Post by aysiu on 2007-04-20
> **kolinab said:**
> 
For the record, I fresh installed the Beta of Feisty and it came with no /opt folder. But I guess I already said that. That's really weird, but that'd explain it.

I just checked final releases of Feisty Xubuntu and Feisty Ubuntu, and both have /opt folders by default.

So it looks as if the beta releases may have just lost the /opt folder that later got put back.

---

### Post by yabbadabbadont on 2007-04-20
> **aysiu said:**
> That's really weird, but that'd explain it.

I just checked final releases of Feisty Xubuntu and Feisty Ubuntu, and both have /opt folders by default.

So it looks as if the beta releases may have just lost the /opt folder that later got put back.

Maybe the betas "opted out"...  :D

(Hey, someone had to add some humor to this thread.  ;))

---

