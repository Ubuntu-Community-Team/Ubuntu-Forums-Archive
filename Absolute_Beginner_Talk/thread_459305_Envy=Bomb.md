---
title: "Envy=Bomb"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pappapump on 2007-05-30
I see that my previous post is getting no response now.
Envy killed my Ubuntu so now I'm back in Win2k.
WTH was that all about?
Now It looks like I have to start all over again.

---

### Post by pappapump on 2007-05-30
So what now?
You just gonna leave me hanging here?
No replies at all to either of my posts?
Is there no way to save my install of Ubuntu since Envy trashed me?
I mean you post a fix for my nvidia driver and it crashes and all of a sudden nobody wants to help me?

---

### Post by pappapump on 2007-05-30
Do you even care that I have to start all over?
This is completely wrecking my peace of mind here.
Your FIX killed my Ubuntu and now you won't even reply to my thread?
At least tell me how to undo it.

---

### Post by Nekiruhs on 2007-05-30
What happens on boot?
__
BTW: I understand you come from the Windows world where you pay for service, but Ubuntu is an open+free software, we gain nothing from you using Ubuntu, we lose nothing from it not working, please don't demand help, it just doesn't work when you take money out of the picture.

---

### Post by aks44 on 2007-05-30
I don't mean to be rude, but what about restoring your xorg.conf from the backup you, as a responsible user, oughta have made before tinkering with your video drivers?

---

### Post by raeb on 2007-05-30
Give us some details about what went on, what steps did you go through, are there error messages?

---

### Post by alan34 on 2007-05-30
sudo dpkg-reconfigure -phigh xserver-xorg

sudo shutdown -r now

good luck

---

### Post by psyke83 on 2007-05-30
In a terminal:

```
sudo nano /etc/X11/xorg.conf
```

Find 'Section "Device"'

Change this line:

```
        Driver          "nvidia"

```

To this:


```
        Driver          "nv"

```

Save the file and reboot, then uninstall the nvidia driver using Envy.

Also, consider an attitude re-adjustment. This forum is visited by volunteers and fellow users, they owe you nothing.

---

### Post by aidanr on 2007-05-30
of course there's a way to fix it, a bit of patience would help and more info

boot up into recovery mode (hit escape when grub is loading), type in sudo nano /etc/X11/xorg.conf, scroll down to section device and change Option driver from nvidia to nv, save and exit, and type sudo reboot

edit:// there you go, 3 posts at the same time

---

### Post by pappapump on 2007-05-30
Ok thats another thing that gives me trouble.
I can't seem to make any of the backup programs work.
Yeah I KNOW money isn't part of the equation but if you were me getting help and it looked like GOOd help then all of a sudden nobody responds just imagine how YOU would panic.
PUT Money in the equation and just WATCH how fast I shell out!
Somehow you don't get the fact that a lot of us want Ubuntu to replace windows and people like me with deep pockets are indeed willing to pay to see it happen.
At some point this ( It's free so dont demand topic wil be addressed).
I'm not demanding, I was freaking out that days worth of work would all be lost and nobody was responding.
Though wipe and reinstall works quite well and easily I'd just rather not have to start all over again because I'm Ubuntu ignorant.
If friggin money is the issue here let me suggest that one of you linux gurus make a pay site for those of us who would be delighted to PAY for your timely help.
Make a site for UBUNTU only and post it here along with your rates to help people like me and I'll be there.

---

### Post by Nekiruhs on 2007-05-30
> **pappapump said:**
> Ok thats another thing that gives me trouble.
I can't seem to make any of the backup programs work.
Yeah I KNOW money isn't part of the equation but if you were me getting help and it looked like GOOd help then all of a sudden nobody responds just imagine how YOU would panic.
PUT Money in the equation and just WATCH how fast I shell out!
Somehow you don't get the fact that a lot of us want Ubuntu to replace windows and people like me with deep pockets are indeed willing to pay to see it happen.
At some point this ( It's free so dont demand topic wil be addressed).
I'm not demanding, I was freaking out that days worth of work would all be lost and nobody was responding.
Though wipe and reinstall works quite well and easily I'd just rather not have to start all over again because I'm Ubuntu ignorant.
If friggin money is the issue here let me suggest that one of you linux gurus make a pay site for those of us who would be delighted to PAY for your timely help.
Make a site for UBUNTU only and post it here along with your rates to help people like me and I'll be there.
Canonical (the company that makes Ubuntu) does offer 24/7/365 paid support.

---

### Post by pappapump on 2007-05-30
Thank you nehirus.
Do you happen to know the rates?

---

### Post by NewJack on 2007-05-30
Check my response to your other post here:  [http://ubuntuforums.org/showthread.php?t=459262](http://ubuntuforums.org/showthread.php?t=459262)

That may help you.

Joe

---

### Post by phr0ze on 2007-05-30
Are you just trolling? I think the problem is the way you stated your problem. I don't know anything about Envy. But If you said X won't start, you'd have a fix in minutes. Even with your posts it seems your question was answered quickly. Have you tried any of the suggestions above? You didn't indicate if anything worked when you made your post about money. We don't want to take anyone's money. We just want to help, but it does require your feedback to our diagnostic questions and suggestions.

---

### Post by pappapump on 2007-05-30
Ok got it.

Coverage 	              9 x 5   	                24 x 7
Desktop support 	$250 (USD)* 	$900 (USD)*
Server support 	$750 (USD)* 	$2750 (USD)*
Thin client and cluster support 	$1200 (USD)* 	$4000 (USD)*
Term 	1 year 	1 year
Live phone support 	Included 	Included
Email support 	Included 	Included
Free upgrades 	Included 	Included
Security upgrades 	Included 	Included

*Prices exclude locally applicable sales taxes.

For more information on which package is best for you, or your business contact us. 
Beats the snot out of anything Microshaft ever offered!

---

### Post by pappapump on 2007-05-30
Yes I have a lot of responses even after I went to the black screen.
Now I'm back to Ubuntu AFTER printing out and FOLLOWING the instructions provided by starcraft.
I just freaked out for a sec.
All better now.
Thanx to everyone who helped me out.

---

### Post by nutz on 2007-06-29
Envy hosed my system too so I am going to tinker with it to see if I can bring it back tonight. The first thing I did was restore my xorg.conf from backup but that didn't do the trick because X will still not start. I will keep you guys posted as I fix it to let you know what was involved...

Could you share whatever instructions you got from starcraft with me pappapump? It could shave some time off solving this...

---

