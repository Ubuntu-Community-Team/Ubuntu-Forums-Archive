---
title: "[SOLVED] Update manager annoyance: notifying me of an unstable version"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by _sluimers_ on 2008-02-03
I don't want the newer version of audacity or vmware since they don't work right, but Update manager keeps wanting me to update them with automatic checks and it's notifier. I accidentally updated vmware again because of this.

How do I stop this madness?

---

### Post by jan quark on 2008-02-03
perhaps you can disable the updater in the sessions window
system > preferences > session

and run updates manually with 
```
sudo apt-get update
```
and checking in synaptic what do you want to update

---

### Post by SunnyRabbiera on 2008-02-03
yeh ubuntu's updater is pretty messy and has a good chance to mess things up.
This is why I like linux mint better.

---

### Post by jan quark on 2008-02-03
SunnyRabbiera welcome in the mint user team :)

---

### Post by hyperair on 2008-02-03
Rather than disabling update-notifier as jan quark said, there's a better method involving Synaptic.

First, open Synaptic Package Manager. make sure the version of audacity and vmware are the ones you want. Then, for each of them, click Package->Lock Version. Now update-notifier will stop bugging you about those packages.

@SunnyRabbiera: I don't think I like Linux Mint's updater much. It can't do distro upgrades yet can it? You still have to go back to the old sudo apt-get dist-upgrade for it. IMO, update-manager's plenty good. But that's just my opinion.

---

### Post by SunnyRabbiera on 2008-02-03
> **hyperair said:**
> Rather than disabling update-notifier as jan quark said, there's a better method involving Synaptic.

First, open Synaptic Package Manager. make sure the version of audacity and vmware are the ones you want. Then, for each of them, click Package->Lock Version. Now update-notifier will stop bugging you about those packages.

@SunnyRabbiera: I don't think I like Linux Mint's updater much. It can't do distro upgrades yet can it? You still have to go back to the old sudo apt-get dist-upgrade for it. IMO, update-manager's plenty good. But that's just my opinion.


well even if it doesnt do dist upgrades perhaps that can be concidered a good thing, after all more people break their systems with ubuntus dist upgrade feature and people should have the option to choose if they want to upgrade or not.
I find ubuntus updator annoying when a new version is out... a new version of ubuntu is out, blah, blah, blah who cares as my current system is working thank you very much.
Ubuntu's updater is too MS like.

---

### Post by hyperair on 2008-02-03
This really isn't the place to start a heated argument of Linux Mint vs Ubuntu. But I'd like to clarify a few points, even in my sleep-deprived state, before I go to sleep.

1. Many more people break their systems using sudo apt-get dist-upgrade compared to using the update-manager's distribution upgrade feature.

2. People DO have the option to choose whether they want to upgrade or not. It's not a do or I'll shut you down thing like Windows's is.

3. A new version of ubuntu is out doesn't mean that you must install it. The button's just there in the event that you want to. 

4. Don't even get me started on how different update-manager is from MS's updater.

Like I said in my previous post. everybody's entitled to their own opinion. I don't oppose you using Linux Mint, but I must say, please don't run down Ubuntu when you promote Linux Mint.

---

### Post by SunnyRabbiera on 2008-02-03
I am just telling it as i feel, I am not arguing as I like both mint and ubuntu...
But there are some things that annoy me about ubuntu, but meh.

---

### Post by hyperair on 2008-02-03
Fair enough, let's leave it as that.

---

