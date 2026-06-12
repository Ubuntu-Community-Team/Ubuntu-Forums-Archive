---
title: "I'm Excited!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by rhardie on 2007-04-23
I am a recent convert to Linux and Ubuntu and run a business as well as a fairly serious photography passion.

I have been experimenting with Ubuntu and how to run my business on Linux.

So far I have loaded 7.04 onto my AMD Athlon system, synched Evolution with my IIS Exchange Server and can do all my word processing, spread sheets and presentation slides from Ubuntu.

I do need to find ways to run vitual machines via VM Ware for my industry specific applications ( and there is only ONE show-stopping software I use).

My next phase is to learn how to substitute my IIS server for something Linux.

I have the core application running on the IIS server and then a client that runs remotely by [https://domainname.com/application](https://domainname.com/application) name.

Does anyone know how I can replicate the same functionality in Linux or how best to approach this?

My software application won't run on Linux without a virtual machine and it appears to not work with WINE according to the tech support people.

Thanks in advance,
rhardie

---

### Post by pppetter on 2007-04-23
I don't really get it - why do you need a windows virtual machine to run a web application? 

if the web application only runs with Internet Explorer, just install IE with [IE4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"). It works lilke a charm.

If this doesn't help you go ahead and install VMware player.

---

### Post by rhardie on 2007-04-23
The application itself is hosted on my server and will only run on Windows.  The IIS functionality allows me to go over the internet and use/communicate with a client version of the same software - which still needs Windows.

I'm scratching my head trying to figure a way to not use the Windows IIS server, but I guess since I must have Windows to run my application, then there is no real point in attempting to use a Linux server with VM Ware.

My software application also runs MSDE, come to think of it, . . . hmmm . . . .  but it can run SQL . . .so I wonder if it could run MySQL?  Have to check that out.

I'm open to thoughts and ideas from the Ubuntu collective consciousness..

Thanks

---

### Post by rhardie on 2007-04-23
Actually, the IE4Linux was a good suggestion since the software vendor will provide a web-browser based version - I just have to give up control of my client database and synchronization with my email client.

I didn't yet know of IE4Linux and you answered one of my next questions.

Thanks again.

---

