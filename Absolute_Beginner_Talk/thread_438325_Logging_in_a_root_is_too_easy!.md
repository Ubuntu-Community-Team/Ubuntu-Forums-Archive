---
title: "Logging in a root is too easy!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-05-09
I've been using Ubuntu at home for some time, at least back to Dapper, but I've never had occasion to boot into the recovery mode from Grub before.  When I did, I was horrified to discover that my machine was wide open.   All anyone has to do to break in to a stock Ubuntu system is power it down, bring it back up, hit escape when they are told to, and the next thing they know they are staring at a terminal prompt that says root.

Now, as a newbie, we buy the idea that sudo is a safer way to go in general, and I'll bet not 1 in 1000 people ever think to set a root password.  Good lord, folks.  Now whenever I see anyone running Ubuntu I'm going to say "Bet I can break into your box with full privs in about a minute."  I's a bet I'm more likely to win than not.

I'm glad I've always been in the habit of setting BIOS passwords, but this seems again like something only perhaps 1 in 1000 would do.

Am I wrong, or is this so serious a problem that Ubuntu should pull the product until it's fixed?

---

### Post by Cypher on 2007-05-09
To be able to do what you are suggesting, the offender would need to have physical access to your computer. They cannot do the same thing over the Internet and that's the security.

If someone has come into your house and has physical access to your computer, they could just as easily remove the HD, take it to another machine and extract all the info.

Kinda moot, isn't it??

---

### Post by Lord Illidan on 2007-05-09
> **RTrev said:**
> I've been using Ubuntu at home for some time, at least back to Dapper, but I've never had occasion to boot into the recovery mode from Grub before.  When I did, I was horrified to discover that my machine was wide open.   All anyone has to do to break in to a stock Ubuntu system is power it down, bring it back up, hit escape when they are told to, and the next thing they know they are staring at a terminal prompt that says root.

Now, as a newbie, we buy the idea that sudo is a safer way to go in general, and I'll bet not 1 in 1000 people ever think to set a root password.  Good lord, folks.  Now whenever I see anyone running Ubuntu I'm going to say "Bet I can break into your box with full privs in about a minute."  I's a bet I'm more likely to win than not.

I'm glad I've always been in the habit of setting BIOS passwords, but this seems again like something only perhaps 1 in 1000 would do.

Am I wrong, or is this so serious a problem that Ubuntu should pull the product until it's fixed?

Hell, I could just run a live cd, and extract the data in your /home account and your Windows drive and copy it.
If you are paranoid, encrypt the drive. It wouldn't hurt to include a grub password and a BIOS password, although a BIOS password can easily be overridden.

---

### Post by RTrev on 2007-05-09
> **Cypher said:**
> To be able to do what you are suggesting, the offender would need to have physical access to your computer. They cannot do the same thing over the Internet and that's the security.

If someone has come into your house and has physical access to your computer, they could just as easily remove the HD, take it to another machine and extract all the info.

Kinda moot, isn't it??

It's moot if you live in the perfect environment, with no teenage children around, or if you aren't running in an office environment.  But we all hope to see Feisty running in the office soon.

Why not just set the root password to the password of the first user to log in during install?  They're going to have sudo anyway, so there would seem to be little to lose and a lot to gain.

---

### Post by RTrev on 2007-05-09
> **Lord Illidan said:**
> Hell, I could just run a live cd, and extract the data in your /home account and your Windows drive and copy it.
If you are paranoid, encrypt the drive. It wouldn't hurt to include a grub password and a BIOS password, although a BIOS password can easily be overridden.

Granted that there are a lot of other ways to easily and quickly get into a machine, but why make it any easier than it has to be?  Only someone who knows what they're doing could pull off the CD trick, where anybody could log in via grub.

---

### Post by y-lee on 2007-05-09
if it bothers ya remove that grub entry....problem solved. If somehow has physical access to your machine then it is insecure no matter what ya do. Perhaps encrypting your hd would help but still encryptions can be broke.

---

### Post by RTrev on 2007-05-09
> **y-lee said:**
> if it bothers ya remove that grub entry....problem solved. If somehow has physical access to your machine then it is insecure no matter what ya do. Perhaps encrypting your hd would help but still encryptions can be broke.

Well, I simply set a root password.  But I think of all the people out there who are going to think their box is at least as secure as "that other OS."  


Am I the only one who thinks it's bizzare to give people a menu selection to gain full access to a machine?  At least make them work at it a bit.  ;-)

---

### Post by Cypher on 2007-05-09
> **RTrev said:**
> It's moot if you live in the perfect environment, with no teenage children around, or if you aren't running in an office environment.  But we all hope to see Feisty running in the office soon.

Why not just set the root password to the password of the first user to log in during install?  They're going to have sudo anyway, so there would seem to be little to lose and a lot to gain.
I didn't know teenage children were that destructive. :)

Setting the root password to the first user isn't going to gain you much more security because if you have access to GRUB, then you can just as easily append "single" or "1" to the boot command line to make Ubuntu drop to a shell prompt without much prompting for recovery purposes.

We're not trying to fight you here, just saying that if someone has malicious intents, then there is little that you can do to protect yourself, but majority of people don't have an urge to attack their Ubuntu installation to somehow break it.

At the same time, it's great to be able to get into the system with the least amount of hassle when things break to attempt a recovery.

---

### Post by Cypher on 2007-05-09
> **RTrev said:**
> Well, I simply set a root password.  But I think of all the people out there who are going to think their box is at least as secure as "that other OS."  


Am I the only one who thinks it's bizzare to give people a menu selection to gain full access to a machine?  At least make them work at it a bit.  ;-)
When people claim that Linux is more secure than other OS', they're usually talking about dealing with external infiltrators into your machine. Not local/physical ones. In that regard, no OS is truly secure, because if I could plug in a USB stick with Knoppix, I can get a full-blown Linux running and have access to all your partitions and copy out whatever I need.

So when we say more secure, we mean from threats from the Internet..

---

### Post by RTrev on 2007-05-09
> **Cypher said:**
> I didn't know teenage children were that destructive. :)

Setting the root password to the first user isn't going to gain you much more security because if you have access to GRUB, then you can just as easily append "single" or "1" to the boot command line to make Ubuntu drop to a shell prompt without much prompting for recovery purposes.

We're not trying to fight you here, just saying that if someone has malicious intents, then there is little that you can do to protect yourself, but majority of people don't have an urge to attack their Ubuntu installation to somehow break it.

At the same time, it's great to be able to get into the system with the least amount of hassle when things break to attempt a recovery.

lol.. teenaged children can be okay, but we adopted a couple who are RAD kids.  Look that up and you'll see what we're facing.  We keep a padlock on our bedroom door!

As for appending a "1" to the Grub command line, then we are at least back to where only someone with some knowledge could easily get in.  

I dunno, maybe I'm making more of this than it deserves, but my jaw hit the floor when I saw that "root" prompt...

---

### Post by Bachstelze on 2007-05-09
Just put a password to GRUB then. It is fairly easy to bypass if you have some knowledge but should be enough to stop the kids ;)

---

### Post by Cypher on 2007-05-09
Good luck with the RAD Kids..

The use of "1" or "single" or other recovery tactics are very common responses when anyone asks about how to recovery Linux, so they aren't really as elusive.

I do think you might be making this more than it is..depending on who is using the computer, teaching awareness and do's and donts might be sufficient in most cases..

---

### Post by RTrev on 2007-05-09
> **Cypher said:**
> Good luck with the RAD Kids..

The use of "1" or "single" or other recovery tactics are very common responses when anyone asks about how to recovery Linux, so they aren't really as elusive.

I do think you might be making this more than it is..depending on who is using the computer, teaching awareness and do's and donts might be sufficient in most cases..

Probably.  Let me think about it a bit.  If I were setting up a large office environment, I would have at least some minor worries..

Thanks for all the feedback!!

---

### Post by aysiu on 2007-05-09
[http://psychocats.net/ubuntu/security#recoveryrisk](http://psychocats.net/ubuntu/security#recoveryrisk)

---

### Post by Lord Illidan on 2007-05-09
I'm curious now..is there any way howto remove that grub recovery feature, even by the 1 or single option?

---

### Post by Bachstelze on 2007-05-09
No. But you can password-protect GRUB so the users cannot modify the lines.

---

### Post by aysiu on 2007-05-09
There's quite a lengthy thread about this:
[ Is root in recovery mode a security risk? ](http://ubuntuforums.org/showthread.php?t=372262)

---

### Post by BRAXS69 on 2007-05-09
all this fuss and all you  need to do is set the root password. :popcorn: 

sure point taken that not realizing that recovery mode just logs you into root with no password validation then having full access to the computer may cripple your beliefs that your super secure computer has such a big hole. but sense you cant login as root by default, the password was never set to lock it. kind of silly if you ask me, during the install they should add something to set it. but meh maybe next version...

---

### Post by Bachstelze on 2007-05-09
Ubuntu has never, since the beginning, set a root password and this is very unlikely to change... As was said earlier, if someone has physical access to your machine, he'll be root, whether you set a root password or not.

---

