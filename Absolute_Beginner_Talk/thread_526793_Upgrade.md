---
title: "Upgrade"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by jimaveritt on 2007-08-15
**[SIZE=3][FONT=Comic Sans MS]Does anyone know how to upgrade from Ubuntu 7.04 to version 7.10 gutsy gibbon?[/FONT][/SIZE]**

---

### Post by HereInOz on 2007-08-15
Unless you want to be an alpha tester of Gutsy Gibbon, perhaps wait until the release in October, however, if you want to live on the edge:

If you are using Feisty, you can upgrade to Gutsy Gibbon using these commands.

sudo apt-get update
sudo apt-get upgrade
gksudo "update-manager -d"
(copy and paste courtesy of [www.go2linux.org](www.go2linux.org))

---

### Post by Hobo Joe on 2007-08-15
```

sudo apt-get update
sudo apt-get upgrade
gksudo "update-manager -d"

```
Also, no need for such a big font!

---

### Post by HereInOz on 2007-08-15
Actually, when you think about it, the correct answer to the question, large font or not, is a simple "Yes"

Just being pedantic!

---

### Post by Koti on 2007-08-27
I tried this and I keep getting this:

"warning: could not initiate dbus"
"current dist not found in meta-release file"

I'm not sure how to check my version of Update Manager so I do not know if that's the issue.

It may also be that I installed this version of Fiesty via Wubi. 

So my questions are: 
1. How do I check my version of Update Manager?
2. Can I do this upgrade with an installation via Wubi?

Thanks!

---

### Post by Koti on 2007-08-28
Bump...

Any help would be appreciated on these questions.

Thanks!

---

### Post by abhiroopb on 2007-08-28
I was actually wondering what the issues with upgrading will be. I don't plan on doing it now, but come October what will I have to change on my current feisty install? Because if its a lot of effort I doubt I'll be doing it as I'll have work/exmas at the time.

---

### Post by SunnyRabbiera on 2007-08-28
i would personally suggest waiting...
latest doesnt always mean greatest

---

### Post by ramjet_1953 on 2007-08-28
I can only echo what has been said before.

Gutsy still has quite a few bugs and unless you are fully competent with the command line to work-around some of these problems, I suggest that you stay with Feisty.

Regards,
Roger :cool:

---

