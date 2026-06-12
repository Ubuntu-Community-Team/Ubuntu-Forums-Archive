---
title: "Best way to archive the actual programs?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Jagermaster on 2007-01-07
What is the best way to actually make backups of the programs themselves?

My issue is that I'll be needing a CD to do some off site installs of extra programs where there is NO Internet connection.

I'm sure there are a few ways to do it without missing dependencies and would love to hear any and all ideas.
Thanks,
:-k

---

### Post by 23meg on 2007-01-07
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

### Post by az on 2007-01-07
[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

or

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

### Post by tagra123 on 2007-01-07
I like aptoncd

Here it is

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Jagermaster on 2007-01-07
Thanks muchly...I wouldnt have even known where to begin to look at that topic!
Cheers!
:)

---

### Post by dsmithnc on 2007-01-07
> **tagra123 said:**
> I like aptoncd

Here it is

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Went to the site, dowloaded the .deb file and ran it.  Received a dependency error something about python-dbus.

Don't find that in synaptic.

Any help?

Dick

---

### Post by tagra123 on 2007-01-07
> **dsmithnc said:**
> Went to the site, dowloaded the .deb file and ran it.  Received a dependency error something about python-dbus.

Don't find that in synaptic.

Any help?

Dick

Try

python2.4-dbus in synaptic

I recall getting that same dependencty error.

Its running smoothly on my machine.  

Post here if 2.4 makes it go.

---

### Post by dsmithnc on 2007-01-08
> **tagra123 said:**
> Try

python2.4-dbus in synaptic

I recall getting that same dependencty error.

Its running smoothly on my machine.  

Post here if 2.4 makes it go.

Interestingly enough, 2.4-dbus was already installed but aptoncd couldn't/wouldn't see it.  Went back to the source and discovered that aptoncd doesn't work as expected on Dapper.  There is a conflict with the form of dbus it expects.  it works as advertised in Edgy.

So, I downloaded a "dapper" only release.  It installed and starts fine, but I can't seem to get it to work. It probably is my general lack of knowledge about the whole process but it gets so far as creating the files and then just stops.

So I'm back to ground zero again.

Dick

---

### Post by dsmithnc on 2007-01-08
Well, not exactly ground zero, I guess.  I have successfully created an .iso image of all the packages that were listed when the create option was chosen.  Got it copied to a cd and was able to restore.

I think it will take some time to digest the entire process and understand it.  It appears that it might be just the thing that I'm looking for.  I particularly wanted a way to restore packages easily when updated the os.  

For now I'll stick with Dapper, but I will have backups in case something crashes.

Thanks for your suggestions.

dick

---

### Post by tagra123 on 2007-01-08
Please post the link where you found the dapper only deb for aptoncd to give others reading this a heads up.

I remember tinkering to get it to work, but really do like it's easy to use interface.

For cloning a drive, or for hourly, daily, or weekly see my post here.
[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

---

### Post by dsmithnc on 2007-01-10
> **tagra123 said:**
> Please post the link where you found the dapper only deb for aptoncd to give others reading this a heads up.



Duh!  I'm sorry about that omission.  I should have done it when I found it.

Got it from this url: [https://answers.launchpad.net/aptoncd/+ticket/2874](https://answers.launchpad.net/aptoncd/+ticket/2874)

The direct link is: [http://cypherbios.org/aptoncd/aptoncd_0.1beta-1_all~dapper0.deb](http://cypherbios.org/aptoncd/aptoncd_0.1beta-1_all~dapper0.deb)

The second URL will begin the download process.  It worked very nicely.

Dick

---

