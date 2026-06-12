---
title: "Lost with ISP CONFIG and DNS"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by londonhelper on 2006-10-18
Well I have been all over - read all there is about DNS and bind - Read Howto forums etc - but still seem to be stumbling on something - but cant put my finger on it.

Here are my objectives but not sure if i am taking things further than i need and would really appreciate some help.

I have got a 123-reg domain - mywebspace.co.uk (here i am allowed to change everything on dns, nameservers, A records CNAME's etc.

I have a Ubuntu -server installation on my personal home machine (running at the moment as a virtual machine Until i get things right)

I have pointed my domain name to the external (static) Ip address of my router - 888.888.888.888 (for eg)
I have configure my router to forward ports on 8080, 80, 23, 21, 110, 10000 etc etc to the internal ip address (static)  192.168.1.10

My true intentions are : to have multiple webpages under my domain name : like - me.mywebspace.co.uk and mymate.mywebspace.co.uk and once i have email set up for [email]EVERYTHING@mywebspace.co.uk[/email] to goto a web login at say webmail.mywebspace.co.uk . (obviosly will have all the mail stuff set up according to the howtoforge guid on 6.06 perfect setup)

Now I am not sure if i need it but I looked and attempted to use ISPconfig but this seems to confuse me more.

The front end to it all - I would love to use the Joomla system (as i know how to ue it for a single web system) but not sure what i need to do to manage more than one webpage.

What is getting to me the most is DNS and nameservers etc. I have tried so many different things - but not sure how involved i need to be with the configs.

Do i need to have my own nameserver? ns.mywebspace.co.uk and configure the control panel at 123-reg to point my name server to this ns.mywebspace.co.uk and the (external or internal) ip address of it?

when i edit the /etv/hosts file - server1.mywebspace.co.uk - do i use 192.168.1.10 or the external ip address of my router?

do i need to edit or creater /etc/resolv.conf ? what do i need to put in there?

If i need to create a nameserver - what should i do? (they mention 2 name server are needed) but i have one server - what do i point to as the second server?

If i want to create a subdomain - webmail.mywebspace.co.uk - how do i go about doing it?

Once this has been fully explained and installed and working - It will then be able to look into it to understand it better.

Any help will be muchly apreciated -
cheers

---

