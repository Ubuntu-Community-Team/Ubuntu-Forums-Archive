---
title: "Should I upgrade the Edgy?"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-10-27
I feel as if I have spent a lot of time getting my Dapper version set up and installed with all of the programs that I enjoy.  Not to mention setting up all of the drivers and little nuances that come with coping with a fresh install of Ubuntu.  My question is, is Edgy really worth it to upgrade from Dapper?  Is it possible to install Edgy over Dapper and keep most of my settings, programs, and drivers?  Thanks.

---

### Post by jd65pl on 2006-10-27
If you are happy with your dapper install why not stick with it? After all it is a long term support version and edgy is not.

J

---

### Post by MakLeod on 2006-10-27
That's kind of what I am thinking.  I mean, is there anything so great in Edgy that will make it that much better than Dapper?  Maybe I'll partition 10 gigs or so and try Edgy out...  Plus the LTS thing, makes me want to stick with Dapper.

---

### Post by jd65pl on 2006-10-27
> Maybe I'll partition 10 gigs or so and try Edgy out.

That sounds like a good option that way you have one install to use for working on and another which you could play about on without breaking too much important stuff!
;)

---

### Post by apanloco on 2006-10-27
My $.05:

NO!!

I just ripped out Dapper, which worked 100% perfectly, and installed Edgy (final). After 5 minutes I threw it out because basic functionality didn't work:

* Screen resolution/hz not detected correctly
* Cannot open Audio CDs

I just tried to install Fedora Core 6 instead. When selecting "add other repositorys" the installer crashed :-)

Seems that everything is rushed out, just stick with Dapper.

BR/D

---

### Post by jd65pl on 2006-10-27
You probably cant open audio CD's because you haven't got the codecs.

You could fix your xserver problem by editing /etc/X11/xorg.conf

---

### Post by trippyd on 2006-10-27
> **jd65pl said:**
> If you are happy with your dapper install why not stick with it? After all it is a long term support version and edgy is not.

J

The best answer is to try it out without busting your current install.  The problem with the bleeding edge is you will sometimes find yourself bleeding.

That being said, I took the dive, and haven't had too many serious issues.   Took a couple of hours of tweaking after the install to get it happy.

---

### Post by Aberrix on 2006-10-27
Xorg 7.1 + beta nvidia drivers + beryl = yes please

:)

---

### Post by MakLeod on 2006-10-27
What is the overall speed increase everyone is seeing between Dapper and Edgy?

---

### Post by Brunellus on 2006-10-27
One thing that nobody here has mentioned:  the upgrade mirrors are getting absolutely HAMMERED with so many people upgrading at once.  You will be stuck with slow connections, timeouts, and generally be pretty upset.  

An incomplete upgrade can sometimes leave your computer in an awkward state:  I lost X once because an upgrade didn't go through cleanly.  

My advice:  unless you have a real compelling need to upgrade to Edgy this instant, wait a week or two for the load on the servers to ease up.

---

### Post by Danny Boy on 2006-10-27
After running Eft since knot 2, I just went back to Dapper. Firefox, GDM & Nautlis keeps crashing. Connect To Server doesn't place icons on the desktop until after reboot.

It's final now isn't it? Something happened between RC1 & final that boinked stuff, for me anyhow.

---

### Post by martinbriscoe on 2006-10-27
Dont upgrade unless you really enjoy messing about trying to get software to work and fixing crashes -  I have and its taken many hours and lots still isnt working do to aborted upgrades due to unresolvable errors.

Wait -Dappers fine.

 
Martin
UK

---

### Post by MakLeod on 2006-10-27
Yea, I'm definitely keeping Dapper around for a long while.  Might as well focus all of my computing energy on a LTS version.  8)

---

### Post by jem7v on 2006-10-27
Speed increase? Um, I Might have a slight boot time speed increase? But not much. It's not much. As for speed once things get going and Gnome is cruising along, I haven't noticed any difference, except a few moments where it felt subtly slower.

It took quite a few hours to install - WITH the CD rather than through the repositories, because the upgrade process crashed on me twice. And then there were some version incompatibilities between x.org and nvidia kernels, and that took almost as long to solve. Now that it's dealt with and I've reinstalled a few programs that got removed, everything Works. So far I haven't seen anything that has made me say, "Well, this is undoubtedly better. I sure am glad I switched." Most of the differences have been aesthetic...

Mind you, there are a lot of new programs in Edgy's "Add/Remove..." application that weren't in Dapper's. You could probably have found them through Synaptic instead, but it's just *easier* using the Add/Remove dialogue.

---

