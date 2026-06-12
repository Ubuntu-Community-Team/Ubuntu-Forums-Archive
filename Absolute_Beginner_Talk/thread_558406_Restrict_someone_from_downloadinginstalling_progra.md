---
title: "Restrict someone from downloading/installing programs?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Djbb on 2007-09-23
Hello, I'm a bit new to Ubuntu having used Freespire in the past. I occasionally let my younger brother use the computer, but whenever I get back on I notice that hes downloaded tons of hentai/anime crap. More recently hes starting to learn his way around Ubuntu and has been using WINE and the Add/Remove Programs to install software I honestly don't want on this computer. I know how to set up a seperate user account for him, but how would I go about restricting his access to things I don't want him doing? You'll be saving a 13 year old boys life if you tell me because I'm going to dropkick him out the window next time he does it.

---

### Post by overdrank on 2007-09-23
> **Djbb said:**
> Hello, I'm a bit new to Ubuntu having used Freespire in the past. I occasionally let my younger brother use the computer, but whenever I get back on I notice that hes downloaded tons of hentai/anime crap. More recently hes starting to learn his way around Ubuntu and has been using WINE and the Add/Remove Programs to install software I honestly don't want on this computer. I know how to set up a seperate user account for him, but how would I go about restricting his access to things I don't want him doing? You'll be saving a 13 year old boys life if you tell me because I'm going to dropkick him out the window next time he does it.

Hi the first thing comes to mind is don't tell him the password! :)
Ok a bad joke but maybe this link will help
[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)

---

### Post by Djbb on 2007-09-23
> **overdrank said:**
> Hi the first thing comes to mind is don't tell him the password! :)

I would do that, but hes a tad bit of a problematic child and letting him on for a bit keeps him calm.

---

### Post by Hospadar on 2007-09-23
Basically you will want to create a new user (in System->administration i believe) and then you'll want to go to Users & Groups and remove him from the "admin" group this will make it so he can't use sudo (any time you type in your password you are using a sudo command) so he won't be able to install anything or monkey with any system files or anything outside of his own account.

---

### Post by yuku-aki on 2007-09-23
To make it a little more simple, the part about permissions, "Under the &#8220;User privileges&#8221; tab, note the default access given to this basic user. You may prefer to change some of these, such as &#8220;Monitor system logs&#8221;, &#8220;and Connect to Internet&#8221;. Anything that is checked is allowed by this user. Also make sure that the &#8220;Executing system administration tasks&#8221; is NOT checked." is the MOST important of all.  That alone decides what the user can(not) do, and keeps those kids who catch on quickly from ruining a system with a bad administrative decision.

I should know - I was one of those kids.  ;)

posting to the link again to validate my usage of its text - [Users In Ubuntu]("http://www.freesoftwaremagazine.com/articles/users_in_ubuntu")

---

### Post by Djbb on 2007-09-23
Alright, I've got his own account set up with no administrative privileges like you guys said, but how would I go about allowing him to share some of my files? Like Frostwire for instance, I don't mind if he downloads music, its more the installing programs I don't want him doing.

---

### Post by Adramelech on 2007-09-23
New account for him, and strict quotas for music:

[http://www.linux.com/feature/118885?theme=print]("linux.com")

---

### Post by Djbb on 2007-09-23
Thanks for the quick responses everyone, hopefully now I won't see "HotHentaiGirls.Exe" in my home folder next time I get on. :roll:

---

### Post by overdrank on 2007-09-23
> **Djbb said:**
> Thanks for the quick responses everyone, hopefully now I won't see "HotHentaiGirls.Exe" in my home folder next time I get on. :roll:

LMAO :lolflag:

---

### Post by yuku-aki on 2007-09-30
A new Firefox plugin I just found should help, too.

[https://addons.mozilla.org/en-US/firefox/addon/3911](https://addons.mozilla.org/en-US/firefox/addon/3911)

It's called Public Fox, and it makes your net browser act like a public internet terminal, where you can't browse certain sites/types of sites, and no downloading privileges.

---

### Post by Gwasanaethau on 2007-09-30
> **Djbb said:**
> Thanks for the quick responses everyone, hopefully now I won't see "HotHentaiGirls.Exe" in my home folder next time I get on. :roll:

Oh dear! I bet you're glad it's not a Windows terminal too - I'm 99.9999% certain that running that under Windows would cause untold amounts of chaos! :lolflag:

I sympathise over the whole brother thing too - many a time I've wanted to dropkick mine out the window too! :-\"

---

