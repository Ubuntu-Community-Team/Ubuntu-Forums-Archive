---
title: "Upgrading, but not losing data..."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by grahamroese on 2007-04-12
Hi there! I'm real sorry if this is a repost, but...

I am using Dapper Drake (v.6.06 LTS), and I have had several pleasant computing experiences with it. However, the more I read about 7.04, the more I feel like wanting to try... But since I've never upgraded versions before, I am not sure if I will be able to install the new OS without losing all of my data, including my media and hardware support (because these were major accomplishments to install all by myself!) I kid. Because I love.

But anyhow, if anybody could help, I would be so appreciative!


Thank you!

---

### Post by sailor2001 on 2007-04-12
sudo apt-get dist-upgrade should get you into edgy upgrade and shouldn't lose any previous data.... The newest upgrade ( feisty) is ready in a few more days, but you can't jump upgrades...1 at a time

---

### Post by gh0st on 2007-04-12
```
sudo apt-get dist-upgrade
```

Should do the trick, it just upgrades all your packages without destroying configuration or personal data :)

You should backup your data regularly to an external disk if you can to be safe, I had a hard disk fail on me once and learnt the hard way ;)

---

### Post by FuriousLettuce on 2007-04-12
OS upgrades should be painless under Ubuntu :) There's no reformatting etc, it simply updates the computer like it normally would if it were downloading simple security updates. If you're worried, you can backup your data, but it should all just go seamlessly with nothing to worry about. As sailor said, use 
```

sudo apt-get dist-upgrade

```
and all will be well,

---

### Post by aysiu on 2007-04-12
Upgrading from Dapper to Feisty is a recipe for disaster.

The safest way to upgrade would be from Dapper to Edgy and then to Feisty... but that would also take forever.

So your next best bet is to [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome) and then just do a clean reinstall of Feisty when it's released.

Double upgrade--I'd estimate about five hours on broadband. Single reinstall--I'd estimate about an hour and a half to download the ISO (over broadband), burn it, and install the OS.

Go for the reinstall.

---

