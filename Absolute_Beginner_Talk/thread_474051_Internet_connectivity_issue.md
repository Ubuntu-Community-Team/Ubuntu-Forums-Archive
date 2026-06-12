---
title: "Internet connectivity issue"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by bgamble on 2007-06-14
It's not that I have no connectivity...  I can get to sites like Google and gmail, but other sites, i.e. thedrudgereport.com, or even the update site sit, and sit some more with the "waiting for...(insert web site here"... message at the bottom.  Any ideas?  I can't even update!

Just installed Dapper Drake on an x86_64 system I built a few months back.

Vista (spit)... has no problem accessing through my cable modem and a Linksys WRT54G.

On another note...  I have a Viewsonic 20" widescreen with a native resolution of 1280x1024.  The resolution is set right, but all of the icons and the text seem to be stretched.  Any ideas on that one?

Oh yeah, I'm pretty much a complete newbie to Linux.  I've played with it a bit, but not much at all.

Thanks,

B.

---

### Post by netwerx on 2007-06-14
i would check your drivers for your network card.
i had a similar problem with a 64 bit version.

To be honest, i eventually went back to a 32 bit version, and have been far happier ever since.

---

### Post by bgamble on 2007-06-14
Just tried to update my video card driver via apt-get and after some time got a reply of connection failed  E: Unable to fetch some archives.

b.

---

### Post by bgamble on 2007-06-14
How can I tell which version was installed?  I just ran the DVD that came with the book I picked up today.

---

### Post by Brightbelt on 2007-06-14
Hi,
It sounds like you are actually not connected and you're getting a few site pages from your reserved internet files.  Firstly, are you on wireless or ethernet cable? I can't quite tell from your description - you mention both a cable modem and a wireless router. 

Also, if you have a 20" monitor and your icons are stretched, it's probable that your screen resolution is actually still too low. Check and see what it is in Vista (right-click on desktop/properties/display etc); put it to the highest setting (all the way to the right) in Vista and see what that is.   

I'm not an expert on this but a 20" monitor may call for a 1650 x 1080 screen resolution. If so, and if you don't have that high of an option in your screen resolution selection, you'll need to make sure your graphics driver is completely installed. I don't know if this will work on Dapper Drake (I'm on Feisty) but see if you can go to the System menu/Administration and select Restricted Drivers manager. Try to see or find out if you have an accelerated graphics driver that has not been installed. 

If you are going wireless, it may be that you simply have not configured your wireless card yet.  I don't know much about Dapper Drake, so I'm not qualified to help you here really.  I do think you can run this in your terminal to see what kind of wireless card you have: 
lspci

I hope this helps, ....Frank B.

---

### Post by bgamble on 2007-06-14
It's ethernet.  I use the wireless for my laptop which is still windows.

I don't think it would be saved Internet files since this is a new installation as of a couple of hours ago.  I checked my email from the connection. 

Also it tells me that I need to update, even lists the files.  Wouldn't there have to be some kind of connection for that?

B.

---

### Post by bgamble on 2007-06-14
Oh yeah, and I downloaded the latest driver for my video card from ATI on another machine, but I have no idea how to install it.

---

### Post by bgamble on 2007-06-14
If I can send and recieve email via gmail... Shouldn't I be able to download updates and new drivers?

---

### Post by bgamble on 2007-06-14
Anyone?

---

### Post by bgamble on 2007-06-14
Could really use the help...

---

### Post by jba6511 on 2007-06-30
same problem here. Did you ever get this resolved?

---

