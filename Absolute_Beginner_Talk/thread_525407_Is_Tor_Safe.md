---
title: "Is Tor Safe?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by edwin.e.johnson on 2007-08-14
hello i am having a problem... yesterday i installed tor. used it for about 6 hrs. with firefox gaim and xchat

today i wake up connect to the net open gaim and irc all that... start surfing and whatnot about 10 min pass and i get a msg from gaim via my aim.. saying i had just connected from another location.

weird thing is this is a brand new aim account. maybe a 2weeks old. i have never connected to if from any other computer and have not used any other program except gaim. my password was seriously ridicules so i know it wasn't guessed. 

does anyone know if the people hosting the tor exit nodes can collect your packets and data as it passes through them?

---

### Post by Tomosaur on 2007-08-14
> **edwin.e.johnson said:**
> hello i am having a problem... yesterday i installed tor. used it for about 6 hrs. with firefox gaim and xchat

today i wake up connect to the net open gaim and irc all that... start surfing and whatnot about 10 min pass and i get a msg from gaim via my aim.. saying i had just connected from another location.

weird thing is this is a brand new aim account. maybe a 2weeks old. i have never connected to if from any other computer and have not used any other program except gaim. my password was seriously ridicules so i know it wasn't guessed. 

does anyone know if the people hosting the tor exit nodes can collect your packets and data as it passes through them?


On the time when you received the 'you connected from another location' message, where you actually using Tor then? It could simply be a conflict between some Tor servers - the way it works is basically via proxy (although it's a bit more complicated than that). Your data is encrypted and then sent through the internet via lots of different servers - the end result being that it is incredibly difficult, if not impossible, for someone to trace you and build up a profile of your internet usage. It is theoretically possible that you got logged in 'twice' - TCP (which is how your computer sends packets of information) keeps track of lost packets and asks for them to be resent. Given the complex nature of Tor - it's entirely possible that some server somewhere didn't get a particular packet, so it asked the previous server to re-send the information. The upshot of this is that the server which gaim uses may have received your log-in information twice from two different servers, and thus sent you the 'you logged in elsewhere' message. In reality, something like this is most likely what happened, and it's just one of those quirks of the internet. Another possibility is that even if you weren't using Tor, the same thing just happened on the Gaim servers. It's just one of those things you have to put up with given the distributed nature of the internet. There are so many possible points of failure that it's very hard to say for sure what happened, but I'd say that the **least** likely situation is that someone really did find out your information and log in. What would they have to gain by doing so?

EDIT: You may wish to read this too: [http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#ExitEavesdroppers](http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#ExitEavesdroppers)

---

### Post by edwin.e.johnson on 2007-08-14
thankyou for the info. i was reading not to long ago on the net that people are conifuring there computers as tor exit nodes and collecting packets is this possible?

---

### Post by Tomosaur on 2007-08-14
> **edwin.e.johnson said:**
> thankyou for the info. i was reading not to long ago on the net that people are conifuring there computers as tor exit nodes and collecting packets is this possible?


Yes. The only way you can ever be 'safe' on the internet is by encrypting sensitive information. The most common way to do so is to enable the 'use SSL' option in any software you use on the internet. The problem, however, is that not all software has this option, so if you can't find the option to enable SSL in your software's settings, then you should check out the software's documentation. If you can't find 'SSL', then look for 'TLS', because they're basically exactly the same thing with different names. If you can find neither of these, and your software offers no other way of encrypting the information it sends over the internet, then it's time to find a different program!

If every single connection you use is inside a Tor network (That means your computer, the server you ultimately want to send info to, and all the servers in-between), then this shouldn't be a problem - but of course, you'd be fairly hard pushed to find such a network, and even then it's completely out of your control - one of the servers could go down and the traffic may be forced to leave the Tor network and find a new path. The **only** solution at the moment is to encrypt sensitive information such as passwords and whatnot. It's not really a problem with Tor - people can still get your information by other means even if you don't use Tor, it's just that Tor gives the kind of people who would do such a thing another tool with which to do it.

Only use software which gives you the option of encrypting your information (some do not give you the option, but have encryption turned on by default, which is why you need to read the software documentation if you can't find any option to turn encryption on).

---

