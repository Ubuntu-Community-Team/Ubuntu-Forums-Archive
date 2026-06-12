---
title: "Automatix update notification"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-03-15
Just received an update notification that there is an update available from Automatix. Update Manager has a note saying that the update "can't be verified". Should this update be applied considering the hack problems on their web site? Just curious (and paranoid). Thanks for any info on this.

---

### Post by Zzl1xndd on 2007-03-15
I got the same thing although I did the update. Have noticed any issues anyone else got any info.

---

### Post by xyz on 2007-03-15
No problem! I think it's just because Automatix has its own repos.

---

### Post by jamere on 2007-03-15
FWIW, I went to their web site and the following was on their support forum (no replies as yet):

> Hi,

My automatic updater is giving the following message: "You are about to install software that can't be authenticated!" When I hit 'Show Details' I see:

automatix2 (version 1.1-2.16-6.10edgy_i386) will be upgraded to version 1.1-2.25-6.10edgy_i386

Suggestions?

---

### Post by jackrobinson on 2007-03-15
> **jamere said:**
> FWIW, I went to their web site and the following was on their support forum (no replies as yet):

give us a link to that post.

---

### Post by Sunflower1970 on 2007-03-15
I get that all the time when Automatix is being updated. I go ahead and allow it to go through. Haven't had a problem yet....

---

### Post by jamere on 2007-03-15
still no reply  (as of 10:40 am) to problem posted on Automatix support forum. Here's link:

[http://www.getautomatix.com/forum/index.php?showtopic=848](http://www.getautomatix.com/forum/index.php?showtopic=848)

jim m

---

### Post by jackrobinson on 2007-03-15
> **jamere said:**
> still no reply  (as of 10:40 am) to problem posted on Automatix support forum. Here's link:

[http://www.getautomatix.com/forum/index.php?showtopic=848](http://www.getautomatix.com/forum/index.php?showtopic=848)

jim m
This is really queer... The link takes me to a dead end and even when I search the post on their forum I dont get any. OK I probably "think" I know whats going on. The Automatix team were saying they are moving to a new host.....
can you please paste the ip address from the following:
```
ping getautomatix.com
```

---

### Post by Sunflower1970 on 2007-03-15
..The link's working for me, and I see their forum when I click out of that post...

---

### Post by jackrobinson on 2007-03-15
> **Sunflower1970 said:**
> ..The link's working for me, and I see their forum when I click out of that post...
Great! Could you please paste the ip address from the ping report?
Thanks.

---

### Post by dimbulb1024 on 2007-03-15
ping address was 208.113.170.63 but putting that into the address bar shows "Site Temporarily Unavailable"

The forum is up and working and this link was working for me:
[http://www.getautomatix.com/forum/index.php?showtopic=848](http://www.getautomatix.com/forum/index.php?showtopic=848)

---

### Post by jackrobinson on 2007-03-15
> **dimbulb1024 said:**
> ping address was 208.113.170.63 but putting that into the address bar shows "Site Temporarily Unavailable"

The forum is up and working and this link was working for me:
[http://www.getautomatix.com/forum/index.php?showtopic=848](http://www.getautomatix.com/forum/index.php?showtopic=848)

yeah so they indeed are moving (DNS cache updates take time, so while some of you will be able to access the forum on the new host, other will be directed to the old host for a while). The forum transfer seems seamless. The wiki might take a couple of days.. lets see.
Is the home page showing up?

---

### Post by jackrobinson on 2007-03-15
ok, here is the new GPG key import instructions for automatix2:
```
wget http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -
```
Hope this helps.
-Jack

---

### Post by banditti on 2007-03-15
Anyone done the update and had problems?

---

### Post by silkstone on 2007-03-15
No problems, except that I've just run Update Manager and got an error message...

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3

---

### Post by jamere on 2007-03-15
the update ran ok for me, but I still get a popup that says (paraphrasing): Synaptic is running...please close and restart Automatix...dunno.:confused:

---

### Post by banditti on 2007-03-15
Thanks Jack.


Worked for me!

---

### Post by jackrobinson on 2007-03-15
> **jamere said:**
> the update ran ok for me, but I still get a popup that says (paraphrasing): Synaptic is running...please close and restart Automatix...dunno.:confused:

try doing the following:
```
sudo apt-get --purge remove automatix2
sudo apt-get update
sudo apt-get install automatix2
```
and see if you still get the error.

---

### Post by useResa on 2007-03-15
> **jamere said:**
> still no reply  (as of 10:40 am) to problem posted on Automatix support forum. Here's link:

[http://www.getautomatix.com/forum/index.php?showtopic=848](http://www.getautomatix.com/forum/index.php?showtopic=848)

jim m
I have posted the solution in the indicated thread
Which is exactly the same as posted by jackrobinson in reply [#13](http://www.ubuntuforums.org/showpost.php?p=2303304&postcount=13)

---

### Post by silkstone on 2007-03-15
Thanks everyone. That's cured it.

---

### Post by digitalis on 2007-03-16
> **jackrobinson said:**
> try doing the following:
```
sudo apt-get --purge remove automatix2
sudo apt-get update
sudo apt-get install automatix2
```
and see if you still get the error.

This one worked for me too.
Many thanks.

S.

---

### Post by wiseNoob on 2007-03-17
Thanks! #13 worked for me too... :)

---

