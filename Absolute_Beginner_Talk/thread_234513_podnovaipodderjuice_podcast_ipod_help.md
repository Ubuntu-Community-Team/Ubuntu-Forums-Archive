---
title: "podnova/ipodder/juice podcast ipod help"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-08-11
I have ipodder, but I can't move tracks to my ipod with it.  I have to use banshee with it, which is not fun.  Is there any better program to use in linux?

---

### Post by ben2talk on 2008-03-30
I'm having trouble too, using Rhythmbox for podcasts is fine as long as the podcast isn't in m4a format, or video podcast format. Is there a software in gnome that's capable of dealing with all of these?

---

### Post by sistoviejo on 2008-05-08
> **ben2talk said:**
> I'm having trouble too, using Rhythmbox for podcasts is fine as long as the podcast isn't in m4a format, or video podcast format. Is there a software in gnome that's capable of dealing with all of these?

I too am looking for an application that can subscribing to video podcasts and copy them to the ipod.
Rhythmbox is able to subscribe and copy only AUDIO podcasts. 
Even though it does download the video podcasts, it tells you that the download has failed and it's unable to copy the video podcasts to the ipod.
After downloading the videos with rhythmbox I was able to copy them to the ipod using gtkpod. 
You have to install the gtkpod-aac not the gtkpod package because the gtkpod package is compiled without video support.
Sadly gtkpod doesn't understand what a video podcast is, and copies the podcasts as if though they were movies. 

Has anyone found an app that can subscribe to video podcasts, download them and then copy them to the ipod? (as podcasts)

Right now I am installing hpodder, gPodder, banshee and hipo using the package manager. Almost all of these are able to manage podcasts and ipods so I will try again with these and update this post with results.

UPDATE: 
banshee didn't know there was an ipod plugged in.

SUCCESS!!! 
I was able to subscribe and download video podcasts and then copy them to my ipod. The winner is gPodder!
You can install it using the package manager.
After installing gPodder I ran it and went to Podcasts>Preferences. 
Then click on Player, choose iPod and enter the right mount point folder where the ipod is mounted.
When you try to send podcasts to the ipod gPodder will ask you to install the packages python-gpod and python-pymad. 
After installing these you should be able to transfer video podcasts to your ipod.
The video podcasts will be tidily put in the podcasts section of the ipod.

For all these tests I used Ubuntu 8.04 Hardy Heron

---

