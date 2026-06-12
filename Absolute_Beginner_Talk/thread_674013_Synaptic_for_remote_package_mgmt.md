---
title: "Synaptic for remote package mgmt?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kazar on 2008-01-21
I'm a recent arrival to the linux universe, at first by force of necessity (managing my own domain server vps) and am gradually just coming to like Linux. 

Now in the process of evaluating VPS hosting providers and flavors of Linux to host my several (very small) domains. Based on my research and on the recommendations of a trusted colleague, I'm leaning heavily towards Ubuntu.

So here come the newbie Qs:

**1. Can I install Synaptic on a local box and point it via a secure connection to my web server? If not, what are the options for remote package/installation management with Ubuntu?**

Since I need to get up & running quickly I will at least at first want to rely on the assistance of some utilities that run in a GUI, perhaps most notably Synaptic. My office is in one location and my web server (VPS) is in a distant city.  If remote use of Synaptic is not possible, would my only choice be to use apt (or alternate cli flavor) on the CLI via ssh? I do not have a predictable public IP address in my office and do not wish to configure VPN that is left accessible to the whole world and therefore cannot use any GUI apps directly on the server.

(I could not find info on this question -- the synaptic pages at [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/) do not have any end-user docs I could find, happy to RTFM if someone can point me to it! I see in screenshots there is a Help menu but I do not wish to build a linux box and install just to see the docs for Synaptic, I'm hoping a pdf or textdoc or html version exists somewhere)


[B]2. Easy/possible with Ubuntu to set up a test server and upload changes to production server?
[/B]
Because I'm still taking my baby steps (still cringe every time I chown or rm!!) and my sites will have live published content and (I hope) a readership, I can't afford to muck up the live server. Is it possible to set up everything on a local box as my test server, and when I'm satisfied that any new install or mods have gone ok, somehow upload the local server to the test server, or do I need to re-do installations, configurations, user accounts, whatever on the live server? If it is possible to "clone" (if that's the right word) one server to another, is there a tool to assist in uploading only what has changed?


thanks in advance!

kazar

---

### Post by jd65pl on 2008-01-21
You could use tunneling over ssh to enable you to use GUI's over ssh, you will have to enable this on the server tho. Then connect to the server with the command below.

```
ssh -X user@hostname
```

---

### Post by jd65pl on 2008-01-21
[This ]("http://ubuntuforums.org/showthread.php?t=302525")should help.

---

### Post by kazar on 2008-01-22
thanks much jd*

i had tried doing my homework before asking but had searched using the word "remote" which does not appear in the thread you referred me to.

so it looks like remote use of Synaptic is possible which is what I needed to know [but at a cost (connection speed cost, that is)]. I may find myself just sticking with the CLI on my new VPS anyhow, reason being that I thought I would need the Plesk CP my ISP had installed on my current (CentOS)  VPS  since i'm a beginner, but I've quite soon come to the conclusion that using CPs like Plesk --

-- creates a directory structure in some ways unlike the ones that will be discussed in tutorials

-- eats up a boatload of RAM (of my precious 512MB guaranteed)

-- quickly becomes like stuffing lots of furniture in a dark room, i keep bumping into Plesk and barking my shins

:-)

so if remote Synaptic doesn't do it for me, I'll learn apt*

thanks again,

kazar

anyhow,

---

### Post by jd65pl on 2008-01-22
You need to read the thread, it will tell you how to get a synaptic gui from one computer by logging into in on another. apt isn't difficult to learn at all you should have no problems with it.

---

