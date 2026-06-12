---
title: "Comparing Lubuntu 14.04 and Debian Jessie"
date: 2014-12-16
forum: Apple Hardware Users
---

### Post by rican-linux on 2014-12-16
I have been running Jessie for over a week. Overall I liked using it however there was still plenty of bugs I found. So last night I loaded Lubuntu 14.04 and am going to see how it compares then install wheezy. So far I have seen similar issues on Lububtu that were on Jessie.

1. KMS: to get Xvid to work I need to load KMS which was not hard but 3D acceleration was not working. In Jessie I need to create an xorg.conf file and set the DefaultDisplay to 16 to get a somewhat working 3D. I really did not want to do that here so I found a 'hack' [here]("http://ubuntuforums.org/archive/index.php/t-2183771.html"). This has given a somewhat working 3D acceleration w/o changing my display.

2. browser crases: In jessie Midori, luakit, ans surf all crashed when trying to start. I placed a bug report for surf with no resolution as of yet. However iceweasel and qupzilla worked fine. Now in Lubuntu qupzilla, surf, midori, and laukit crash. I am attaching debug traces if anyone who is software savy wants to take a look.

Has anyone else seen similar issues or has a better solution for 3D acceleration? Thanks!


[ATTACH]258638[/ATTACH][ATTACH]258639[/ATTACH][ATTACH]258640[/ATTACH]

---

### Post by este.el.paz on 2014-12-16
@r-l:

If you are looking at Wheezy then why don't you try 12.04?  If my iMac was still running I would still be happy with Xubuntu 12.04 w/LXDE/Openbox as added DEs . . . .  I'm on the line between keeping 14.04 on my iBook or rolling it back to 12.04 where it was quite fine . . . .

Searching the forum for posts by "str8bs" or "rsavage" and a few others . . . should bring a number of threads on "acceleration in 12.04" . . . since I have 32 bit PPC I had no need for understanding acceleration . . . or the lack of it.

I also had a Wheezy install on the iMac, I believe it was about 1.5 years ago, it's fine . . . saw a recent post thru someone's link here where "zen" was talking about his Deb7 + LXDE install on a powerbook . . . but, keep in mind that for the most part debian is a server system . . .  so the GUI is not as "integrated" as the Ubuntu options are . . . .

In terms of escaping bugs . . . nature of the beast . . . "resistance is futile . . . ."

e.e.p.

---

### Post by rican-linux on 2014-12-17
I have used Ubuntu and Xubuntu 12.04 already. I have been exploring different distros and so far Debian LXDE has really impressed me with with how well it runs on my PowerBook G4. I have heard great things about the stability of wheezy.I am curious to see how lubuntu compares.

---

### Post by rsavage on 2014-12-17
> **rican-linux said:**
> Now in Lubuntu qupzilla, surf, midori, and laukit crash. I am attaching debug traces if anyone who is software savy wants to take a look.

qupzilla works in trusty when you patch qtwebkit.  I expect midori etc will also work when webkitgtk are patched.  See known issues page.

---

### Post by rican-linux on 2014-12-17
@rsavage thanks will do.

---

### Post by rican-linux on 2014-12-19
I went through the thread and could not find the patch to install. I know in Jessie they have it already patched version in the repos. Do you know when it will move to Ubuntu?

---

