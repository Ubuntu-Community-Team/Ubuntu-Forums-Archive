---
title: "apt-key: command not found?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-17
I'm using Knoppix 3.8, and for some reason apt-key doesn't want to work.

Whenever I try to add a key with it, it just spits out this:

> sudo apt-key add -
sudo: apt-key: command not found

And if I try it without sudo, the same message comes up with bash replacing sudo...

---

### Post by pyros on 2007-07-17
> **ARandomKid said:**
> I'm using Knoppix 3.8, and for some reason apt-key doesn't want to work.

Whenever I try to add a key with it, it just spits out this:



And if I try it without sudo, the same message comes up with bash replacing sudo...

I'm not terribly familiar with knoppix anymore, but it sounds like it isn't installed... try typing apt and then using tab complete to see what commands are available.

---

### Post by ARandomKid on 2007-07-17
Heh, what do you know - it ain't there!

;>.> Yet another thing that isn't working...I hate outdated versions. Granted, I'd probably be having the same problems in Feisty, but maybe not....

---

### Post by pyros on 2007-07-18
> **ARandomKid said:**
> Heh, what do you know - it ain't there!

;>.> Yet another thing that isn't working...I hate outdated versions. Granted, I'd probably be having the same problems in Feisty, but maybe not....

nope, it's in Feisty, I checked. you could see if add-apt-key is in there...

---

