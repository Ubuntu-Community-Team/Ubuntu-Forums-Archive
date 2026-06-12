---
title: "evil user problems"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Mr.Carramba on 2008-01-30
Hi!

I have installed ubuntu on the machine were evil user works. he always messes thing up in mysterious ways, even if this computer skills are below 0.   

so my questions: how-to
change sudo password? (now it's same as users)
allow only access to one folder?
make OpenOffice save only in one folder (user are not allowed to navigate to up from the folder only down)
disable any program installation and removal or configurations without sudo.
allow only some program uses for certain user
at the same time keep functionality so that user can work on station.

create shortcut on desktop for user log out, disable restart and shutdown   

Thank you in advance!

---

### Post by dcstar on 2008-01-30
> **Mr.Carramba said:**
> Hi!

I have installed ubuntu on the machine were evil user works. he always messes thing up in mysterious ways, even if this computer skills are below 0.   

so my questions: how-to
change sudo password? (now it's same as users)
allow only access to one folder?
make OpenOffice save only in one folder (user are not allowed to navigate to up from the folder only down)
disable any program installation and removal or configurations without sudo.
at the same time keep functionality so that user can work on station.

Thank you in advance!

Make a "Standard" user account with no admin rights, that is exactly what they are for.

The user account created by the install is "Special" with admin rights - otherwise you would never be able to control and configure the installation.

---

### Post by Mr.Carramba on 2008-01-30
> **dcstar said:**
> Make a "Standard" user account with no admin rights, that is exactly what they are for.

The user account created by the install is "Special" with admin rights - otherwise you would never be able to control and configure the installation.

ok, I guessed that but how to do  it?
what recourses should I add so that user wont experience problems using pc?

are this enough 

> audio, cdrom,  dip, games, lp,  scanner, ssh, video

what is dip?

---

### Post by Infinity-al on 2008-01-30
System > Administration > Users and Groups > Add User... And configure his account to your liking...

---

### Post by Mr.Carramba on 2008-01-30
thanx!
It seems to work quite good, but why does firefox add-on are gone? I mean like flash?
do I need to reinstall it for each user?

---

### Post by dcstar on 2008-01-30
> **Mr.Carramba said:**
> thanx!
It seems to work quite good, but why does firefox add-on are gone? I mean like flash?
do I need to reinstall it for each user?

Some plug-ins install into individual home directories, others are system wide.

The Flash install may have been done as a user install instead of the other way.

---

### Post by Mr.Carramba on 2008-01-30
> **dcstar said:**
> Some plug-ins install into individual home directories, others are system wide.

The Flash install may have been done as a user install instead of the other way.

is it enough to copy .firefox folder and change right for user ? would it work? or I have to reinstall?

how to I make installation system wide?

---

### Post by Mr.Carramba on 2008-01-30
well it worked !
I just copied plugins folder and bum! ^^ hehe thank you guys!

---

