---
title: "it plays bad quality video"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by raffaello on 2006-10-07
Hello community,


this is my first post and i am a newbie....so i really need info!!!  a friend of mine usually drive me fixing all my trouble when on line, but he got sick and now.....big sh...
i had a big fight with totem video player to play a dvd, because totem play every dvd with bad quality video. i tried others and i installed at the same time xine and vcl too, since the video still have quality problem

now, i still cannot see a dvd with the proper quality, so it means supposedly that i need to set up some properties or things like that.

can you give me some tip or idea??

Tnx

---

### Post by Sef on 2006-10-07
Have you checked out [Restricted Formats?]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9")

---

### Post by PPAAUULL on 2006-10-07
Could use EasyUbuntu or Automatix.

---

### Post by Dinerty on 2006-10-07
I have noticed a new client called "ogle" which is availabel in the Synaptic Package Manager.

System > Applications > Synaptic Package Manager then search for "ogle" and install the following:

>ogle
>ogle-gui
>ogle-mmx

Like previously mentioned, go to:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by podunk on 2006-10-07
I had a hard time with Totem also. So hard a time I gave up on it and used Synaptic Package Manager to install Gxine.

Assuming you have the non free video codecs installed:
System>Administration>Synaptic Package Manager

Search for gxine
Right click gxine and chose “Mark for Install”
Right click gxine-plugin and chose “Mark for install”
In the bar click the green check mark “Apply”

It will install Gxine in the Applications> Sound and Video folder

When you start Gxine it has a Set up Wizard which checks your set up and tells you if you have any problems (it turned out DMA wasn't on for my DVD player which was why I was having so much trouble with Totem)

If you continue to have problems with the video (and I did) like green lines or dropped frames there is a nice check list/how to here to fix it:
[http://xinehq.de/index.php/faq](http://xinehq.de/index.php/faq)

Once I got everything set up I stuck with Gxine because the user interface is more to my liking, but I bet if I tried Totem it would work now also.

My movies play a lot better in Ubuntu than they ever did in Windows.

If you don't have the non free codecs installed go here and install Automatix:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

