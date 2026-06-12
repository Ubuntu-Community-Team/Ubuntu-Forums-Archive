---
title: "Is Dapper Drake not supported now ??"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Googler on 2007-12-21
Hi everybody
i'm using Ubuntu Dapper Drake and everytime i try to compile packages i face a problem of dependencies, it requires the newer version of that dependency than the installed one.
i always make my system updates, so i wonder is dapper drake not supported now so i have to upgrade to feisty?

regards,

---

### Post by seventhc on 2007-12-21
Why don't you use
Ubuntu 7.10 - Gutsy Gibbon - released in October 2007.

---

### Post by L Campbell on 2007-12-21
> **Googler said:**
> Hi everybody
i'm using Ubuntu Dapper Drake and everytime i try to compile packages i face a problem of dependencies, it requires the newer version of that dependency than the installed one.
i always make my system updates, so i wonder is dapper drake not supported now so i have to upgrade to feisty?

regards,

If you look here:- [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

you will see it is supported till 2009

Hope this helps.

---

### Post by Sef on 2007-12-21
> i'm using Ubuntu Dapper Drake and everytime i try to compile packages i face a problem of dependencies, it requires the newer version of that dependency than the installed one.
i always make my system updates, so i wonder is dapper drake not supported now so i have to upgrade to feisty?


Dapper Drake is a Long Term Stable (LTS)  version which means it is supported for 3 years on the desktop (ends June 09) and 5 years as a server (ends June 11.)

---

### Post by GGLucas on 2007-12-21
Ubuntu works with a release mechanism that updates the packages to new versions only in new releases (most of the time), which means you have old versions of libraries that won't work with recent versions of whatever software you are trying to compile, it's still supported, but with the old packages and programs, not with newer ones.

---

### Post by insane_alien on 2007-12-21
dapper drake is really meant for sitting for a long time and not changing. this is what it was intended for. it still get numerous security updates so it is safe to use. 

this means that every now and again if you are compiling a new program you will encounter dependancy issues as the installed files are old and stable.

you should use gutsy if you like keeping things up to date.

---

### Post by Googler on 2007-12-21
thanks everybody,
the image is clear now.
so it's time for Gusty.

---

### Post by maljaros on 2007-12-21
Not a solution, just a philosophical aside.  You have just made clear to me something that I have struggled to grasp, which is when to upgrade to a newer release. Obviously it is a trade-off between stability (if it aint broke dont fix it) and new features. The reason I hadn't figured this out before was that I never managed to get my system the way I wanted it and would eventually change (usually to a competing distro) just to get away from the same old problems.  Ubuntu has finally allowed me to break out of this endless cycle.  Gutsy is loaded on my box and Feisty on the wife's.  It wasn't planned, it just happened that way - and the reason has to be that she wants things to stay the way they are and I want to try out new toys in a (reasonably) stable environment.  Fortunately, now that the basic needs are covered, I still have space on my drive to install Arch :)

---

### Post by saltydog on 2007-12-21
I have dapper installed on my production server since 2006. As v 8.04 will be another LTS, anybody knows if I could then upgrade directly from 6.06 to 8.04, without the need of going thru sequenced updates?

---

### Post by thelatinist on 2007-12-21
> **saltydog said:**
> I have dapper installed on my production server since 2006. As v 8.04 will be another LTS, anybody knows if I could then upgrade directly from 6.06 to 8.04, without the need of going thru sequenced updates?

I think it would be strongly recommended to use a fresh install.  The extra time it would take to get things set up just the way you want them would be more than offset by the avoidance of potential upgrade issues, especially since you would have to do several sequential upgrades.

---

### Post by saltydog on 2007-12-22
> **thelatinist said:**
> I think it would be strongly recommended to use a fresh install.  The extra time it would take to get things set up just the way you want them would be more than offset by the avoidance of potential upgrade issues, especially since you would have to do several sequential upgrades.

This is not easy for a server which is running since 2 years. There are a lot of tunings-configuration that I will lost,

---

### Post by Sef on 2007-12-22
> The extra time it would take to get things set up just the way you want them would be more than offset by the avoidance of potential upgrade issues, especially since you would have to do several sequential upgrades.

I have heard that it will be possible to upgrade directly from Dapper to Hardy, the next LTS. I am not sure if this is correct or not though.  If it is true, then upgrading will be much easier.

---

### Post by saltydog on 2007-12-22
> **Sef said:**
> I have heard that it will be possible to upgrade directly from Dapper to Hardy, the next LTS. I am not sure if this is correct or not though.  If it is true, then upgrading will be much easier.

That's exactly the info I was looking for. Where can I ask for confirmation?

---

### Post by hyper_ch on 2007-12-22
why do you want the server to upgrade? is it runing the way you want it to?

---

### Post by saltydog on 2007-12-22
I want to include latest apache2 with latest modules. The current dapper version has at least 15 vulnerabilities warnings.

---

### Post by hyper_ch on 2007-12-22
but they are fixed... that's what the 5 year support service does

---

### Post by saltydog on 2007-12-22
> **hyper_ch said:**
> but they are fixed... that's what the 5 year support service does

No. they are not fixed. I have just run a Vulnerability & Security Discover platform over my dapper server, and it cames out that 19 vulnerabilities are installed. First of one will require to update APache2 to version 2.1.6 which is not available in dapper.

---

### Post by thelatinist on 2007-12-22
> **hyper_ch said:**
> but they are fixed... that's what the 5 year support service does

From the Dapper release notes:  "Ubuntu 6.06 LTS (Long Term Support) will be supported with security updates for 5 years on the server and 3 years on the desktop after its release."

I don't have Dapper,  so I can't confirm.  *shrug*

---

### Post by saltydog on 2007-12-22
> **thelatinist said:**
> From the Dapper release notes:  "Ubuntu 6.06 LTS (Long Term Support) will be supported with security updates for 5 years on the server and 3 years on the desktop after its release."

I don't have Dapper,  so I can't confirm.  *shrug*

Words... Look at the attachment.

---

### Post by thelatinist on 2007-12-22
> **saltydog said:**
> Words... Look at the attachment.

Ubuntu update will not include version-upgrades of software, only security fixes for the versions included in releases.  Rather than upgrading Apache versions, for instance, Dapper will include a patch to fix the security hole.  Are you sure that your vulnerability detection software is actually checking for the vulnerabilities and not just checking software versions?

If you want be on the cutting edge with the latest versions of software, upgrade to Gutsy.  If you want an OS you can set and forget, relying on updates to keep you safe, stick with Dapper.  It's that simple.

---

