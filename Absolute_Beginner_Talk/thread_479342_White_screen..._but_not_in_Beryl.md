---
title: "White screen... but not in Beryl"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by nikohs on 2007-06-20
I have the newest kernel of Ubuntu and partitioned off 15 gigs of my ample hard drive to test it out. In doing so I stumbled across a feature of the desktop much like running beryl (i.e. windows "wobble", cube desktops ...). As soon as I turned this feature on my desktop went white. I cannot get rid of the white, nor can I access my menus. I am able to get into my command line, but i dont know what to change!!!! HELP 

P.S. I already configured my video card... so thats not it

---

### Post by overdrank on 2007-06-20
> **nikohs said:**
> I have the newest kernel of Ubuntu and partitioned off 15 gigs of my ample hard drive to test it out. In doing so I stumbled across a feature of the desktop much like running beryl (i.e. windows "wobble", cube desktops ...). As soon as I turned this feature on my desktop went white. I cannot get rid of the white, nor can I access my menus. I am able to get into my command line, but i dont know what to change!!!! HELP 

P.S. I already configured my video card... so thats not it

Hi ok I believe you are using compiz that comes with feisty and I am not a expert with compiz but it still maybe with your video card. Which graphics card are you using!

---

### Post by nikohs on 2007-06-20
ATI radeon 200M, in a compaq R4000 laptop

---

### Post by overdrank on 2007-06-20
> **nikohs said:**
> ATI radeon 200M, in a compaq R4000 laptop

Have you enabled the restricted drivers on feisty? They are under system, administration, restricted driver manager.

---

### Post by nikohs on 2007-06-20
I havent done a freakin thing! And I cant access that as I cannot see any of my GNOME screen... its all white!!! EEK

---

### Post by overdrank on 2007-06-20
> **nikohs said:**
> I havent done a freakin thing! And I cant access that as I cannot see any of my GNOME screen... its all white!!! EEK

YOu can try ctrl,alt, backspace to restart x and see it that helps if not then maybe someone else can help

---

### Post by capecove on 2007-06-20
Yeah, and a 

sudo dpkg-reconfigure xserver-xorg

May not be out of the question?

---

### Post by meuge on 2007-06-20
> **nikohs said:**
> I have the newest kernel of Ubuntu and partitioned off 15 gigs of my ample hard drive to test it out. In doing so I stumbled across a feature of the desktop much like running beryl (i.e. windows "wobble", cube desktops ...). As soon as I turned this feature on my desktop went white. I cannot get rid of the white, nor can I access my menus. I am able to get into my command line, but i dont know what to change!!!! HELP 

P.S. I already configured my video card... so thats not it

Did you have to use XGL with fglrx drivers? If you did, then just click "change session" in the login screen and choose GNOME instead of XGL. When you log in, you'll be able to disable desktop effects. 

I suggest installing Beryl, and using my solution to get rid of the white cube bug (search for my recent posts).

---

### Post by meuge on 2007-06-20
> **capecove said:**
> Yeah, and a 

sudo dpkg-reconfigure xserver-xorg

May not be out of the question?

I suppose he could just switch to the vesa or ati driver with no 3D support, then disable desktop effects, then switch back.

---

### Post by felipe82 on 2007-06-25
I'm sorry, really stupid question. I'm having the same problem with the white screen, but I don't know how to open a terminal window :P . Thx.

---

### Post by overdrank on 2007-06-25
> **felipe82 said:**
> I'm sorry, really stupid question. I'm having the same problem with the white screen, but I don't know how to open a terminal window :P . Thx.

Hi it is located under applications, accessories, terminal  But are you using 5.10 breezy?

---

### Post by felipe82 on 2007-06-25
> **overdrank said:**
> Hi it is located under applications, accessories, terminal  But are you using 5.10 breezy?

No, I'm using Fiesty. I already found it tough. Unfortunately something bad happened (altough kinda funny): I managed to open the terminal window and run the Xserver config util, but when I finished my keyboard layout was in arabic (I think), so there was no way for me to enter my username (felipe) and log in the system, even in terminal mode :(

Anyway, I just reinstalled and I'm runnig automatix right now to install everything again. Thanks a lot anyway.

---

