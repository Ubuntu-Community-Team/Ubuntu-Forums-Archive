---
title: "creating a home/development http server"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by yamokojc on 2005-11-09
as a side project/hobby i like to design and develop websites. so, i would like to create a server on my home network that i can use as a development server to test websites and what not before i send them to a live server.

i think i pretty much have that figured out though...all i need to do is install and configure apahce, right?

i would also eventually like to take this server live to have a place where my family can connect and share files and what not. obviously i am going to need a bit more than just apache. i assume that i will need to run DNS somehow? i have heard of DynDNS but i am not exactly sure how it works.

i know that this thread is very vague but that is b/c i am not totally sure what to ask. so i am opening this though hoping that it will spark some more questions/answers and develop into a good helpful thread.

i am running Ubuntu 5.10

---

### Post by Joe_lurker on 2005-11-09
> 
i think i pretty much have that figured out though...all i need to do is install and configure apahce, right?
This is correct.  However to unleash the full power of Apache you should really get a good book.  I learned Appache from using a book called "Apache" by Wrox Press.  I would look for a newer version.

As far as making your server public first you need to know whether you have a static or dynamic IP address.  If posible you should get a static IP address.  You need to ask your ISP how to get one.  As far as DynamicDNS you should look for a router that supports it.  My DLink does but I have never used it.  If your computer is set up directly to the internet (bad idea running a server) then there is software to automatically inform the DynamicDNS server of your ip address changes.

As far as sharing files you might want to consider WebDAV.  It is supported by Apache via a module.  You can secure it and use ssl to encrypt it.  That is how I syncronise my Firefox bookmarks!.

I hope this helped a bit.  Maybe it will start some ideas for you.

-Joe

---

