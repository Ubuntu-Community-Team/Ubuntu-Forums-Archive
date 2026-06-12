---
title: "Ubuntu 7.04 Minimal fails at &quot;select and install software.&quot;"
date: 2008-02-15
forum: Apple PPC Users
---

### Post by Cleric. on 2008-02-15
I'm attempting to install Ubuntu 7.04 on a blue and white Mac G3 using the minimal disc. I picked 7.04 because of all the problems people seem to be having with 7.10. 
After I choose which desktop I want to install, it fails, only telling me that it failed at "select and install software."

I looked at some other threads where people had the same problem, but most of them seemed to have been disc-related; since the minimal disc downloads everything from the internet, I don't think there would be much of an issue with the disc itself.

Also, when I attempt to go on to the next step, "build LSTP chroot", it fails too.

Is there any other information I can provide to help with this problem?

---

### Post by VCF on 2008-02-15
> **Cleric. said:**
> I'm attempting to install Ubuntu 7.04 on a blue and white Mac G3 using the minimal disc. I picked 7.04 because of all the problems people seem to be having with 7.10. 
After I choose which desktop I want to install, it fails, only telling me that it failed at "select and install software."

I looked at some other threads where people had the same problem, but most of them seemed to have been disc-related; since the minimal disc downloads everything from the internet, I don't think there would be much of an issue with the disc itself.

Also, when I attempt to go on to the next step, "build LSTP chroot", it fails too.

Is there any other information I can provide to help with this problem?

I was trying the minimal CD image install with 7.10 last night and had the same problem if I chose anything except the Gnome desktop. I had a bunch of other stuff checked off which I think might have given problems.

Did it install the "base system" files OK?  

After I had the problem at "select and install software" I chose the install base system again just to be sure.  It asked me if I wanted to install on a "dirty" system, I just said yes, go ahead and everything went OK from there.

---

### Post by Cleric. on 2008-02-15
Yeah, it installed base system alright, it just failed at about 90% when it seemed like it was finishing with the Xubuntu installation.

I'll try disabling Xubuntu and installing the regular Ubuntu desktop and see how it goes.

---

### Post by Cleric. on 2008-02-15
Completely skipping the errors and going on with the installation seemed to do the trick.
My performance seems like it's garbage though.
I'll try to figure that out.

Thanks for your help.

---

### Post by VCF on 2008-02-15
> **Cleric. said:**
> Completely skipping the errors and going on with the installation seemed to do the trick.
My performance seems like it's garbage though.
I'll try to figure that out.

Thanks for your help.

You're welcome!  

Be very careful in upgrading to 7.10 once you get 7.04 running well enough.  I've done that and have had nothing but trouble (but I haven't given up yet!)

---

### Post by stream303 on 2008-02-16
I wonder if the repository you've chosen might be having problems.  From what I remember, I only saw the one in the UK as being a hard-coded option.  Do you have better success choosing a different repository (for those not actually in the UK)?

---

### Post by VCF on 2008-02-16
> **stream303 said:**
> I wonder if the repository you've chosen might be having problems.  From what I remember, I only saw the one in the UK as being a hard-coded option.  Do you have better success choosing a different repository (for those not actually in the UK)?

That one (UK) worked perfectly for me a couple of days ago.  I'm in Western Canada.....

---

### Post by powerbookluv111 on 2008-02-23
I have this same problem on Installing 7.10 from the alternate disc. I finally got the base system to install, but now it always fails on "Select and Install Software." This is rreaaallly getting annoying how uneasy it is to get Ubuntu running. Any ideas?

---

