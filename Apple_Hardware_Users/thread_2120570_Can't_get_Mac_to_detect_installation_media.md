---
title: "Can't get Mac to detect installation media"
date: 2013-02-26
forum: Apple Hardware Users
---

### Post by nedak on 2013-02-26
Note: I am following these instructions: Dual Boot OS Ubuntu -OMG Ubuntu.

So, for the past few days I've been trying to install Ubuntu on my Mac OSX because I would really like that extra option of using Ubuntu instead of Apple's OS. Easy enough, right? Well, I first tried installing via a usb but that didn't work (it kept saying my USB was unreadable) so I decided I would use one of my blank DVD-RWs. I downloaded the Ubuntu file and inserted my blank DVD-RW and it just kept spinning until it was ejected by my Mac. It's not the hardware because it is accepting video DVDs, it just plain won't accept it.

I decided burning the .iso file from my PC would work, after burning it on my PC I inserted it into my Mac, but my Mac still couldn't read the DVD. What am I doing wrong? My Mac's processor is x64.

---

### Post by MAFoElffen on 2013-02-26
Welcome to the Ubuntu Forums.

Have you burned a DVD RW disk (means that disk is "rewritable") on that Mac before? Or is it just writable to DVD +R? Some DVD drives cannot rewrite, so will not recognize that kind of disk format.

What model Mac?

---

### Post by nedak on 2013-02-26
> **MAFoElffen said:**
> Welcome to the Ubuntu Forums.

Have you burned a DVD RW disk (means that disk is "rewritable") on that Mac before? Or is it just writable to DVD +R? Some DVD drives cannot rewrite, so will not recognize that kind of disk format.

What model Mac?

Nope, I haven't. I got fed up with it so I decided I would just burn the image on the DVD on my Windows PC. Right now the Ubuntu .iso is burned onto the rewritable disk. I originally tried it on the Mac, but it wouldn't even recognize the disk. 

I'm using a MacBook Pro, this is a link to the Mac:
[http://gdgt.com/apple/macbook-pro/15-inch/](http://gdgt.com/apple/macbook-pro/15-inch/)

Even if I can't burn with the Mac, it should still be able to read the DVD, shouldn't it?

---

### Post by MAFoElffen on 2013-02-26
> **nedak said:**
> Nope, I haven't. I got fed up with it so I decided I would just burn the image on the DVD on my Windows PC. Right now the Ubuntu .iso is burned onto the rewritable disk. I originally tried it on the Mac, but it wouldn't even recognize the disk. 

I'm using a MacBook Pro, this is a link to the Mac:
[http://gdgt.com/apple/macbook-pro/15-inch/](http://gdgt.com/apple/macbook-pro/15-inch/)

[COLOR="Blue"]Even if I can't burn with the Mac, it should still be able to read the DVD, shouldn't it?[/COLOR]

[COLOR="blue"]No.[/COLOR] It just looked up the spec's on it: DVD+R.

It can read/write DVD+R and less disks (dvd+r, cd+r, cd-r, cd-rw). [COLOR="blue"]On DVD-RW it didn't recognize it as a supported format so it spit it out[/COLOR]. 

Where as your PC probably has a newer or better drive, but if you put a Blueray disk in it, it probably wouldn't recognize it.

---

### Post by nedak on 2013-02-26
> **MAFoElffen said:**
> [COLOR="blue"]No.[/COLOR] It just looked up the spec's on it: DVD+R.

It can read/write DVD+R and less disks (dvd+r, cd+r, cd-r, cd-rw). [COLOR="blue"]On DVD-RW it didn't recognize it as a supported format so it spit it out[/COLOR]. 

Where as your PC probably has a newer or better drive, but if you put a Blueray disk in it, it probably wouldn't recognize it.
Ah, okay. That makes sense then. It didn't read the CD-R80 that I used to test to see if the hardware was working, either. But it did read the DVD of a TV show, so I don't know.

If I get a blank DVD-R it should work then?

EDIT: I just stuck a blank DVD+R into my Mac and it ejected it again. On my Windows PC it showed it as a blank DVD+R.

---

### Post by MAFoElffen on 2013-02-26
Yes it will. And you'll be pleasantly surprized that they are dirt cheap compared to DVD-RW disks.

And with DVD-RW disks... I quit buying them. I still have about 90 left from a 100 stack that I bought 2 years ago.

For what I do, DVD+R disk are cheaper and if I need re-write storage, usb thumbdrives are handier, more portable and durable.

---

### Post by nedak on 2013-02-26
> **MAFoElffen said:**
> Yes it will. And you'll be pleasantly surprized that they are dirt cheap compared to DVD-RW disks.

And with DVD-RW disks... I quit buying them. I still have about 90 left from a 100 stack that I bought 2 years ago.

For what I do, DVD+R disk are cheaper and if I need re-write storage, usb thumbdrives are handier, more portable and durable.

Cool. I found a case of DVDs that were just white on the top (didn't say whether they were DVD+Rs or not) and I put them in my PC and my PC says they are DVD+Rs. However when I put them in the Mac, it does the same thing where it spits them back out.

EDIT: Actually it says it's a DVD-R and not a DVD+R, does that make any difference?

---

### Post by MAFoElffen on 2013-02-27
Actually, there is a few differences, but a DVD+r drive should be able to read and write to a dvd-r disk... But there where actually 2 different formats of that same disk (sections 4.3.1 & 4.3.2:
[http://www.dvddemystified.com/dvdfaq.html#4.3.1](http://www.dvddemystified.com/dvdfaq.html#4.3.1)

But your MAC "might" read that type disk. The only reason I'm thinking that, is that Apple was one of the companies pushing to get that format accepted as a standard. But then again, if it doesn't, like I said, the spec's for that MacBook says DVD+R.

I really can't confirm that for your MacBook as you can see from the "usually" in that chart, I don't have any DVD-R disks... and I don't have a MacBook here.

---

### Post by nedak on 2013-02-27
> **MAFoElffen said:**
> Actually, there is a few differences, but a DVD+r drive should be able to read and write to a dvd-r disk... But there where actually 2 different formats of that same disk (sections 4.3.1 & 4.3.2:
[http://www.dvddemystified.com/dvdfaq.html#4.3.1](http://www.dvddemystified.com/dvdfaq.html#4.3.1)

But your MAC "might" read that type disk. The only reason I'm thinking that, is that Apple was one of the companies pushing to get that format accepted as a standard. But then again, if it doesn't, like I said, the spec's for that MacBook says DVD+R.

I really can't confirm that for your MacBook as you can see from the "usually" in that chart, I don't have any DVD-R disks... and I don't have a MacBook here.
Alright, I guess I'll just burn that DVD and see if that works-- if not I'll be picking up some DVD+Rs in the morning. 

Thanks a lot for the help and for answering my amateur questions! :P

---

### Post by nedak on 2013-02-27
Sorry to re-open this can of worms, but I decided I would check my Mac's system information and in the system information it does say that it supports -R, -R DL, +R, +R DL, and +RW. So in theory both my +RW and -R DVDs should be working, according to this information.

Could there be any other reason as to why it will refuse to my blank DVDs? Mind you-- it's only when they're blank. Movie DVDs work just fine.

---

### Post by MAFoElffen on 2013-02-27
Just guessing, because this now seems odd.. It saying that, It should have then read the prepared RW from yourPC. Burnt on slowest speed? Does it read a -R if burned on your PC?

Maybe a dirty lens in the MAC drive?

---

### Post by nedak on 2013-02-27
> **MAFoElffen said:**
> Just guessing, because this now seems odd.. It saying that, It should have then read the prepared RW from yourPC. Burnt on slowest speed? Does it read a -R if burned on your PC?

Maybe a dirty lens in the MAC drive?

Okay, so I got it to read the -R after I burnt the .iso on my PC, however when I try to boot it from said DVD on start up I get "select cd rom boot type". After doing some googling apparently that COULD mean my Mac doesn't want to read any sort of .iso? So now I'm going to see (and probably figure out I can't do this) if I can burn the img file I created on my Mac to a -R by transferring the img file to my PC.

---

### Post by nedak on 2013-02-27
Update! That worked actually, I'm installing right now.

---

### Post by MAFoElffen on 2013-02-27
Great!!! Please mark this as solved.

---

