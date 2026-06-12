---
title: "Potential EGroupWare User w/ Questions"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-09-24
Hi All

I posted this on the EGroupWare forums and got no response so I figured I would post it here and at least get opinions from others who have used it.

> Hi All

I'm new to Linux and considering using e-groupware but I have some (probably) dumb questions first.

1. How hard is it to install and setup? It seems easy but there are so many features and so much administration I can't imagine it's as easy as it seems.

2. How secure is the program since it opens up access form the internet? I have a firewall and virus check but I like to be safe.

3. When I was using M$ I was syncing my Palm with Yahoo through Intellisync and using Zoho for online document editing/storage. This is what originally led me to find e-groupware. How hard is SyncML to setup?

3.A. Does SyncML sync over the internet? or is it a local sync utility? I'm having trouble understanding the work flow of the program.

3.B. It seems that if I want to sync my Palm I need another program called Synthesis, is that right?

4. What port do these programs run on? I know (from setting up an FTP server) that my ISP blocks ports up to about 1500. That being said, in the past I've just used a port number higher than that.

I guess I'm trying to get a handle on how much work it's going to take to set the program up and then how much work it's going to take to admin. I have written some small programs before and have done a fair amount of web programming so I'm not afraid (or unable) to do the work so please be honest (but gentle) with me.

Thanks,

Any feedback will be much appreciated. I've read more about SyncML and it seems like it's a program for the Palm, which allows it to sync via the internet? I cou be wrong in my interpretation of that though.

Thanks,

---

### Post by High Camp on 2007-09-24
Anyone?

---

### Post by djchandler on 2007-09-24
> **High Camp said:**
> Anyone?

I don't use egroupware, but there's a wiki for it that you can install via synaptic.
Surprising you got no help at egroupware.org. I doubt that many here use that suite, but I could be wrong.

Also, there's kdepim-wizards. Try installing and running that after you've installed the whole package. Sounds as if you are better supported using Kubuntu.

> KDE server configuration wizards 
This package contains KDE-based wizards for configuring eGroupware,
Kolab, and SUSE Linux Openexchange servers.

This package is part of the official KDE pim module.DJ

---

### Post by djchandler on 2007-09-24
The website indicates it integrates nicely with evolution or kontact as well as either firefox or Konqueror. The way I read it, it should be totally platform independent, so your support should come from eGroupWare. 

Are you trying to set up servers? See my previous posts about wizard in KDE (Kubuntu).

---

### Post by High Camp on 2007-09-25
Hey DJ

Thanks for the reply's. I've seen a couple posts on here about EGroupWare so that's why I figured I would give it a shot. I'll try again on their forums.

The info you provided was very helpful. 

Ultimately what I'm tyring to do is set up a server at home that I can sync my Palm to and then access the calendar, addresses, notes, and tasks online. I don't care if I sync via a network or locally. The reason I chose this program is because it looks like it has some cool file management tools and collaboration tools as well.

So thanks again,

---

### Post by earth_walker on 2007-10-03
I've been testing various groupware solutions, including egroupware (and phpgroupware, which seems to have many more bells and whistles, but didn't feel as robust). I tried reading about this stuff, but in the end trying it was much quicker and more useful than the outdated and sometimes wrong info on the web.

Anyway, when you install using apt-get, it creates all of its folders in /usr/share/egroupware/. You must move these to (or make a link to them from) /var/www/egroupware/

Then point your browser to localhost/egroupware/setup and the php scripts will let you set everything up on your test system and play with it.

---

### Post by High Camp on 2007-10-04
Howdy earth-walker

Thanks for the reply. I have downloaded it and gotten to the setup page but have not gone further than that simply due to a lack of time.

Have you looked into syncing a Palm device with it? The whole Palm setup sounds overly complicated and complex.

Let me know how it goes,

---

### Post by psycho78 on 2007-11-01
Hi I also use eGroupware and also set it up for our small firm (20 users)... It works quite nice, but i have not found a good sync solution yet.. Even with Kontact under Kubuntu Gutsy I have several problems, e.g. double entries in the calender, etc...  

I read that there is a way to sync with palm (i have a treo650) with the funambol client.... but I did not get it to work yet.. unfortunately.... :( 
I also tried eGWO Sync for windows to sync with outlook for some of our users but that also did not work as i expected..... 

So if you can live with the web interface only, it is a real nice solution... 
Has anybody else got eGroupware to sync with some other devices / clients successfully?

It must be some kind of version problem (i have the latest eGroupware 1.4002 installed) and Kubuntu Gutsy 7.10... I read an article from a famous german online magazine where they obviously got it to work?
[http://www.pro-linux.de/berichte/kontact_egroupware.html](http://www.pro-linux.de/berichte/kontact_egroupware.html)

---

