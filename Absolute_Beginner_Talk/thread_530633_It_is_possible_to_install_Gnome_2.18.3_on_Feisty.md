---
title: "It is possible to install Gnome 2.18.3 on Feisty?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-20
As the title says..

Feisty has gnome 2.18.1, but as you know  gnome folks released some months ago the newest stable version 2.18.3 with lots of bugfixes. I would like to have this specific version, but Ubuntu doesn't integrate this update in my Feisty... So... I can refuse to install it, or maybe I can try to do it by myself. The problem is, I don't have any idea about how to install (or upgrade) my gnome.

Is something a (normal user) can do? 

Somebody wants to help me?

Thank you!

---

### Post by Jimmyfj on 2007-08-20
You might just want to upgrade to Gusty, I have GNOME 2.19.6 running right now

---

### Post by Kosimo on 2007-08-20
> **Jimmyfj said:**
> You might just want to upgrade to Gusty, I have GNOME 2.19.6 running right now

Nope.
Gutsy is still in development. I'm looking for a "very" stable GUI. 

(By the way, I already have another PC with gutsy)

Anyway, thank you for your answer ;)

---

### Post by Kosimo on 2007-08-20
up!

---

### Post by Kosimo on 2007-08-21
up!  :(

---

### Post by Kosimo on 2007-08-21
:(:(:(:(:(:(](*,):frown:

---

### Post by testube_babies on 2007-08-21
The short answer:  No.

The long answer:  Yes.  But compiling Gnome could take a VERY long time, especially the trial-and-error that it takes to get the proper options running.  Also, every package in the repositories is tested and supported on the current version of Gnome, so some might need a recompile to function.  Additionally, system updates fed through Apt could likely break your system after a manual upgrade to Gnome, so further recompilation would be necessary.  Overall, you would probably cause more stability problems by upgrading to 2.18.3 than you would ever want.

---

### Post by Kosimo on 2007-08-21
> **testube_babies said:**
> The short answer:  No.

The long answer:  Yes.  But compiling Gnome could take a VERY long time, especially the trial-and-error that it takes to get the proper options running.  Also, every package in the repositories is tested and supported on the current version of Gnome, so some might need a recompile to function.  Additionally, system updates fed through Apt could likely break your system after a manual upgrade to Gnome, so further recompilation would be necessary.  Overall, you would probably cause more stability problems by upgrading to 2.18.3 than you would ever want.

Yes, I though it was much easier.. 
So, your long answer makes me ask another question.
Why ubuntu community didn't update Feisty with the newest release of 2.18 branch?
2.18.3 should be more stable than 2.18.1 with hundreds of bugfixes.

---

### Post by mikewhatever on 2007-08-21
> Why ubuntu community didn't update Feisty with the newest release of 2.18 branch?
2.18.3 should be more stable than 2.18.1 with hundreds of bugfixes.
As far as I know, most versions of software are not upgraded in one release and you have to wait for the next one to get newer software. This is a reasonable approach, since Ubuntu releases follow every 6 months.
Can you specify some of the features and fixes available in the newer gnome. I've used Edgy before Feisty, and after reinstalling found minor differences (nothing I could not live without) and no performance change, although a lot of people claimed that Gnome on Feisty was better.

---

### Post by igknighted on 2007-08-21
> **Kosimo said:**
> Yes, I though it was much easier.. 
So, your long answer makes me ask another question.
Why ubuntu community didn't update Feisty with the newest release of 2.18 branch?
2.18.3 should be more stable than 2.18.1 with hundreds of bugfixes.

Ubuntu does not upgrade applications mid release.  Even though it is just a bugfix, you never know how little changes can change the way the system as a whole acts.  Plus the devs who would need to make sure that everything works perfectly are busy making sure that Gutsy works perfectly.  It doesn't make a ton of sense to split the work that much.  When security updates come down they are passed out, but otherwise not.  I can almost guarantee you that plugging Gnome 2.18.3 into Feisty would create more issues than you would solve.

The simplest answer is that what you are looking for is against Ubuntu's release policy.  If this is a big deal to you, then you are using the wrong distribution.  Not in any way meant to be mean, just stating a fact that Ubuntu may not be the distro that meets your needs.

---

