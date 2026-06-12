---
title: "external hd issue"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-11-01
[COLOR="Indigo"]Hey y'all! I'm hoping someone might have a quick solution for an issue I'm having with an external hd. When it's hooked to my windows machine I end up with a lot of crc issues. I've run CDCheck on it a few times and it comes up with random win32 errors, not always on the same files. I've read that it could be a possible windows or cable issue as opposed to the hd actually being dead. So I hooked it to my Kubuntu machine and it pops up Unmountable Media Type. So I clicked on Open in New Window. And then it pretty much vanishes. Doesn't show up in my media menu or anything?! Any ideas on what to try so I can access the info on it? Thanks much!! [/COLOR]

---

### Post by cmnorton on 2007-11-01
When you say external drive, do you mean USB? From the windows side, this sounds familiar. What version of USB is on the motherboard? What are win32 errors, delayed write?

---

### Post by andyho on 2007-11-02
Yes it's a Maxtor 2.0 USB drive... ntfs file system, no partitions.. The only error I get on the win box when it's plugged in is a crc error. I'm mostly just trying to get some photos off of it and whenever I try to access them from photshop it tells me they're "trunciated". 

I messed around with trying to mount it on my kubuntu box last night and had it mounted for a brief moment, but whenever I tried to access it, it told me I didn't have permission. I checked the setting with ntfs-3g and they were fine.

Now though I've forgotten how I got it mounted! Grrr.. I just want to mount it so that I can see if it's a Windows issue or if the hd is fried. Hopefully I can get the info off of it I need!!


**UPDATE**
I have it mounted.. but here's the error I'm getting now...

Unable to enter file://media/sdf1. You do not have access rights to the location.

---

### Post by cmnorton on 2007-11-03
First, if you're getting CRC errors, I'd dismount the disk and dd everything off it to a safe place. 

As far as the error message you got, it sounds like the external drive was not mounted with the proper permissions.

---

