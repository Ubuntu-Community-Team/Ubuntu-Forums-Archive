---
title: "No sound output. Ubuntu 11.04 on MacBookPro3,1"
date: 2011-05-24
forum: Apple Hardware Users
---

### Post by BigIslandVegan on 2011-05-24
I'm trying to help a friend move to Ubuntu 11.04 from Mac OS 10.4.11 on a MacBookPro3,1.

We have great success minus the sound output. Sound input works but not output.

Here is the alsa-base.conf [http://pastebin.com/N5QDMVvU](http://pastebin.com/N5QDMVvU) as it came from a fresh install of Ubuntu 11.04

I found this suggestion to get sound working on this mac in ubuntu 10.10 but I don't see the same thing in 11.04 as listed here:

[https://help.ubuntu.com/community/MacBookPro3-1/Maverick](https://help.ubuntu.com/community/MacBookPro3-1/Maverick)

I thank you for your time and attention.

---

### Post by papibe on 2011-05-24
Maybe the outputs are muted. Try  [alsamixer]("http://alsa.opensrc.org/Alsamixer"). Check [this]("http://www.patheticcockroach.com/mpam4/index.php?p=62").

Run it like this:
```
$ alsamixer
```
Unmute the speakers, test them. When you get the results you're going for, save the settings like this:
```
$ alsactl store
```
Regards.

---

### Post by BigIslandVegan on 2011-05-29
I thank you very much for the quick response. Only today was I able to access her machine to try your suggestions. I was not able to get it to work, unfortunately. Has anyone had functional sound output on the MacBookPro3,1 with Ubuntu 11.04?

---

### Post by ritchiewall on 2011-05-30
Hey there.

I too am having problems, initially I installed 11.04 and sound was working OK.. then after a little playing :( I can either get the microphone or speakers to work, it won't recognise them at the same time! I have tried many suggestions on here but to no avail. I would love to be able to use skype again but am having to go back to windows.

PS I am brand new to linux. Thanks.

---

