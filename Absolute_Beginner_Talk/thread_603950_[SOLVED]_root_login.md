---
title: "[SOLVED] root login"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-05
hi,

What do people mean when they say to login as the root user? And how do you do it????

Thnx

---

### Post by rsambuca on 2007-11-05
Root login is disabled by default in Ubuntu.  For details, [see this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by daimaru on 2007-11-05
just in case u don't want to spend an hour reading the stuff on the howto page the guy above me mentioned.

go to system-> admininstration-> Login window  select securities tab and tick the checkbox "allow local system administrator login" .
then log out and login as root with same password as your username.

---

### Post by rsambuca on 2007-11-05
> **daimaru said:**
> just in case u don't want to spend an hour reading the stuff on the howto page the guy above me mentioned.

go to system-> admininstration-> Login window  select securities tab and tick the checkbox "allow local system administrator login" .
then log out and login as root with same password as your username.

The problem with these forums these days is that everyone just wants to be spoonfed info that is already laid out for them. It shouldn't take 5 minutes to read the page, even if English isn't your primary language.

EDIT:  And now you just gave someone enough info to be very dangerous and potentially bork their system!

---

### Post by daimaru on 2007-11-05
um sorry hope i did not offend you . no offense intended.

EDIT: i see what you mean just read the post by biomedtech on dvd's won't play on gutsy and what a BS that is LOL, your right ppl should at least inform themselves a bit b4 posting. or at least google it or search the forums.

---

### Post by rsambuca on 2007-11-05
> **daimaru said:**
> um sorry hope i did not offend you . no offense intended.

EDIT: i see what you mean just read the post by biomedtech on dvd's won't play on gutsy and what a BS that is LOL, your right ppl should at least inform themselves a bit b4 posting. or at least google it or search the forums.

Hey, no sweat, I wasn't offended.  I just think it is better to give people all of the information so that they can make an informed decision themselves - especially when they are considering running as root!

---

### Post by ardchoille42 on 2007-11-05
> **daimaru said:**
> just in case u don't want to spend an hour reading the stuff on the howto page the guy above me mentioned.

go to system-> admininstration-> Login window  select securities tab and tick the checkbox "allow local system administrator login" .
then log out and login as root with same password as your username.

I don't mean to offend you, but that is extremely bad advice.

Consider this scenario:
I want to break into your computer so I can use it to break into government computers or spam millions of other people. That way, when the law gets involved, and they eventually will, they'll show up at your door, not mine, because your computer (which I hacked into) was used to do illegal things. I know you have a root account on your computer so I can just sit here for months brute forcing the root account, and I'll probably succeed because most people don't use secure passwords on their systems. However, if the root account is locked/disabled (which is the default in *buntu's), I can't brute force it. I can't brute force the other user accounts on your computer because I don't have the usernames.

Enabling the root account is dangerous, it's not recommended, and I feel that people should not teach others how to do it because it breaks the security of the system.

In Ubuntu, we use [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by daimaru on 2007-11-05
@ardchoille42
your right. i might have been a bit quick to tell him that but i just thought if someone wants to know, he'll know what the repercussions are. 
oh and by the way getting a persons username isn't as hard as you think. all you have to do is read the posts here and check the CODE blocks where ppl are nice enough to post their terminal output including their username at the prompt :)

but still your point is valid and i apologize for having mentioned it. so mister thread starter do not enable your root account, because this is not SUSE or some other distro.

---

### Post by limac on 2007-11-05
U guys r gooooood. Thnx again for sharing your geniusness...

---

### Post by Maestro23 on 2007-11-05
> **limac said:**
> U guys r gooooood. Thnx again for sharing your geniusness...

Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

