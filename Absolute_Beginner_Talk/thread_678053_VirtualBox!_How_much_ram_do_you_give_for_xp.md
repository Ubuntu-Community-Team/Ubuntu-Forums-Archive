---
title: "VirtualBox! How much ram do you give for xp?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-01-25
I was just wondering how much ram you give your XP guest OS?

I switch off from 756MB and 1024MB.  My reason is, I use photoshop and illustrator for my school projects.

Specs: 2.0ghz Duo Core T7200, 7700 GO Nvidia, 2 GB DDR2.


I do notices freezing music and freesing of Windows for a few seconds every once in a while during a day.  My standle Programs:  Opera, VirtualBox: XP Professional SP2, Adobe Photoshop CS2, RhythmBox, and Pidgin.

So, returning to my main question.  How much ram do you give for XP?   What programs do you use most of the time?  Do you have any problems with skipping or freezing?

Sugi

---

### Post by insane_alien on 2008-01-25
128MB i use it only for seeing the effects of a virus. i could give it far more(i'm not short of RAM, 8GB ftw!) but it would be pointles.

---

### Post by rscott5 on 2008-01-25
I have 3GB in my system and I run XP Pro through VirtualBox, usually giving it 2GB. The reason for this is my use of XP is converting large amounts of music and I found that if VirtualBox didn't have enough memory when doing heavy operations like that, I get the blue screen of death and the virtual OS restarts.

I never really found a work around, just came to the conclusion that adding more memory must have fixed it since I haven't seen the problem when allowing it 2GB.

---

### Post by gvartser on 2008-01-25
I use Vista, need windows for an old Oracle Application that isn't available for linux at all.

This is an Java application which take a lot resources, i gave 512MB as sys ram and 128 MB as Video RAM.

I must say that this configuration works great. No performance issues inside the guest OS.

Best regz,
/g

---

### Post by Sugi on 2008-01-25
gvartser,
you only gave Vista 512MB?? o.0  Wow, it runs good for you?  How much ram do you have in your PC?  Oh, thanks for the help in my other thread.  Everything is almost working, but I am going to respond to it in a little bit.



I always have XP running.  I got Adobe Photoshop, Illustrator, and ImageReady CS2 installed.  I am going to install some MP3 Tag editor, and maybe video editor?  I don't know, but I am excited.  I will almost never need to boot into windows again. :)

---

### Post by antisocialist on 2008-01-25
a virtualbox of windows is considered booting windows

---

### Post by smacattack on 2008-01-25
> **gvartser said:**
> I use Vista, need windows for an old Oracle Application that isn't available for linux at all.

This is an Java application which take a lot resources, i gave 512MB as sys ram and 128 MB as Video RAM.

I must say that this configuration works great. No performance issues inside the guest OS.

Best regz,
/g


How do you change the video RAM?? I see where I can change my system RAM and I've noticed from within my virtualbox XP that I only have 16MB video RAM, how can I up it?

Is it a specific VM product or something? Right now I use VMServer.

Thanks.

---

### Post by Sugi on 2008-01-26
> **antisocialist said:**
> a virtualbox of windows is considered booting windows

Let me restart that, I will never have to directly boot into Windows again.

---

### Post by gvartser on 2008-01-26
> **smacattack said:**
> How do you change the video RAM?? I see where I can change my system RAM and I've noticed from within my virtualbox XP that I only have 16MB video RAM, how can I up it?

Is it a specific VM product or something? Right now I use VMServer.

Thanks.


I do not know about VMWare, but with vbox you can set this parameter in the general tab whilst configuring the guest machine.

> you only gave Vista 512MB?? o.0 Wow, it runs good for you? How much ram do you have in your PC?

I have 1,5GB as total.

/g

---

### Post by Sugi on 2008-01-26
gvartser:
Did you have problems with installing Vista.  I tried installing it, but I got some weird error within Vista just after inputting my CD key.  The error had nothing to do with the CD key :p  I heard there was some fix for this online?   Maybe?


Sugi

---

### Post by gvartser on 2008-01-26
I do not know, I used an OEM:ed version provided by DELL. Didnt have to supply a serial during the installation, and no I had no error's during the install.

My advice is to "borrow" another VISTA from someone on the internet as your copy has errors. That must be legal eh?!?

/g

---

### Post by JshWright on 2008-03-06
There's really no reason to bump the video ram up. VirtualBox doesn't support 3D, etc...

1024x768x32 will run quite happily in 5MB.

~JW

EDIT: Apologies for the thread resurrection... The wonders of google...

---

