---
title: "thunderbird"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by vurt on 2007-11-25
i've allready tar -zxvf mozilla-thunderbird and it created a new directory named thunderbird.

now I should just be able to enter it and ./configure, make install and voila right?

It's not allowing me to ./configure or install in any way.  any hints or has anyone ever installed thunderbird 2.0.0.9, the latest version?

---

### Post by stchman on 2007-11-25
> **vurt said:**
> i've allready tar -zxvf mozilla-thunderbird and it created a new directory named thunderbird.

now I should just be able to enter it and ./configure, make install and voila right?

It's not allowing me to ./configure or install in any way.  any hints or has anyone ever installed thunderbird 2.0.0.9, the latest version?

The .tar.gz archive you get from Mozilla's website is a pre compiled binary.  No need to make it.

I have a script to install Thunderbird in Ubuntu.  The script even makes a menu entry.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

---

### Post by spiderbatdad on 2007-11-25
if you have the default repos. you should be able to sudo apt-get install thunderbird

---

### Post by erfahren on 2007-11-25
I agree with spiderbatdad. The version in the repos is 2.0.0.8

that's not very old, c'mon! - lol

the other good thing about instaling it out of the repos is that when there's updates for it you automatically get them with the others. That's one of Linux's best attrtibutes in my opinion. No need to sit there and install updates fo programs individually.

---

### Post by vurt on 2007-11-25
spider: I ran the script and it worked perfectly except for the fact that thunderbird is still 2.0.0.9

I tried sudo apt-get upate mozilla...
sudo apt-get install mozilla*

and always it returns me with .6 version.

---

### Post by jrusso2 on 2007-11-25
> **vurt said:**
> spider: I ran the script and it worked perfectly except for the fact that thunderbird is still 2.0.0.9

I tried sudo apt-get upate mozilla...
sudo apt-get install mozilla*

and always it returns me with .6 version.

2.0.0.9 is the newest version of Thunderbird

---

### Post by vurt on 2007-11-25
sorry meant to say im still on .6 not .9

---

### Post by spiderbatdad on 2007-11-25
Apparently Thunderbird 2 (2.0.0.9) still has an number of known issues and is not entirely compatible with mozilla's own extensions and add-ons. Probably why it isn't in the repos yet.

---

### Post by stchman on 2007-11-27
According to ubuntu packages the version in the repos is 2.0.0.8

[http://packages.ubuntu.com/gutsy/mail/mozilla-thunderbird](http://packages.ubuntu.com/gutsy/mail/mozilla-thunderbird)

---

### Post by vurt on 2007-11-27
Thanks guys, i'll make do until the bugs are ironed out i guess.

---

