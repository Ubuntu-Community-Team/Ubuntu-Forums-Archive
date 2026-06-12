---
title: "Do I need to update"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-06-14
I currently have Ubuntu Linux 5.04: The Hoary Hedgehog release.  Is it necessary that I update??

---

### Post by shae on 2007-06-14
It is highly suggest that you update to a new version.  Either 6.06 or 7.04 would be the best selections.  Because you are needing more than two dist-upgrades, I  recommend downloading one of those versions and starting fresh.

---

### Post by sachill on 2007-06-14
can u tell me how without compromising the stuff I have on my system already?

---

### Post by shae on 2007-06-14
You will have to start over.  There have been way too many changes in my opinion.  You should back up your files and start new.  Using the upgrade route has a high odds of making your system an unbootable mess.

---

### Post by sachill on 2007-06-14
updatable root?

---

### Post by agurk on 2007-06-14
I agree it would be advisable to upgrade to at least Ubuntu 6.06 Dapper Drake, as Hoary Hedgehog is no longer supported, meaning, there will be no more security fixes released.

Sorry, I don't understand what you mean by 'updatable root?', please elaborate.

---

### Post by sachill on 2007-06-14
updatable root?

---

### Post by sachill on 2007-06-14
sorry, my bad...the 'update root'

---

### Post by Crafty Kisses on 2007-06-14
> **sachill said:**
> I currently have Ubuntu Linux 5.04: The Hoary Hedgehog release.  Is it necessary that I update??

Yes you really should. :p

---

### Post by sachill on 2007-06-14
is the only way to update by replacing my current installation?  ie. can't I simply download something which will update it for me?

---

### Post by agurk on 2007-06-14
Ah, the update route? That would be:

1. Upgrade from Hoary (5.04) to Breezy (5.10)
2. Upgrade from Breezy to Dapper (6.06)

Here is a good guide how to upgrade, though it has a spelling error (it should be /etc/apt/source**s**.list):
[http://www.extremetech.com/article2/0,1697,2132617,00.asp](http://www.extremetech.com/article2/0,1697,2132617,00.asp)

In short, you:
1. Make sure you have all the updates installed for your current version.
2. Edit /etc/apt/sources.list and perform the upgrade to the next version.
3. Rinse and repeat.

Remember to make backups of any valuable data before you start.

---

### Post by kittyhawk63 on 2007-06-14
Dapper is a long term supported (LTS) version . I would stay with it if you want a stable release. However, Feisty Fawn is really stable and has some nice features.

[SIZE=6]BACK UP...BACK UP...BACK UP  [SIZE=2](and don't turn around or make any u-turns)[/SIZE]

[SIZE=2]Need we say more? Oh yes, back up. ;)
kh
[/SIZE][/SIZE]

---

### Post by Old Pink on 2007-06-14
I know it's not advisable. But what happens if you just replace your Hoary sources.list with the Feisty one and upgrade four shots in one? 

Or even if you just went to Dapper, and did two in one? 

I couldn't see anything going wrong, to be honest. :)

---

### Post by agurk on 2007-06-14
Yeah, and did we mention that you should backup your stuff? :p

Another good idea would probably be to download and burn a Feisty Fawn 'desktop' CD before you start, just in case the upgrades go south on you. I'd even go so far as to recommend downloading and burning the 'alternate' CD as well (I never leave home without it ;)).
You'll find both here: [http://releases.ubuntu.com/7.04](http://releases.ubuntu.com/7.04)


(I have to catch some shut-eye, I'll check this thread back tomorrow, good luck!)

---

### Post by wallyts on 2007-06-14
Hi, Sorry this is off subject, but I can't seem to post a new thread.

Can anyone tell me if there are any Ubuntu users in the lower 2/3 part of Palm Beach County, Florida. I would really like to see it in operation.

If you are such a person please contact me at [email]wallyts@iname.com[/email].

Thanks.

---

### Post by kittyhawk63 on 2007-06-14
> **wallyts said:**
> Hi, Sorry this is off subject, but I can't seem to post a new thread.

Can anyone tell me if there are any Ubuntu users in the lower 2/3 part of Palm Beach County, Florida. I would really like to see it in operation.

If you are such a person please contact me at [EMAIL="wallyts@iname.com"]wallyts@iname.com[/EMAIL].

Thanks.

Go to the first page of Absolute Beginner Talk and look toward the top of the page on the left side. You will see a button that says "Make New Post" in black letters with an orange background. Click on it and have fun. Private message me if you need more help on understanding the steps to take. 
kh

---

### Post by jdackle on 2007-06-15
> **Old Pink said:**
> I know it's not advisable. But what happens if you just replace your Hoary sources.list with the Feisty one and upgrade four shots in one? 

Or even if you just went to Dapper, and did two in one? 

I couldn't see anything going wrong, to be honest. :)

Well... I dunno... Upgrade from one version to the immediate following one is somewhat _planned_ by the amintainers of the distro... There are dependencies changes, software splçits and/or unions in different packages, meta-packages to ease the upgrade... Leaping over one or more versions may cause inconsistencies in the planned upgrade process(es)...

I would advise against it.

---

### Post by diatribe on 2007-06-15
from what I've heard the breezy servers were not available so he would prbably have to start anew, just back up your files and do what you have to

---

