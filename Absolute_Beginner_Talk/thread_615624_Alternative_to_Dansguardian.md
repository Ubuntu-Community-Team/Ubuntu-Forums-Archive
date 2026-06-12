---
title: "Alternative to Dansguardian???"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by marianlibrarian on 2007-11-17
Is there anything other than Dansquardian for filtering? --- That works on Ubuntu 6.06 Dapper Drake??

---

### Post by marianlibrarian on 2007-11-17
I have to have filters. Sorry.

I am a librarian of a very small rural library with all public access computers using DApper Drake 6.06. I was able to purchase new computers for us with federal grants. One of the stipulations of using this money for new computers is that I have filters installed on them. If I do not, then I would lose all my computers, and I would not be eligible to apply for federal grants again. I also use this grant money to purchase children's books.

So if I sound frustrated - -  - I AM!

I just joined the dansguardian yahoo message board. One other person posted a message there asking the same question as me. He was basically told he shouldn't be accessing myspace anyway. That is NOT an answer.

Please, is there an alternative to Dansguardian??? 

I will pay for it!!!! I have to use CrossOver and they charge an annual fee and I am willing to pay that.

---

### Post by taurus on 2007-11-17
Besides Dansguardian, I've found Naomi, [http://www.radiance.m6.net/](http://www.radiance.m6.net/), and SquidGuard, [http://squidguard.mesd.k12.or.us/](http://squidguard.mesd.k12.or.us/).

---

### Post by por100pre1 on 2007-11-17
IMHO you should NOT put those grants at risk just because you are trying to access a "MySpace" page:

[http://ubuntuforums.org/showthread.php?t=615610](http://ubuntuforums.org/showthread.php?t=615610)

Try this [proxy]("http://www.myspacebypass.com/").

---

### Post by OldTimeTech on 2007-11-17
As a tech that was working for a school district, we were not allowed to let the children access any hotmail, yahoo mail, gmail or any of the social networking sites.  We had computers in almost every room, plus a lab and library....according to state/federal rules that was considered dangerous for intrusions and for the well being of the children.

---

### Post by mike555 on 2007-11-17
In my home network I setup all my computers to use " OpenDNS " servers , by just putting the numbers in the DNS setup ...... then tell OpenDNS to filter Porn ....... all my computers are now filtered ....... but a smart kid could use a proxy or set the DNS numbers differently (if they had the password)

---

### Post by marianlibrarian on 2007-11-17
It is very different being a "public" library versus a "school" library. I also have wireless access and that means that it is the owner of the laptop - chooses - to filter or not to filter. I should have been more observant in that Dansguardian is part of Christian Ubuntu. It worked great while it did but it doesn't look like there is going to be any chance of it going back to the way it was. Oh well, such is life these days.

I am here because with the access I did have to myspace, I had more teens coming into our library than had been seen since the sixties. Not only were they checking email and getting on myspace but were checking out books. I put a whole section of books just for them and the response was unbelievable. These are kids that have been exposed to 'no child left behind reading to pass tests" and now they know that they can pick up a book and read for pleasure. And several of them are reading books at a higher level than before. They know that when they finish the book there is no "test" that will follow. 

All of our computers are exposed to the public. By that I mean that anyone can see anything you are doing at any time. There is no physical privacy regarding our computers. Most of these kids have shown me their myspace pages and there were a couple of times when an account got the "you have tried to access a forbidden site" message. I explain - clean it up - if you want to access it in our library. Up until Dansguardian changed, they did exactly that, there were no more "forbidden access" messages. 

The easy thing to do would be to just give up and let the kids go to some other kids house that have no filters at all and access what ever they want and rest in the sublime NMP (not my problem) attitude. It would be real easy.

Anyway, I am going to take a look at the links given by the kind person earlier - thanks! A filtering application outside of a religious platform may be the proper alternative for a - public - library.

I won't jeopardize my grants for myspace. If I have to ban it then that is what will be done. However, something just doesn't feel right about this whole thing.

---

### Post by shane2peru on 2007-11-18
You can install Dans Guardian outside of Christian Ubuntu.  Matter of fact there is a way to setup a filtering server so Dan's Guardian is not even installed on the computers, just the proxy server that gives out the internet.  Here is the how to:  [http://taksuyama.com/?p=16#more-16](http://taksuyama.com/?p=16#more-16)  Also this link will tell you how to install DG. [http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)  if you just want DG without the Christian Ubuntu Distro.

Shane

---

### Post by marianlibrarian on 2007-12-10
> **taurus said:**
> Besides Dansguardian, I've found Naomi, [http://www.radiance.m6.net/](http://www.radiance.m6.net/), and SquidGuard, [http://squidguard.mesd.k12.or.us/](http://squidguard.mesd.k12.or.us/).

Naomi is only for windows. (useful information for public libraries that use windows)

SquidGuard is for linux. Installation is not for the nooBee. So I am reluctant to tackle it due to my horrible forays with dansguardian. 

But thanks for the information.

---

### Post by The Cog on 2007-12-10
Out of interest, what is the problem with Dansguardian? In what way did dansguardian change? I ask because I was vaguely wondering about implementing some content filtering.

---

### Post by marianlibrarian on 2007-12-11
It started this a few months ago. It allows you to access myspace.com and you can login fine and see your welcome login message with your login name. However, when you click on "home" page link, it says, "You have to be logged in to do that" just over your user name.

I have isolated it to dansguardian. I tried it on a machine with no dansguardian and the patron can log into their myspace account and click on the home page with no problems. I also tested it on a machine with dansguardian disabled and it worked then but as soon as I enabled dansguardian even with minimum filters it won't let the logged in user get to their home page.

I even removed dansguardian yesterday and reinstalled everything and I am still having the same problem. just weird.

---

### Post by The Cog on 2007-12-11
That sounds like maybe a cookie is being blocked. It may be worth trying this with Firefox (both with and without Dansguardian) and having a close look at the cookies that are set before and after the act of logging in. I'm guessing that maybe with DG active, a session cookie is not getting back to the browser. It shouldn't take long to try, and may hel set you on the right path for investigating further.

---

### Post by marianlibrarian on 2007-12-11
> That sounds like maybe a cookie is being blocked. It may be worth trying this with Firefox (both with and without Dansguardian) and having a close look at the cookies that are set before and after the act of logging in. I'm guessing that maybe with DG active, a session cookie is not getting back to the browser. It shouldn't take long to try, and may hel set you on the right path for investigating further.

That sounds interesting. How do you have a close look at cookies? :redface:

---

### Post by HermanAB on 2007-12-11
Here is an old, general purpose Squid-guard guide: [http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)

Cheers,

H.

---

### Post by shane2peru on 2007-12-11
Mirianlibrarian,

Here is a very nice alternative:  [www.opendns.com](www.opendns.com)  I have switched to it, and am very pleased with how it works.  I have setup a inadyn to automatically update my ip and keep any computer that connects through my network (even wireless) filtered.  For me it is better, because I don't have to get it setup on a few different computers, and because it is a dns (domain name server) it runs faster than a filter service on my computers.  If you need help setting up inadyn just ask, and I would be more than happy to run you through the process, it was quite simple.  You can even keep Dan's Guardian, while trying out or even setting up this new setup.  Also you can set it up on the router, so you don't have to mess with the individual computers.  Only one (probably the main computer) would need to be setup to update the ip address.  Check them out and let me know what you think.

Shane

---

### Post by marianlibrarian on 2007-12-11
>  		Mirianlibrarian,

Here is a very nice alternative:  [www.opendns.com]("http://www.opendns.com/") I have switched to it, and am very pleased with how it works. I have setup a inadyn to automatically update my ip and keep any computer that connects through my network (even wireless) filtered. For me it is better, because I don't have to get it setup on a few different computers, and because it is a dns (domain name server) it runs faster than a filter service on my computers. If you need help setting up inadyn just ask, and I would be more than happy to run you through the process, it was quite simple. You can even keep Dan's Guardian, while trying out or even setting up this new setup. Also you can set it up on the router, so you don't have to mess with the individual computers. Only one (probably the main computer) would need to be setup to update the ip address. Check them out and let me know what you think.

Shane

I just visited the site --- Thank you for this information. I will let you know how it works out. :)

---

### Post by The Cog on 2007-12-11
> **marianlibrarian said:**
> That sounds interesting. How do you have a close look at cookies? :redface:

Edit->Preferences, Privacy, Show Cookies

---

