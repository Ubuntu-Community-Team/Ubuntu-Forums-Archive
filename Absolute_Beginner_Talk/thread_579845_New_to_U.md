---
title: "New to U*"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Mikeoak on 2007-10-18
Hello friends,

I am new to Ubuntu, but in a way am not as I used Mepis 6.5 and I guess it was built on Ubuntu.

Anyway, am loving it after getting used to Gnome which felt like I was driving on the wrong side of the road, a little disorienting.  I have 7.10 rc installed and am quite pleased with it after doing some tweaks such as installing Mplayer and dropping Totem.  Not crazy about the brown, but boy it is easy to change and also changed to panels to match the background.  I think it looks beautiful.

Question for you:  since I installed the rc, will the update manager create the same thing as the final release or should I download and install the new 710 final?:)

---

### Post by p_quarles on 2007-10-18
No, don't bother. I've been running the rc for the past week. When I booted it up today, it told me I could update to the new distribution -- I ran the wizard, and after checking a few things it told me I was already up to date.

Very lilttle changes between the rc and the final release, so everything that does will be easily handled by whatever package manager you are using.

---

### Post by Technoviking on 2007-10-18
Nope, you just need to make sure your updated from the RC.
```

sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by Mikeoak on 2007-10-18
Thanks for the quick response.  The Update Manger says I am up-to-date.  Does aptitude do a better job?

---

### Post by p_quarles on 2007-10-18
> **Mikeoak said:**
> Thanks for the quick response.  The Update Manger says I am up-to-date.  Does aptitude do a better job?
Nah. They're both just front-ends for APT. You're good to go.

---

