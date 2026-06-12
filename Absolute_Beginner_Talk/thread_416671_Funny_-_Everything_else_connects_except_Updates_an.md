---
title: "Funny - Everything else connects except Updates and Downloads"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by maxlinux on 2007-04-21
Hi everyone

I am a relative noob to Ubuntu. I downloaded the ver 7.04 - Very pretty.
I installed it on my Dell system (3.0 gig, 1 gig ram, 128 Intel onboard VGA) at work and works like a charm.

One problem though. I am running a proxy network with proxy authentication at the office through a linux server with squid and samba
I having entered all the proxy settings for internet. synaptic package manager (with authentication under the adavanced tab) etc.
Everything works  - internet, mail, I can even connect to my server and acces all my directories (Server uses Samba). Only thing is that as soon as I try to do updates or download packages ie. beryl and others I get a the error "407 proxy authentication required" error

I even tried forums from various places including other linux based os' (mandriva, suse etc.) for an answer.
I also tried editing config files adding lines "http::proxy "http://username:password@ip:port" commands but everytime i try to use it it tells me there is junk lines in the file. Am i missing something, tried variations on the command. Must I maybe add the domain (Even though it is a linux server) to these lines.

I also had the same issue on unbuntu LTS, but due to time contraints I was not able to try and solve it at the time. (As i am my companies IT manager as well. Did not setup the original linux server box though)

I would like to do a Demo for the big wigs at my organization to  show that Ubuntu should not be the alternavtive but the norm. For every  package that I run on other windows based systems I found a linux alternative :) Including even my phone and database systems.
(Added - everything was setup and downloaded on my home adsl - no proxies etc. issues)
This is one of the few issues I have left that i am aware of (other 1 is a beryl issue)  and would really like to break this one. 

Thanks for reading all my ramblings and hope someone out there can help me. :)

---

### Post by solarix on 2007-04-24
> **maxlinux said:**
> Hi everyone

I am a relative noob to Ubuntu. I downloaded the ver 7.04 - Very pretty.
I installed it on my Dell system (3.0 gig, 1 gig ram, 128 Intel onboard VGA) at work and works like a charm.

One problem though. I am running a proxy network with proxy authentication at the office through a linux server with squid and samba
I having entered all the proxy settings for internet. synaptic package manager (with authentication under the adavanced tab) etc.
Everything works  - internet, mail, I can even connect to my server and acces all my directories (Server uses Samba). Only thing is that as soon as I try to do updates or download packages ie. beryl and others I get a the error "407 proxy authentication required" error

I even tried forums from various places including other linux based os' (mandriva, suse etc.) for an answer.
I also tried editing config files adding lines "http::proxy "http://username:password@ip:port" commands but everytime i try to use it it tells me there is junk lines in the file. Am i missing something, tried variations on the command. Must I maybe add the domain (Even though it is a linux server) to these lines.

I also had the same issue on unbuntu LTS, but due to time contraints I was not able to try and solve it at the time. (As i am my companies IT manager as well. Did not setup the original linux server box though)

I would like to do a Demo for the big wigs at my organization to  show that Ubuntu should not be the alternavtive but the norm. For every  package that I run on other windows based systems I found a linux alternative :) Including even my phone and database systems.
(Added - everything was setup and downloaded on my home adsl - no proxies etc. issues)
This is one of the few issues I have left that i am aware of (other 1 is a beryl issue)  and would really like to break this one. 

Thanks for reading all my ramblings and hope someone out there can help me. :)


Ok, your Problem seems to be... The Proxy Server expects authentification from you´re Computer. When APT the Package Manager starts. The Proxy would not be informed about you´re Identification. And close´s  the Way out.

Do the following. Inform you´re Administrator about this Problem APT had severeal Problems with Proxy´s in the past. At the Moment i´m Short in Time, and it´s only a Hint.

fingers crossed

Solarix


EDIT:

what i´ve done on my Debian Box at my former Company that might help you:

```
 
export http_proxy=http://thereshouldbetheproxyname:theproxyport

```

That should work for you to :)

But exporting the http Proxy Parameters on the Terminal is a temporary Method no permanent Method. Please don´t forget.

I´m quite sure you need a permanent Procedure  there is a method to make it in /etc/apt/apt.conf  

but in the Moment  i forgot it. I wil look after it, when i have the time.

Cheers

Solarix :)

---

### Post by gwm on 2007-04-24
Hi,
I also had proxy issues with dapper. Here's how we fixed it.
Go to the end of the rather lengthy thread to get to the bottom line.

[http://ubuntuforums.org/showthread.php?t=380086](http://ubuntuforums.org/showthread.php?t=380086)

:popcorn:

---

### Post by maxlinux on 2007-04-24
Thanks for the reply Solarix.

I played around with it some more and actually got it to work. I must have done something weird, cause after I did what ever I did,  I selected "direct connection" instead of Proxy Settings  in Synaptic and it started downloading the updates. Everything else still works the way it did, even asking the security clearance to access my servers etc. (Still set to Proxy etc.)

It works, but will be digging a bit deeper as soon as time allows :-) Untill then I am just glad it works.

---

