---
title: "Update Manager and Distro updates"
date: 2012-09-14
forum: Any Other OS
---

### Post by UltimateCat on 2012-09-14
Hi:

I'm running Debian 6.0.5 Stable-

My Update Manager alerted me that I had 17 updates available. Of course the first thing I did was started to sort through them. So.... I Googled a few of them to see what the case was.
<libnm-glib2> for example is for Sid/Unstable and I found it at:
[http://packages.debian.org/sid/libnm-glib2](http://packages.debian.org/sid/libnm-glib2)
Obviously; I won't be installing this update as it is for Sid. But...

How do I delete these updates that I do not want?

Besides using <#apt-get purge <name of update> is there any other way to delete unwanted updates and 3rd party junk?

And these 3rd party software updates keep finding their way into my Update Manger; Is there a way that I can find out where they are coming from?

Thanks in advance-

---

### Post by critin on 2012-09-14
> **UltimateCat said:**
> Hi:

I'm running Debian 6.0.5 Stable-

My Update Manager alerted me that I had 17 updates available. **Of course the first thing I did was started to sort through them. So.... I Googled a few of them to see what the case was.**
<libnm-glib2> for example is for Sid/Unstable and I found it at:
[http://packages.debian.org/sid/libnm-glib2](http://packages.debian.org/sid/libnm-glib2)
Obviously; I won't be installing this update as it is for Sid. But...

How do I delete these updates that I do not want?

Besides using <#apt-get purge <name of update> is there any other way to delete unwanted updates and 3rd party junk?

And these 3rd party software updates keep finding their way into my Update Manger; Is there a way that I can find out where they are coming from?

Thanks in advance-

You don't trust it?  Unless I knew more than the devs, I would install all recommended updates.  This particular update is not used in 'sid' only.  It affects many libraries, and has to do with network.

> <libnm-glib2> for example is for Sid/Unstable and I found it at:
[http://packages.debian.org/sid/libnm-glib2](http://packages.debian.org/sid/libnm-glib2)
Obviously; I won't be installing this update as it is for Sid. But...You're using Squeeze?  It's still used ---it obviously made Sid stable.

Third party are those packages that you've installed yourself.[I] Check your applications 
that you installed from the web and uncheck those 
that you think may  contain 'junk'.

If you KNOW[/I] you don't want to install something, just uncheck the box on the update notice.  Be sure you know though or you may be back here wanting to know why you can't get on the network. And this issue would be difficult for anyone to track down.

---

### Post by cortman on 2012-09-14
> **UltimateCat said:**
> Hi:

I'm running Debian 6.0.5 Stable-

My Update Manager alerted me that I had 17 updates available. Of course the first thing I did was started to sort through them. So.... I Googled a few of them to see what the case was.
<libnm-glib2> for example is for Sid/Unstable and I found it at:
[http://packages.debian.org/sid/libnm-glib2](http://packages.debian.org/sid/libnm-glib2)
Obviously; I won't be installing this update as it is for Sid. But...

How do I delete these updates that I do not want?

Besides using <#apt-get purge <name of update> is there any other way to delete unwanted updates and 3rd party junk?

And these 3rd party software updates keep finding their way into my Update Manger; Is there a way that I can find out where they are coming from?

Thanks in advance-

3rd party junk? Only if you added repositories to your sources.list- otherwise it's only the Debian main repos.
FYI, Debian doesn't use PPAs by default- and it's best not to add them- that's a Launchpad (Ubuntu) thing.

---

### Post by UltimateCat on 2012-09-14
Critin:
You said" I would install all recommended updates"

Perhaps I shouldn't let a one time bad experience rule here.

I allowed 2 updates to install a few weeks ago and directly after the install Iceweasel became unstable. I later found on the Debian website that they (packages) were experimental and unstable.  If fact the e-mail Debian Security set me confirmed the buggy, unstable, experimental etc.

I will think again about this and think twice before I uncheck updates.
Thank you for wise counsel.

---

### Post by UltimateCat on 2012-09-14
Cortman:

Thanks for the sources list reminder-

I did add recently the httpL//deb-multimedia.org.........etc. to my sources list.

Thank you for telling me about PPA's and that it is best not to add them.

Have a good weekend!

---

### Post by cortman on 2012-09-15
> **UltimateCat said:**
> Cortman:

Thanks for the sources list reminder-

I did add recently the httpL//deb-multimedia.org.........etc. to my sources list.

Thank you for telling me about PPA's and that it is best not to add them.

Have a good weekend!

Sure- sources.list is a big thing in Debian, as it is THE place where all software sources come from (and determines how "free" your installtion is as well).
While you can probably add a PPA (you'd have to install add-apt-repository) it's best not to- Ubuntu and Debian are not 100% binary compatible, and unhealthy things can happen.
You have a great weekend too. :)

---

### Post by UltimateCat on 2012-09-16
Thanks again-;)

Good help is appreciated!

Closing the thread-

---

