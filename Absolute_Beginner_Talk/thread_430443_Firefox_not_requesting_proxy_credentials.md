---
title: "Firefox not requesting proxy credentials"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Simon2468 on 2007-05-02
I've recently built a Ubuntu laptop for the first time.  It installed without any problems and it's on my network.  Now I'm trying to use Firefox.

We have a proxy server which requires credentials.  I've used Firefox on my Windows box and when I try to reach the outside world, it pops up a box to get my credentials.  Using Firefox on my Ubuntu box does not pop up the creds window.  I've configured the proxy server in Firefox and I know the address/port is correct.

Any ideas?

---

### Post by mikeyphi on 2007-05-02
Does Firefox work - do you get access to websites?
If yes it could just be that you've left the 'remember passwords' active so you don't get to enter then every time?

---

### Post by Simon2468 on 2007-05-02
No, it doesn't work.  I get a page from the proxy server telling me I'm not allowed to see that site.

Having checked Firefox on Windows, I've realised that the page is similar but definitely different from the page I see if I cancel the proxy authentication window.  Now, why would that be....

---

### Post by PhotoJoe on 2007-05-02
Just an idea, but does the proxy server have MAC address filtering of any kind? That might explain why you're not even being prompted for your user credentials.

Also, am I correct in assuming that you are able to access other network resources  on the laptop without any problems?

---

### Post by steve.horsley on 2007-05-02
I can confirm that Firefox (on Ubuntu) is capable of asking for proxy credentials - we use a Microsoft ISA proxy at work. It pops up the usual username/password prompt.

One caveat - I have been using Firefox downloaded from mozilla.com, not the one that comes with Ubuntu. I know the Ubuntu version has introduced problems with javascript (hence having to use the original Mozilla version), so maybe they have busted the proxy authentication too.

---

### Post by PhotoJoe on 2007-05-02
Okay, now I'm confused. When Firefox (on Ubuntu) asks for proxy credentials, what exactly is it asking the proxy server? I think I've failed to understand how a proxy treats the machine (the problematicUbuntu laptop) versus how the proxy treats the user (Simon2468). In other words, do machine credentials (for lack of a better term) get submitted along with user credentials, or does the proxy look at the machine first?

In the words of Dr. Seuss, " I've puzzed, and I've puzzed 'til my puzzler was sore."

---

### Post by steve.horsley on 2007-05-03
I'm not sure of the details, but I thinkm in my case, the ISA responded to the first request with some kind og "authorization required" message which made the browser pop up a username/password dialog. I think the browser must have known this came from the proxy, because I was later able to log into other sites that also required passwords, so I reckon the browser must have then been sending two sets of username/password credentials.

---

### Post by Simon2468 on 2007-05-03
> **PhotoJoe said:**
> Just an idea, but does the proxy server have MAC address filtering of any kind? That might explain why you're not even being prompted for your user credentials.
I'm not sure - the proxy server belongs to another team.  Anyway, the laptop is plugged in using the cable from a (working) Windows PC and is using DHCP to get its IP address so that wouldn't make sense in this case.
> **PhotoJoe said:**
> 
Also, am I correct in assuming that you are able to access other network resources  on the laptop without any problems?
I haven't yet joined it to the domain and I'm too new to ubuntu to know how to access resources without doing that.  It can ping Windows servers.  If you can suggest a simple test, I can try it.
> **PhotoJoe said:**
> When Firefox (on Ubuntu) asks for proxy credentials, what exactly is it asking the proxy server? 
It's the other way round.  If you've got ISA Server as your proxy server and you're set up to use Integration Authentication, I believe you don't need to do an manual entering of credentials.  In our case, we don't have a Windows proxy server so we can't do Integrated Authentication.  In this case, what happens is you request a page using your browser.  The request gets sent to the proxy server which sends back a request via your browser to you to ask for your credentials.  You submit them and it authenticates you, checks that you have permission to access the internet and if you do, off it goes to fetch the page and return it to you.  At least, that's my understanding of the process.

Except that Firefox isn't asking for my creds.

---

### Post by steve.horsley on 2007-05-03
If it's an HTTP connection rather than HTTPS then you might gain a better understanding of what's going on by installing wireshark - a network capture and protocol analyser tool. I think that's what I would do next.

---

### Post by PhotoJoe on 2007-05-03
> If it's an HTTP connection rather than HTTPS then you might gain a better understanding of what's going on by installing wireshark - a network capture and protocol analyser tool. I think that's what I would do next

Excellent idea at any time. I'm still learning Ubuntu and Fedora but a good network analyzer can answer a lot of questions.

> I haven't yet joined it to the domain and I'm too new to ubuntu to know how to access resources without doing that. It can ping Windows servers. If you can suggest a simple test, I can try it

Join the domain if you can. I've no idea how your work network is set up but the fact that your laptop isn't known to the domain would explain a number of problems.

> I'm not sure - the proxy server belongs to another team. Anyway, the laptop is plugged in using the cable from a (working) Windows PC and is using DHCP to get its IP address so that wouldn't make sense in this case.

Talk to the proxy server team!! A two minute chat with them will probably point out something obvious that would be worth a thousand posts from me. Before unplugging the cable from the Windows PC, see if you can take it off the domain.Then try to join the Ubuntu laptop to the domain. It seems to me (and I might be full of it) that the servers in your domain are expecting to see a Windows work station and an Ubuntu laptop is popping up in its place. Anyway, talk to the proxy team- they will know the what/why/how of your  network and how to join the domain.   

Let us know how you make out....for better or worse. This problem has intrigued me and I'm curious to know what the 'correct' answer is.

Good Luck!

---

### Post by Simon2468 on 2007-05-04
> **PhotoJoe said:**
> Excellent idea at any time. I'm still learning Ubuntu and Fedora but a good network analyzer can answer a lot of questions.
Where would I get this?

> **PhotoJoe said:**
> Join the domain if you can. I've no idea how your work network is set up but the fact that your laptop isn't known to the domain would explain a number of problems.
I'm dealing with this one in a [different thread]("http://ubuntuforums.org/showthread.php?t=91510&page=10")!  I'm having problems and have had to rebuild once!  Maybe you can help: is there a different way to specify local credentials from network credentials, once you've set up (or part set up) network authentication.  Mine wasn't working and then the screen locked and I couldn't unlock it.

> **PhotoJoe said:**
> Talk to the proxy server team!!
Will do.  I've been out of the office for a couple of days so I was trying to gather as much info as possible before I'm back.  

> **PhotoJoe said:**
> Let us know how you make out....for better or worse. This problem has intrigued me and I'm curious to know what the 'correct' answer is.
Will do.  I make a habit of undating posts, even when I fix them mysef!

---

### Post by PhotoJoe on 2007-05-04
> Where would I get this?
Start [[COLOR="Red"]here [/COLOR]]("http://www.wireshark.org"). This is what used to be Ethereal which I used a lot in WinXP. It's on my Linux 'to do' list so I can't say definitively how it works with Ubuntu or Fedora. It works well in Windows.
> I'm dealing with this one in a different thread! I'm having problems and have had to rebuild once! Maybe you can help: is there a different way to specify local credentials from network credentials, once you've set up (or part set up) network authentication. Mine wasn't working and then the screen locked and I couldn't unlock it

I'll have a look at that thread but it will be a few days-I'm out of town for a few days.

Anyway, the proxy team still sounds like your best resource. Thanks for the updating- it's always great when a thread ends with a good answer to the question asked.

---

### Post by kingpoiuy on 2007-05-04
I am having this exact problem also.  Funny enough my Ubuntu 6.06 would work for browsing the web just fine with our proxy information put into the browser.  But 7.04 will not it gives me access denied!

Another thing.  Even when on 6.06 i could not use wget, apt-get, or synaptic.  I tried every forum i could find and no dice.  All i had was a web browser. 

I think if i can figure out how to get this thing on the domain it might help but I am still looking into that.

---

