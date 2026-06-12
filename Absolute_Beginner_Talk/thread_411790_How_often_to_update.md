---
title: "How often to update"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by check on 2007-04-17
This is obviously an opinion, but an opinion from someone with a little more knowledge would be helpful.

How often should you update your ubuntu server? Will updating break any current configurations? and what is the procedure for updating?

Thanks in advance!

---

### Post by palmerthegeek on 2007-04-17
Check,

It's a little difficult to answer your questions.  When you mean update, are you talking running "aptget install update"?  Or are you talking using the Symantic Update manager?   

More details please.

---

### Post by bwhite82 on 2007-04-17
You should update as often as the updates are released. More importantly though, you should get into a regular backup routine and definitely do so before any updating.

EDIT: For a server without a desktop environment, you could create a cron task to automatically download and install updates for you. Come to think of it, you can backup your system this way too. Cron tabs are great.

---

### Post by check on 2007-04-17
> It's a little difficult to answer your questions. When you mean update, are you talking running "aptget install update"? Or are you talking using the Symantic Update manager?

I guess i was talking about aptget. I remember there were 2 commands for this, do you know what they are. Ive never heard of symanteic update, can you explain that a little bit.


As far as the crons are concerned. I havent had time to reaseach this but i know its similar to scheduled tasks. So if all this is automated then i guess i have to go back to the question, will updating break current configuraations with things like php, mysql, apache. Obviously you cannot predict whether future releases will break something since you arent the developers of those programs, but is it common for updates on linux systems to ruin setups or are they typically seemlessly implemented.

---

### Post by jvc26 on 2007-04-17
I would advise installing all updates as and when they are available symanteic update sounds like a symatec antivirus lol, perhaps it was referring to the Update Manager which is accessible via
System -> Administration -> Update Manager
Otherwise its simply either:
```

sudo apt-get update
sudo apt-get upgrade

```

EDIT:: Apologies, it was misguided to add on the dist-upgrade option as it can cause problems.

Ive only every had one thing broken via an update and that was one which affected quite a lot of people and got fixed. On the other hand, upgrading from a whole release to another (dapper to edgy for example) I had a much more mixed bag with some working and some breaking badly - since then always opt for just a simple vanilla reinstall to upgrade between releases, but within a release I havent had many problems at all, and so just install all the updates as and when they come.

Il

---

### Post by hyper_ch on 2007-04-17
I wouldn't auto-do dist-upgrades and as long as you have used only software from the repositories then you should be fine to auto-upgrade...

---

### Post by check on 2007-04-17
I dont really watch for when updates are released...are they on a schedule like m$ does thier patches. Or should i check once a month?...

---

### Post by jfinkels on 2007-04-17
> **check said:**
> I dont really watch for when updates are released...are they on a schedule like m$ does thier patches. Or should i check once a month?...

Many updates come MUCH more often than once a month! That's one of the great things about the aptitude/apt-get system. You might want to have a cron-tab run apt-get update && apt-get upgrade once every couple of days (i guess?).

---

