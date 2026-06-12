---
title: "Experimenting with Kubuntu"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by baillie on 2006-12-24
Hi,

Bear with me here, I'm not entirely sure I'll be able to express this quite the way I want to :) I am new to Ubuntu/Kubuntu and Linux in general so there is a lot of experimenting going on, its the only way to learn after all. 

In Windows (where I know what I'm doing) each user isn't really independent of each other, i.e. if one user messes up the system it's messed up for everybody, Is it the same in Ubuntu?

What I want to do is set up a second account where I can mess about, try installing things (such as Baghira), before I try it in my main account, with the knowledge that even if I mess up the second account my first one will be ok. I can then delete the second account and create a new one if something goes wrong.

Is this correct, presumably if I messed up enough it would break the system, but is it generally more robust than windows?

I hope thats clear enoug, if not I can try explaining again.

Thanks

---

### Post by MkfIbK7a on 2006-12-24
am i right in assuming you havent got anything important on your hardrive if so you can do whatever and just reinstall the operating system if it gets ruined!

im serious!

---

### Post by Frak on 2006-12-24
You have it correct, there should be an option to make it completely independent, in Kubuntu that is in the Kmenu->System Settings-> Users or Groups or something like that, in Ubuntu its in System->Administration->Users and Groups. BUT BE CAREFUL WHEN INSTALLING TO THE $HOME DIR.

Merry Christmas!

---

### Post by taurus on 2006-12-24
If you mess up in Ubuntu, you just mess up your own $HOME so technically, you can delete it and create it again.  It has no effect to others on the same system, assuming you don't install stuff to the system and only installing it to your own $HOME directory...  That's why be real careful with the sudo command!

---

### Post by MkfIbK7a on 2006-12-24
Yes in 6.06 its in **Menu** > **System settings** > **User groups**
in 6.10 menu >system settings > users and click on the tab "groups"

---

### Post by baillie on 2006-12-24
That was quick!

Thanks guys for the responses, if anything major went wrong I could easily reinstall, it's a new install anyway, and it only took about 20mins to install last time.

> You have it correct, there should be an option to make it completely independent, in Kubuntu that is in the Kmenu->System Settings-> Users or Groups or something like that, in Ubuntu its in System->Administration->Users and Groups. BUT BE CAREFUL WHEN INSTALLING TO THE $HOME DIR.

I'll have a look for that later on tonight.

---

### Post by pseudonym on 2006-12-24
Any Linux is 'generally more robust than windows' :)

To add to this, you also have these approaches to isolate your 'test runs' from the main system -

1. Install a second copy of Ubuntu/Kubuntu/Xubuntu into a spare partition on your hard drive or, better yet, installing it on to a second hard drive (a cheap 10gb one off ebay is good enough).

2. (and this may be a little advanced) create a 'chroot' environment. This is basically a second system within your system, where you can do exactly what you want to do and not have it affect your main system. there is a wiki entry on doing this [here]("https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29") and I think there's a couple of howtos on it in the howto section of the forums.

HTH

---

### Post by spockrock on 2006-12-24
sorry guys, but how does one set up the user so that when they install something its in the $HOME directory??

---

### Post by taurus on 2006-12-24
> **spockrock said:**
> sorry guys, but how does one set up the user so that when they install something its in the $HOME directory??

Don't put that user in groups adm & admin and that user cannot install anything outside his/her $HOME directory.  That's all there is to it...

---

### Post by pseudonym on 2006-12-24
> **taurus said:**
> Don't put that user in groups adm & admin and that user cannot install anything outside his/her $HOME directory.  That's all there is to it...
Aah, I didn't know that! :o Pay no attention to what I wrote above unless you really like experimenting.

---

### Post by spockrock on 2006-12-24
> **taurus said:**
> Don't put that user in groups adm & admin and that user cannot install anything outside his/her $HOME directory.  That's all there is to it...

thank you very much for that tidbit of knowledge....

---

### Post by taurus on 2006-12-24
> **spockrock said:**
> thank you very much for that tidbit of knowledge....

You're welcome.

---

