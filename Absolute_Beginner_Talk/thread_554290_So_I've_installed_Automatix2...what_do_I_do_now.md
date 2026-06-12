---
title: "So I've installed Automatix2...what do I do now?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-09-18
I recently just read this:

[Automatix=evil (basically)]("http://mjg59.livejournal.com/77440.html")

So what should I do now? I've had it installed for a long time, but I haven't seen any difference...Is Automatix really as bad as this article claims it to be? I used it to install the codecs to stream video. I haven't touched it ever since. I was looking at the changes automatix makes (according to the article)....and I can't make heads or tails of what is bad and what isn't.

Should I reinstall Fiesty (*sigh* :( )

Could someone clear this up for me?

---

### Post by matthew.lns1 on 2007-09-18
I don't think you should reinstall until you see symptoms of a problem.

---

### Post by alienexplorers on 2007-09-18
You should be able to delete Automatix with synaptic, but the changes it made to your source.lst will remain.

---

### Post by isaacj87 on 2007-09-18
> **alienexplorers said:**
> You should be able to delete Automatix with synaptic, but the changes it made to your source.lst will remain.

I've already removed automatix's package...and it's easy to remove the lines in the sources list. I'm double checking my system to see if any of the changes listed in the article happened on my comp as well.

---

### Post by r4ik on 2007-09-18
> **isaacj87 said:**
> I recently just read this:

[Automatix=evil (basically)]("http://mjg59.livejournal.com/77440.html")

So what should I do now? I've had it installed for a long time, but I haven't seen any difference...Is Automatix really as bad as this article claims it to be? I used it to install the codecs to stream video. I haven't touched it ever since. I was looking at the changes automatix makes (according to the article)....and I can't make heads or tails of what is bad and what isn't.

Should I reinstall Fiesty (*sigh* :( )

Could someone clear this up for me?

Seems to be working for you don't try to fix what is not broken.
If you have or want to go by this guide,

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Good luck !

---

### Post by rsambuca on 2007-09-18
If all you did was use it to install codecs you should be fine.  Make backups of any sensitive data before upgrading to gutsy next month, though.

---

### Post by isaacj87 on 2007-09-18
> **rsambuca said:**
> If all you did was use it to install codecs you should be fine.  Make backups of any sensitive data before upgrading to gutsy next month, though.

I installed:

Java
Mplayer and FF plugin
DVD, Audio codecs

---

### Post by w4ett on 2007-09-18
> **isaacj87 said:**
> I installed:

Java
Mplayer and FF plugin
DVD, Audio codecs

If that's all you installed you should be ok.....to remove automatix:

```
sudo apt-get remove automatix2
```

---

### Post by isaacj87 on 2007-09-18
Done. Removed it.

I'm keeping the packages it installed though.

---

### Post by asmoore82 on 2007-09-18
I think you'll be fine... but if major upgrades like Gutsy fail in the future, don't be shocked.

the real problem with Automatix seems to be the attitude of the "developers."

instead of fixing their BROKEN code ('kill -9' in an automated scrips is a BIG NO!NO!),
they would rather prove in quite a juvenile fashion that they don't even believe
in Linux technologies in the first place by making wild accusations that no
Ubuntu system is capable of a clean upgrade.

[-XKids.

look what systems without Automatix can do: [http://ubuntuforums.org/showpost.php?p=3386265&postcount=9](http://ubuntuforums.org/showpost.php?p=3386265&postcount=9)

---

### Post by isaacj87 on 2007-09-19
> **asmoore82 said:**
> I think you'll be fine... but if major upgrades like Gutsy fail in the future, don't be shocked.

the real problem with Automatix seems to be the attitude of the "developers."

instead of fixing their BROKEN code ('kill -9' in an automated scrips is a BIG NO!NO!),
they would rather prove in quite a juvenile fashion that they don't even believe
in Linux technologies in the first place by making wild accusations that no
Ubuntu system is capable of a clean upgrade.

[-XKids.

look what systems without Automatix can do: [http://ubuntuforums.org/showpost.php?p=3386265&postcount=9](http://ubuntuforums.org/showpost.php?p=3386265&postcount=9)

Wow, that's ridiculous...is there a better way to get the same codecs and plugins not using automatix?

---

### Post by asmoore82 on 2007-09-19
there is a sticky at the top of this "Absolute Beginner Talk" board.

---

### Post by Sef on 2007-09-19
> is there a better way to get the same codecs and plugins not using automatix?

With Feisty it is easy to install almost everything needed.

---

