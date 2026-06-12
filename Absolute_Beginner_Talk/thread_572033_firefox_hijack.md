---
title: "firefox hijack"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by mikesmith00 on 2007-10-10
When using firefox, anytime I go to my universities website, the site redirects me to a foreign travel site(invia.cz), and so I installed opera to see if I still was redirected, and it seems to only be in firefox.  Is there anyway to see where this redirect is from, or any way to repair it?  I like firefox better than opera, at least so far.  Thanks in advance for any help.  Also, what might've caused this, I was under the impression that linux was secure from attack, any chance of passwords being stolen?

---

### Post by kvonb on 2007-10-10
You could try deleting your .mozilla folder.

Run Nautilus (the file manager) and turn on hidden files, rename the folder .mozilla to something like old.mozilla, run firefox and see if that works.

---

### Post by allalogie on 2007-10-10
I'm curious about this as well. I'm running 7.04 and I've had a similar problem.
If I access the Reuters news site using Firefox, very occasionally it is redirected to a website  
PCoptimizer?. It only happens with Reuters.

*Run Nautilus (the file manager) and turn on hidden files, rename the folder .mozilla to something like old.mozilla, run firefox and see if that works.*

I looked for the mozilla file without success  :confused:


Just noticed, I've been reading this Forum for months now......and this is my first post :-)

---

### Post by mikesmith00 on 2007-10-10
It fixed the problem after I cleared the cache and deleted my user profile in firefox, although I'm still curious about the potential for password theft, whether or not I need to go through and change my passwords or not.  Thanks guys.

---

### Post by n3tfury on 2007-10-10
interesting.  first i've heard of hijacking on a linux box, but it had to happen at some point.

---

### Post by mikesmith00 on 2007-10-10
Yeah, I'm not all that sure that linux got hijacked, because I know I didn't input my root password anywhere.  It seemed like possibly a javascript exploit in firefox, my schools website is flooded with javascript and flash.  Anyway, I'm trying to recreate it now that I know how to fix it, so I can notify whoever is in charge where I got nailed.

---

### Post by Seisen on 2007-10-10
Install Noscript add-on for firefox.

[https://addons.mozilla.org/en-US/firefox/addon/722]("https://addons.mozilla.org/en-US/firefox/addon/722")

---

### Post by Romin-1 on 2007-10-10
Just a thought; I would look around the website and see if one of the advertisers is the one you are being redirected to. If so, notify the webmaster of the site that the adserver is redirecting/hijacking thier site. 

As I said, just a thought,

Jon

---

### Post by mikesmith00 on 2007-10-10
I installed noscript, and that was what allowed me to see that it wasn't the site being hijacked, it was something on my computer, although all of the functionality on the site as far as accessing my university email, registering for classes, etc, all opens windows with javascript, so noscript wasn't a complete solution for me, because if I disabled it and changed nothing else then I might still be redirected.  I still haven't been able to come up with how it happened, hopefully I'll figure it out sometime tonight, because I'd like to be able to repeat it, so I can notify the proper people to get it fixed.  Thanks though.

---

### Post by kvonb on 2007-10-11
mikesmith:

What is the address of the page you are trying to reach?

Maybe a few people could try it and see what happens.

It might be a DNS issue, when an address is not found, certain scumbag DNS providers automatically redirect you to some moron that is paying them money.

It could be on your server (if you are doing your own DNS), or maybe your ISP's DNS server.

You could try changing your DNS server to a public one, here is a list:

[http://www.tech-faq.com/public-dns-servers.shtml](http://www.tech-faq.com/public-dns-servers.shtml)

Just go into system-network and change your DNS server to one of those, see if it makes a difference.

---

### Post by handy on 2007-10-11
> **allalogie said:**
> 
***Run Nautilus (the file manager) and turn on hidden files, rename the folder .mozilla to something like old.mozilla, run firefox and see if that works.***

I looked for the mozilla file without success  :confused:


Did you follow the instructions & turn hidden files on?

After that you will see a lot of new files that were hidden, with their first character being a dot "." .

***/home/handy/_._mozilla*** 

Is where my ***_._***mozilla lives, yours should be similarly located under your user name. 

I know that this may not have anything to do with the problem that you are experiencing, but it may hopefully help you understand why you can't find .mozilla... :-)

---

### Post by Paulmd on 2007-10-11
> **mikesmith00 said:**
> It fixed the problem after I cleared the cache and deleted my user profile in Firefox, although I'm still curious about the potential for password theft, whether or not I need to go through and change my passwords or not.  Thanks guys.

As a precaution, I would consider all the passwords you have ever used, or entered on that machine as potentially compromised. It would be prudent to change them.

It would be a mistake to presume that Linux is somehow hijack-proof. There is a small handful of known Linux viruses. Mostly proof of concept. This is not by any means a definitive list:

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

One of these days, there's bound to be a major virus outbreak in the linux world. The more popular Linux gets, the bigger, and more tempting target it becomes. Judging by the stream of security updates, Linux, and various Linux libraries, still have plenty of unpatched security holes in it. 

The gist of this is that having Linux is not in itself perfect security. Many um... Lin-vangelicals may have you believe so. But it simply isn't true. the user must still be vigilant.

---

### Post by handy on 2007-10-11
Apple on BSD, still doesn't have any problems, my wife runs OS-X & uses the net a LOT, as do I on various *nix based systems, I don't use any anti-virus software, & if I'm running Ubuntu I play around with the IP Tables, just because its so easy.  I'm most concerned with my privacy i.e. being tracked on the net, not with having passwords, data or my bandwidth hijacked.  So on rare occasions I turn on TOR, to make it difficult for anyone to track me.

I'm not going to get paranoid about what might happen in the future, if things change, so will I.

---

### Post by allalogie on 2007-10-12
*I know that this may not have anything to do with the problem that you are experiencing, but it may hopefully help you understand why you can't find .mozilla... *

Thanks for that. I've found it now.:)

FWIW, I already had Firefox set up to clear the cache etc automatically. 

I don't know whether this means anything, but the problem arose after I had added the Reuters news site as an Addon to my Google homepage.
Ocassionally, if I clicked on a news item, It would be redirected to PCoptimizer,com?. If I clicked to close the window, it would return to my desktop. If I tried again, it was generally ok. I suppose it happened about 10 times all told, the last being about 2 weeks ago.

Since l posted, I have loaded Noscript, and cleared the cookies, but have'nt done anything else.

I'm currently dual booting my laptop with 7.04/ XP (although I have'nt used XP for weeks).

I'm loathe to make any changed over the next few days as I'm changing my broadband ISP on monday. If it all goes to plan (some hope :)) I was going to load the whole laptop with Gutsy after 18th.

Just wanted to say how much I have appeciated  all the input on the  Ubuntu forums.......
especially regarding commands in the terminal. For me, it is still a case of monkey see, monkey do :)

Cheers

---

### Post by handy on 2007-10-12
> **allalogie said:**
> *I know that this may not have anything to do with the problem that you are experiencing, but it may hopefully help you understand why you can't find .mozilla... *

Thanks for that. I've found it now.:)

FWIW, I already had Firefox set up to clear the cache etc automatically. 

I don't know whether this means anything, but the problem arose after I had added the Reuters news site as an Addon to my Google homepage.
Ocassionally, if I clicked on a news item, It would be redirected to PCoptimizer,com?. If I clicked to close the window, it would return to my desktop. If I tried again, it was generally ok. I suppose it happened about 10 times all told, the last being about 2 weeks ago.

Since l posted, I have loaded Noscript, and cleared the cookies, but have'nt done anything else.

I'm currently dual booting my laptop with 7.04/ XP (although I have'nt used XP for weeks).

I'm loathe to make any changed over the next few days as I'm changing my broadband ISP on monday. If it all goes to plan (some hope :)) I was going to load the whole laptop with Gutsy after 18th.

Just wanted to say how much I have appeciated  all the input on the  Ubuntu forums.......
especially regarding commands in the terminal. For me, it is still a case of monkey see, monkey do :)

Cheers

The Linux based learning curve loops the loop at the beginning for those of us who migrate from windows, I know. :-)  It doesn't take all that long & windows seems like such a strange land to visit, which is cool.  & this magnificent forum is just a lifesaver, I've not found one to compare with it on any subject. 

Regarding your plans to upgrade to Gutsy on the 18th, if I were you I would just hold back a little, watch the forums & see where the problems are, to try & be sure that you are not stepping into a mess due to any hardware incompatibility issues.  There have always been problems with new releases, sometimes things that worked in previous versions of Ubuntu no longer do, which of course causes much consternation amongst those affected! :lolflag:

I will be putting Gutsy on my 2nd machine, so I won't be crippled by any problems that may arise.  I find the best attitude is to expect problems, then you never know, you may be pleasantly surprised to find that there are none! :)

---

