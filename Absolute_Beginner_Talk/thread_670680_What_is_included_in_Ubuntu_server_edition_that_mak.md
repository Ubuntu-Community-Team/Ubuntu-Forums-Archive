---
title: "What is included in Ubuntu server edition that make it server edition?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-17
Hi
Thank you for reading my post
Can you explain what software or optimizations are included in ubuntu server edition that is not available in ubuntu desktop edition?

Thanks.

---

### Post by SOULRiDER on 2008-01-17
The server one doesnt have a GUI. The server edition comes by default with packages youre going to use on a server like for example Aache.
The desktop edition comes with software you'll want in a desktop, the server edition comes with software you'll want on a server.

---

### Post by corvusdoro on 2008-01-17
can you add a gui to the server edition?
or is it easier to add the LAMP functionality to a desktop ubuntu?

Thanks

---

### Post by SOULRiDER on 2008-01-17
You can add a GUI yes. I really dont know what would be easier to do, someone else will have to answer that. I build this system (with archlinux) from the bottom up and it wasnt really hard. I guess all you need is a good wiki explaining everything.

---

### Post by jjsonp on 2008-01-17
It's quite easy to add LAMP functionality to a desktop Ubuntu install; I just did it last week. It takes like 5 minutes via the Synaptic Package Manager.

Just go to System->Administration->Synaptic Package Manager, then look for Apache2, MySQL (make sure you ad the mysql-admin if you want that as it's not added by default), and PHP5. These will install all the necessary dependencies as well.

I installed MediaWiki (also in Synaptic) last week and it was unbelievably easy.

---

### Post by julian67 on 2008-01-17
> **legolas_w said:**
> Hi
Thank you for reading my post
Can you explain what software or optimizations are included in ubuntu server edition that is not available in ubuntu desktop edition?

Thanks.

kernel is optimised for server use

---

### Post by corvusdoro on 2008-01-18
Thanks for the answers.  Lets see if I can noob my way through.
:)

---

### Post by hyper_ch on 2008-01-18
what do you need a gui for on the server?

What do you want to do with the server?

And I'm not sure whether the kernel is optimized for a server...

---

### Post by julian67 on 2008-01-18
> **hyper_ch said:**
> what do you need a gui for on the server?

What do you want to do with the server?

And I'm not sure whether the kernel is optimized for a server...

The repos contain different kernels for server and desktop. Typical load on servers and desktops are different so kernels are set up differently. On a desktop *apparent* responsiveness (i.e. how fast gui apps take to launch/respond) is sometimes more important than what is going on in the background, whereas on a typical server those same "background" services/applications are the important ones. I guess a lot of this is done with the scheduler though am certainly no expert, I guess other parameters might be slightly differently set up too. As for using a gui perhaps the best compromise is a web based tool like Webmin....access the server from a desktop and manage remotely via browser while the server remains very light with no X server.

---

### Post by corvusdoro on 2008-01-21
> **hyper_ch said:**
> what do you need a gui for on the server?

What do you want to do with the server?

And I'm not sure whether the kernel is optimized for a server...

I want to set up mrtg to query a network of about 40 devices, so I started just looking at a server based solution.  But I'm just lost completely without a gui.  with a gui I am trying to ease the learning curve.

Thanks

---

