---
title: "150 users in 45days + a server"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Abhi Kalyan on 2006-10-24
Problem-0010:
Creating Domain in Server:
How do we go about it
I had already installed/configured a windows server2003 to do this, but have no ides how its to be done in UBUNTU

1. WIll have 150 Clients running ubuntu in the next 45 days
2. Have a server running- on whihc am currently installing a GUI-UBUNTU desktop.

Can handle stuff like using apt, aptitude (etc)- This i suppose is very minor.
Can soome body gimme suggestions.
Note: Adding a Poll to see if the above is possible, Please do help by joining in.
Thanking you all
Love Abhi Kalyan

---

### Post by brentoboy on 2006-10-24
Depends on your definition of domain server.

What services do you honestly intend to have your server running?

make the list -- all of them -- post it here.

(dhcp?)
(cups?)
(file sharing?)
(router, filter, ...?)
(remote user authentication?)

Word to the wize, if you *love* active directory, and need its features in order to be happy, write out a big check to microsoft for 150 user server license and save yourself the trouble.  There are those who will tell you "if it can be done on windows... it can be done on linux"  And, as far as I know, they might be right, but some things arent worth the money.

If all you want is a file server... you could set the whole dang thing up over the weekend (with only a few cups of expresso)

---

### Post by Abhi Kalyan on 2006-10-25
Thank you brentoboy,
Thats sound advice.
You are absolutly right
all of the services whihc you had mentioned
Plus
LDAP, MysQL (etc) - The list is currently growing.
Frankly we might have 50 people accessing the server all the time.
The reast are spread out throught INDIA.
When We open VPN, Vidoe Conferenceing-These remaining people will also need to logon for user authentication.
Thats where we stand-
We might have made this big check, but thought not to do so as this did not seem to be the solution taht we were looking for. More over We prefer Linux to windows, So....
Thats about it.
Thank you once again buddy.
Sincerely Abhi Kalyan

---

### Post by brentoboy on 2006-10-25
Here is what I would do:

First, go to the book store, here are the titles you want in order of importance:

Ubuntu Hacks

The Official Samba-3 HOWTO and Reference Guide

Linux Quick Fix Notebook

and Samba-3 By Example

------------------
If your project cant afford the books, you need to abort mission ASAP.  You are in for a crazy ride, and even though these forums are helpful, you are going to need the advice from some really good books.

The last book up there (Samba by example) is the only one I would say is not absolutly necessary, I list it becuase it might give you a quicker start with samba, which will make the initial fealing as you get started give the project a euphoric lift -- that is always nice to have.

-------------------

Setup SAMBA first
Create 2 or 3 users, and 2 or 3 shares, and install ubuntu on 2 or three of the client computers.  Get a "happy" little network going.

Once you like them, you can roll out the client PCs as quickly as you want.

This is a weekend project.  When you are done, you will probably want to reformat all the PCs involved, and start over using the experience you gained doing it the first time.
----------------------

As far as all the other services go, add them one at a time, in order of importance.  DHCP is probably necessary  before you get too much farther.

The Official Samba-3 HOWTO book will sit by your desk for a few months, and you will need it every time someone calls and asks "Why does it..."  "How do I..."  (basically every day for a while)

The Ubuntu Hacks Book is the only book in the list that is specific to Ubuntu.  It has loads of advice, it should sit on your toilet.  Every time you "go" you should read a tip or two.  As the administrator of this whole thing, you need to know what your options are.  The book has lots of ideas that I would have never tried that are quite helpful.

The Linux Quick Fix Notebook is the one that will come in handy after you get past the samba hurdle.  It will help you set up all the other stuff you want.

Dont even touch LDAP until you have a working network in place that people like.  Then, (after your 45 day startup) when things settle down a touch, set up a new server with LDAP and add a handful of client boxes to that network until you really like what you have.  Then, roll that out to all the other PCs.

------------

There is nothing inherantly difficult in what you want to do, and there are lots of guys out there who could just do it.  But, if you want to do it yourself, and discover how at the same time, that takes time.  And, you are going to do some things that will come back and give you a headache.

The number of client PCs on your network will amplify your headaches until you have things smooth, which is why I recommend adding one or two new things at a time until you have it doing all that you need. Starting with the most critical and moving on to the "luxuries."

---------------

The biggest reason that I can see that will cause you to NOT finish within 45 days is that you still dont have a concrete list of exactly what you are going to finish in 45 days.

So, not only can I not judge how easy it will be to do it, you cant focus on your target until you know what it is.  And if you cant focus on a target, you will most certainly miss it.

-brent

---

### Post by lapsey on 2006-10-25
If it were me, I would personally like to have more experience with linux before trying to administer it to that many users. But it can be done.

---

### Post by Abhi Kalyan on 2006-10-26
thats the soundest piece of advice i had heard in a long time.
1. I am moving to the conferance hall with another colleague of mine to creat a list of mile stone.

Thank you Loads brentoboy.
Will post back when the list is ready and authenticated.
Thank you for putting me on to reallity. (on track)

---

### Post by Abhi Kalyan on 2006-10-26
Thank you lapsey,
Hope it works fine and i live to tell the story!!
Thank you once again

---

