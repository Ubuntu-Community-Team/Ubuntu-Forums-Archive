---
title: "Will upgrading versions screw up my internet?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by mdvigi7536 on 2007-05-06
Hi...majorly new Ubuntu user here.

I have one of those wireless internet cards in my laptop...the kind that stick out the side.  I had a friend install Ubuntu "Edgy" on it.  He had a difficult time getting the card to work...and he's amazing with Linux.

Last time I visited the Update Manager, there was a little button offering to upgrade me to the next version.  I'd like to press it, but first:

Will upgrading to another version erase whatever he did to my internet card?

I will never be able to replicate the things he did, so I want to know if "upgrading" is essentially starting from scratch or what.

Thanks for all the support I've been getting on here--this thing is really helpful.

--Mike

---

### Post by jfinkels on 2007-05-06
> **mdvigi7536 said:**
> Hi...majorly new Ubuntu user here.

I have one of those wireless internet cards in my laptop...the kind that stick out the side.  I had a friend install Ubuntu "Edgy" on it.  He had a difficult time getting the card to work...and he's amazing with Linux.

Last time I visited the Update Manager, there was a little button offering to upgrade me to the next version.  I'd like to press it, but first:

Will upgrading to another version erase whatever he did to my internet card?

I will never be able to replicate the things he did, so I want to know if "upgrading" is essentially starting from scratch or what.

Thanks for all the support I've been getting on here--this thing is really helpful.

--Mike

There is a small chance that upgrading from Edgy to Feisty will cause some problems with your wireless card. It seems that some people on these forums have had problems upgrading.

However, if you are willing to risk it, we can help you get it up and running again if it doesn't work, I promise :)

---

### Post by neodarksaver on 2007-05-06
Put the drivers u need on a flash drive, such as the windows driver file and NDISWrapper.

Just in case it wont work after the upgrade.

---

### Post by mdvigi7536 on 2007-05-06
That's a good idea about putting those files on a disk--could you please tell me where these files are on my computer so that I may save them?  I like the idea of upgrading and keeping the files on my flash drive just in case.

Thank you so much for your help.

---

### Post by neodarksaver on 2007-05-06
Well... I am a newbie also. 

NDISWrapper is here,
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Depending what ur wireless card is, you should be able to find the driver on the manufacturer's website.

---

### Post by jfinkels on 2007-05-06
> **neodarksaver said:**
> Well... I am a newbie also. 

NDISWrapper is here,
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Depending what ur wireless card is, you should be able to find the driver on the manufacturer's website.

The problem with this method is that we don't know for certain that the Linux guru friend used ndiswrapper :D. 

Plus, it might be pointless to make him scour the internet for a driver when unnecessary.

My recommendation is to go ahead with the upgrade if you want, as long as you can make it back here to the forums from a computer with internet access (can you plug in your laptop to a wired ethernet connection?) to ask for help  if necessary.

---

### Post by mdvigi7536 on 2007-05-06
Jfinkels:  Yeah, I remember hearing him mention something about "ndiswrapper."  I'm sure you can tell me how to get it if the upgrade screws up :-)

I also have the cd that came with the card, so between the two and your help I'm thinking I will give it a shot.  Just wanted to make sure it's doable before I do it and have to go crawling back to him for help. :-)

I'll start the upgrade now and you better believe I'll be back if it screws up.

Thanks again for the help.

--Mike

---

### Post by jfinkels on 2007-05-06
> **mdvigi7536 said:**
> Jfinkels:  Yeah, I remember hearing him mention something about "ndiswrapper."  I'm sure you can tell me how to get it if the upgrade screws up :-)

I also have the cd that came with the card, so between the two and your help I'm thinking I will give it a shot.  Just wanted to make sure it's doable before I do it and have to go crawling back to him for help. :-)

I'll start the upgrade now and you better believe I'll be back if it screws up.

Thanks again for the help.

--Mike

Okay, great! I'm not much of an expert with ndiswrapper but if you need help definitely come back and make a new thread. Let us know how it goes :D

---

### Post by mdvigi7536 on 2007-05-06
OK.  The update is complete and things appear to be functioning well.  I'm writing this while connected to the wireless internet in my apartment--if you can read this, it must still be working.

May I ask one other, unrelated question though?  I'll promise I'll leave you all alone soon--I have to be up early anyway.

They [the computer gurus] told me to get this Automatix program.  I tried it the first time I installed Linux on this laptop [over the weekend] and it had lots and lots of cool things in it.  Now I went and got it and it has hardly anything in it...like two or three things in each category whereas before it would have like 10.  For example, there was a Java thing in there before...now it's not there and my college's website requires it for some student stuff.  Oh, apparently my computer doesn't play MP3's either.

What have I done *now*? :-)

---

### Post by neodarksaver on 2007-05-06
automatix has a lot of things the default program manager does not have, and the default one has some more other programs. and automatix will only show u GNOME programs unless u click the show KDE button.
go to [www.ubuntuguide.org](www.ubuntuguide.org) to find out how to install java and pretty much everything else.

---

### Post by jfinkels on 2007-05-06
> **mdvigi7536 said:**
> OK.  The update is complete and things appear to be functioning well.  I'm writing this while connected to the wireless internet in my apartment--if you can read this, it must still be working.

May I ask one other, unrelated question though?  I'll promise I'll leave you all alone soon--I have to be up early anyway.

They [the computer gurus] told me to get this Automatix program.  I tried it the first time I installed Linux on this laptop [over the weekend] and it had lots and lots of cool things in it.  Now I went and got it and it has hardly anything in it...like two or three things in each category whereas before it would have like 10.  For example, there was a Java thing in there before...now it's not there and my college's website requires it for some student stuff.  Oh, apparently my computer doesn't play MP3's either.

What have I done *now*? :-)

I don't really know much about Automatix because I've never really used it to install anything. But if you want to install the Java packages, type the following in the terminal:
```

sudo aptitude install sun-java6-bin sun-java6-jre

```
While those packages are being installed, you may get a goofy blue screen with Sun's license agreement. Go through it and choose "Yes" or "Accept" or whatever it says by moving left or right with the arrow keys if necessary and pressing space bar to press the button.

As for mp3 support, you may need the gstreamer0.10-plugins. I'm not sure which one of them has mp3 support, but go ahead and install them all anyway:
```

sudo aptitude install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```

If that doesn't work, you might need a 'lame' library, I'm not too sure about this either, though. See if the gstreamer plugins work.

---

### Post by mdvigi7536 on 2007-05-06
OK, I updated my system and restated it.  Things were good until an hour ago, when the wireless stopped working all of a sudden.

I have the CD for the wireless card, but I don't know what to do.  This is seriously my first weekend with Linux.  Please help!

Edit:  Nevermind, I think I fixed it!

---

