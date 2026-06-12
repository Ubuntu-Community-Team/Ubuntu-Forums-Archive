---
title: "How to upgrade."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Jokeaflorias on 2007-06-19
I'm running Edgy, fully updated, and I'd like to upgrade to Feisty Fawn, except the orange square isn't in the top right for me to click. How can I bring up the updates interface without waiting for that symbol to be there?

---

### Post by BarfBag on 2007-06-19
You can't upgrade to Feisty Fawn with the update manager.  You have to use the terminal.  Back up your data, and type the command below.

> sudo apt-get update
> sudo apt-get dist-upgrade

---

### Post by Jokeaflorias on 2007-06-19
Yeah, but it always has a box at the top of the update box asking if I want to upgrade to Feisty Fawn. When I tried that command you gave me, I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dist-upgrade

---

### Post by bodhi.zazen on 2007-06-19
Ummm ... NO NO NO :lolflag:

Update manager is the recommenced method :

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)


_Note_: This is new as of 6.10 (Edgy)

Open System -> Administration -> Update Manager

---

### Post by bodhi.zazen on 2007-06-19
> **BarfBag said:**
> You can't upgrade to Feisty Fawn with the update manager.  You have to use the terminal.  Back up your data, and type the command below.

you have to update your sources first :)

Look up for information on Edgy =^.^=

---

### Post by diatribe on 2007-06-19
> **bodhi.zazen said:**
> you have to update your sources first :)

Look up for information on Edgy =^.^=

I thought update-manager -c -d would do it?

---

### Post by bodhi.zazen on 2007-06-19
> **diatribe said:**
> I thought update-manager -c -d would do it?

lol

Same thing, CLI vs GUI

I was responding to apt-get dist-upgrade (which now that I look back is slightly incorectly posted as apt-get install dist-upgrade)

_Note_: It can be done with apt-get, but expect some breakage (which if you know what you are doing you can fix without too much difficulty, but I would not advise it in general).

---

