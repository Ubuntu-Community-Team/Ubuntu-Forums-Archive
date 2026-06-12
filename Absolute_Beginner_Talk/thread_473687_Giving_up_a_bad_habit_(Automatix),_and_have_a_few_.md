---
title: "Giving up a bad habit (Automatix), and have a few questions."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-06-14
Hello, everyone.

I have used Automatix to install applications and such over the past year or so.  Well, I finally did a full installation of Ubuntu (Windows is gone, except for a future virtual machine so that I can still use my Lexmark printer), and after using Automatix, I've discovered that some things are broken. :(  It is alright, though.  I am going to do a fresh installation this weekend and start from scratch, and go the route fo using simply the package managers and manual installation configuration, if necessary.

Anyway...

I just have a big question that I have been curious about...actually more like two questions...

First, when I install Java/Flash/etc on my user account, will all other user accounts automatically have this installed?  Or will I have to install the Firefox plugins and such for each individual account?

And secondly...I don't know if this is just some weird problem...but I have (now) an 80GB partition which I am going to use to store things such as music and backups.  For some reason, only my account can access items on this partition.  It si formatted in ext3.  Does this sound right, or did I do somethign wrong here?  Basically, my wife and I use Banshee for listening to music, and I want to import songs from the separate partition (on the 80GB drive).  It works fine under my account, but not at all under my wife's account.  Any ideas on this one?

Thanks, everyone for any help.  I liked using Automatix in the past, but if I wish to attain a level fo knowledge to become (maybe one day) a Linux administrator, I feel that I need to just learn to do things myself...

Thanks again, and take care.

---

### Post by domat00 on 2007-06-14
Try going into Users and Groups and changing your wifes permissions to the same as yours for that disc, or navigate to the disc, right click it, tab to Permissions, for the drop down menus and click Read-only if you only want her to be able to access the disc, or Read and Write if you want her to be able to Write to the disc also.

---

### Post by Kobalt on 2007-06-14
Installing Java & Flash through Add/Remove or Synaptic will make it available for all users. 
By the way : giving up Automatix is a good thing in my opinion.

---

### Post by ccfjeff on 2007-06-14
> **Kobalt said:**
> By the way : giving up Automatix is a good thing in my opinion.

But giving up Windows is even better!
:popcorn:

---

### Post by starcraft.man on 2007-06-14
> **Kobalt said:**
> Installing Java & Flash through Add/Remove or Synaptic will make it available for all users. 
By the way : giving up Automatix is a good thing in my opinion.

Seconded. Depending on an unofficial installer can lead to problems...

Banshee is a great music program btw, I love it :).

Oh and lastly, with regard to permissions... if your really aiming to learn and use it very well I [recommend this tutorial on linuxcommand.]("http://www.linuxcommand.org/lts0070.php") You may want to read the first 6 a bit before getting to it, most is self contained though, the terminal has many functions simply not conveyed to the GUI.

---

### Post by RKCole on 2007-06-14
OH, no problems with permissions and such, but that site will be a good reference.  I actually (for the most part) prefer the terminal for getting things done; it's just faster.

Anyway, Automatix did break some things, and somewhat badly at that.  Any AA (Automatix Anonymous) groups around? :)  O)kay...I apologize for that one...it was a bit harsh, but I'm tired and trying to keep in a good mood. :)

Anyhow, I'm off to reinstall.

Take care, and thanks for the replies.

---

### Post by RKCole on 2007-06-14
I'm still amazed at the installation time for Ubuntu.  Between my two hard drives I have 320GB fo space, and the Ubuntu installation completed in about thirty minutes.

Okay, so no more Automatix.  Now, is [http://www.getdeb.net](http://www.getdeb.net) alright to use to get newer applications?  I just wnat to make sure I do things right this time as this isntallation is here to stay; no more fresh installs (hopefully) for me until I get another computer. :)

Thanks, everyone.

Take care.

---

### Post by arnieboy on 2007-06-15
> **RKCole said:**
> Anyway, Automatix did break some things, and somewhat badly at that. 
Really? Like what?

---

### Post by RKCole on 2007-06-17
I did a fresh install fo UBuntu (before this one) and put Automatix in as I usually did.  I have no idea as to why this happened, but I set up some other user accounts (for my wife and my sister-in-law/brother-in-law), and then I used Automatix to install the AUD-DVD and Multimedia codecs.  After doing that, things just started acting kind fo strangely.

I had never had any problems with Automatix before this point; I really enjoyed using it.

The thing is...I am working toward (hopefully) obtaining my Linux+/UBuntu certifications, and I really want to learn how the system works the way it does and why.  For example, I just installed Thunderbird 2 today by using the tarball file from Mozilla, which I had never done before.  In Automatix, I simply checked the option indicating that I wanted to install Thunderbird 2, clicked the start button, and ti was done.

In any case, upon installing the AUD/DVD codecs, the sound and video did not work too well; as to why I am not too sure.

I do, however, apologize for my remarks in my original post.  I was kind fo frustrated becaus efo the entire situation.  But now things are running smoothly.

Thanks for all of the input related to this situation.

Take care.

---

### Post by meborc on 2007-06-17
getdeb.net is as good as any other site with debs :) ... oh, and read the [www.ubuntuguide.org](www.ubuntuguide.org) to get a general idea how to install stuff without using scripts

---

