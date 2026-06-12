---
title: "Pidgin - MSN Messenger problem -- Keep getting connection error when sending messages"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-08-20
I was using Pidgin for a few weeks with no problems with MSN Messenger.  Suddenly now it seems I can not send any messages -- Keep getting connection error.

I can log into MSN Messenger, and even see when my buddies log in and out, however when I attempt to send them any messages I keep getting a connection error

[QUOTEMessage could not be sent because a connection error occurred:][/QUOTE]

Ive googled around, but havent found a solution, although this problem has been described (but only with attempting to send URL's).

Any input?

Thanks

---

### Post by Hobo Joe on 2007-08-20
Try uninstalling and reinstalling:
```

sudo aptitude purge pidgin
sudo aptitude install pidgin

```

---

### Post by kevdog on 2007-08-20
I compiled it from source -- (which I highly recommend everyone to do -- got all the good plugins etc).  Ill give it a whirl, but its kind of weird

---

### Post by Hobo Joe on 2007-08-20
Actually, I've been having problems, so I reinstalled just now, and the repos that I had were broken.
So I went to getdeb.net and found some new ones.

---

### Post by kenshin_i on 2007-08-20
I have the same problem, earlier, i can't even log into msn, but then I used the HTTP method.  When I did that, I can see my buddies on / off but can not chat, have the same connection problem.

In addition to that, i can't connect to google talk as well.

Btw, I did compiled from source.  So right now I am not sure what should I do.  How should I purge the pidgin if you compiled from source and start over?

---

### Post by kevdog on 2007-08-21
If you compiled from source:

To completely remove pidgin

sudo updatedb

Then change to the source pidgin directory (where you did make, make install)

Type
sudo make uninstall

Then
locate pidgin

The above might list some directories that were left behind (beyond the source directories).  Delete these and then reinstall.

---

### Post by matzi11a on 2007-08-21
I started having the same problem with gaim 2.0.0beta5 yesterday, here is what I did to solve it. not sure if all steps are required - but it worked for me.

1. installed pidgin 2.0.1
2. looked at Accounts->MSN->Advanced and unchecked "Use HTTP Method"
3. working again :-)

---

### Post by kenshin_i on 2007-08-21
I forgot to mention that I tried both Kopete and aMSN, still no luck getting connection to MSN and google talk.  Wondering if the problem lies somewhere else.

---

### Post by kevdog on 2007-08-21
Seems like a bug report was filled on pidgin a few days ago about the same problems -- something about when msn changed its interface --- [http://developer.pidgin.im/ticket/2643](http://developer.pidgin.im/ticket/2643)

Tried the HTTP/not HTTP option -- a no go!!

Is everybody having this problem or just me??

---

### Post by RonB123123 on 2007-08-21
I'm having this problem too.

Kopote connects to MSN fine and it doesn't even use the HTTP method. Somehow the Pidgin developers screwed up because I still can't connect the normal way and I have to check the HTTP method to see the friend's list and that doesn't work either just like your problem. 

Pidgin and MSN haven't worked for 2 to 3 months now. Ahh well, I really liked them too.

PS: I'm using Pidgin 2.1.0 and in 2.1.1 they haven't fixed it either.

---

### Post by kevdog on 2007-08-21
Im also using pidgin 2.1.0 compiled from source.  Ive read problems compiling the new version and have stayed away thus far.  Anyone no where a cvs or svn version may be available???

---

### Post by nebbe on 2007-08-21
Its not an issue with Linux, or with router.
Both me and my flatmate are using Gaim/Pidgin, and it works fine on mine (Ubuntu Feisty), but not on her XP. 
On my Pidgin - Msn the button HTTP is unchecked...

---

### Post by kenshin_i on 2007-08-21
In regards of connecting to MSN, used to be working fine for me until last week.
Then the problem came up.. First not able to connect the MSN at all, tried the HTTP method, then I can login, but not able to send any messages out, gave me the same error as in your 1st post.

---

### Post by nebbe on 2007-08-21
I can actually answer my own post this time. 
And to qvote Matsi11a:

"2. looked at Accounts->MSN->Advanced and unchecked "Use HTTP Method"
3. working again "

Im not sure if version of the program does matter, but i dont think so.. 

Im using (Linux/Xubuntu Feisty Fawn 7.04), with Pidgin 2.0.2 and it has always been working.

My flatmate has (MS XP Sp2), first had the error message on a late v. of Gaim for some time but couldnt be bothered.... tried first with upgrading to Pidgin v. 2.1.1 (for win), still nothing. 

Unchecked the "Use HTTP Method" option, restarted the program, and we all Smiling again :)


Hope this helps, took a while to google an answer ;)

---

### Post by marked23 on 2007-08-21
Hi folks,

I'm the guy who posted the pidgin ticket 2643... That ticket has since been closed as duplicate of 2638.

Some of you are able to get things working if you turn off HTTP method.  On many corporate networks, the HTTP method is the only hope for us. 

The HTTP method was working fine for us for about a month.  It may be coincidence, but when MS came out with a new Hotmail login page, that's about the same time my pidgin HTTP Method stopped working. 

I imagine that something subtle about the HTTP method was changed by MS and it will be a while until LibPurple can be updated to deal with it.

---

### Post by kenshin_i on 2007-08-21
Marked23:

Do you know if this affects other programs? i.e. Kopete or aMSN?

---

### Post by kevdog on 2007-08-21
I was using the http method since I couldnt get the non-http method working from the get go about 3 weeks ago.  Now Im having the same problem as everyone described -- being able to see when msn buddies are logged in/out, but not being able to send messages to them.  With the non-http method I get the error about 1 second after the send, with the http method it takes 5 seconds until the error message appears (based on message time stamps). 

Hopefully someone is looking into it.  I really like pidgin -- particularly the purple pidgin plugin pack compiled from source.

---

### Post by marked23 on 2007-08-21
I would guess that any project that is based on libpurple would certainly have the problem.

Even though aMSN appears to be based on something else, I just tried it.  It has the same issue. 

There isn't a windows version (ducks for cover) of Kopete (duh!) so I can't try that from here. 

-Mark

---

### Post by Angellis_ater on 2007-08-21
I'm having the exact same problems with Piding 2.1.0 as described here, I've tried everything including changing the servers to messenger.hotmail.com, live.com or msn.com (this worked earlier, so someone might get by on this), trying different ports, using or not using the HTTP-method.

Nothing works. I can still SEE my friends, but not send or receive messages. Sucks.

aMSN and Kopete also fail somewhere along the road, aMSN cannot even login and Kopete gets the same problems that Pidgin gets, only that Kopete bounces on and offline all the time as well.

So, PLEASE, can someone help us?

---

### Post by fct on 2007-08-22
Have to try unchecking the HTTP method when I get home.

It makes sense, both amsn 0.97RC1 and pidgin fail when sending messages, and both are set to HTTP method because of the university firewall.

---

### Post by Jamie Jackson on 2007-08-22
Yup, same here: Got buddies, but can't IM 'em. Can't turn off HTTP at work.

I'm not sure (I don't have all that many MSN contacts), but I think it happened in the last week or two.

---

### Post by kevdog on 2007-08-22
Jamie 

Good to here from you, but sorry to say I still have the same problem as you and everyone else.  According to the bug ticket that was submitted, this problem was given low-priority, so it might be sometime until this problem is resolved.  I too started having the problem about 1 week ago.

---

### Post by Chris11 on 2007-08-22
> Unchecked the "Use HTTP Method" option, r[COLOR="Red"]estarted the program[/COLOR], and we all Smiling again


worked for me.. with Pidgin 2.1.1., Thx

---

### Post by aluxito on 2007-08-22
Yes, this problem is due  changes in MSN interface. by now i have to use [[COLOR="Blue"]meebo[/COLOR]]("http://www.meebo.com") . you can see the report in previous posts. i think

---

### Post by kevdog on 2007-08-23
I can confirm today that I can connect if I disable or uncheck the HTTP option (I use to use this).  For many however I know this is not an option.

For those that want to try this, uncheck the http option, save the changes, and then restart pidgin.  I only worked for me after a reboot for some reason -- maybe Windows is haunting my machine!

---

### Post by Angellis_ater on 2007-08-23
Kevdog: Can you communicate with those on your list?

---

### Post by kevdog on 2007-08-23
The list??? Im guessing you mean those on the msn messenger buddy list.  The answer is yes!  It works as before -- still using version 2.1.0.

---

### Post by RonB123123 on 2007-08-23
Hey it finally worked! I've had HTTP thing unchecked before and it still did not work, but for some reason when I opened up Pidgin, and I ticked it on. Then hit save. Opened preferences again, unticked it and kill and reopened Pidgin, MSN worked fine! :D

Thanks for the help!

---

### Post by kenshin_i on 2007-08-24
It is still not working for me, when i unticked HTTP option, restart pidgin, I can't even get online to MSN.  I even tried uninstalling and installing Pidgin again (2.1.0)

---

### Post by fct on 2007-08-24
kenshin_i, sounds like you're behind a firewall and hence you need the http connect method.

---

### Post by kenshin_i on 2007-08-24
fct: i do have a router and firewall setup.  Should i free up the port on the firewall setup?  What about the router?

Btw, I was able to connect to MSN before with no problem until a couple weeks back.

---

### Post by kevdog on 2007-08-24
If it was working a couple of weeks ago, unless you made a change in the firewall, you probably dont need to do anything.  As a test, you could just turn your firewall off, and then see what happens.  I know this wasnt a problem for me.  I didnt need to change anything at the router level (port forwarding etc).  I have a basic linksys router with no built in formal firewall.

---

### Post by kenshin_i on 2007-08-24
Thanks!! now it works!!! (no HTTP)
Google talk also works!!

So now i just let the firewall to allow the messenger's hosts.

---

### Post by kevdog on 2007-08-25
Dmnit!!!

Now its not working anymore.  Any one else with any suggestions???  No work with the HTTP enabled or disabled.

---

### Post by gladstone on 2007-11-20
I think I'm getting a slightly different issue: MSN is silently dropping messages (not receiving them from my contacts). I have tried using Pidgin in both http and non-http modes, and have used various web messengers (including MS's own!) and I still seem to not be receiving **all** messages.

When I sign into MSN on my XP machine, all the old messages are received

Has anyone else noticed this?

---

### Post by odin79 on 2008-03-26
> **gladstone said:**
> I think I'm getting a slightly different issue: MSN is silently dropping messages (not receiving them from my contacts). I have tried using Pidgin in both http and non-http modes, and have used various web messengers (including MS's own!) and I still seem to not be receiving **all** messages.

When I sign into MSN on my XP machine, all the old messages are received

Has anyone else noticed this?

Yes I have this EXACT same problem: I am using Pidgin 2.4.0 with msn and google talk. MSN doesn't drop all the messages, but some of my friends always sees me as offline (we can still chat). Also, it happens that they send me messages but I don't recieve them untill I log in with live messenger. Nedlees to say this is EXTREMLY annoying, and IMHO is a major usability issue for people new to Ubuntu. It should get the highest priority (if it is a bug that is)!

Anyone has any ideas how to fix? :confused::confused::confused::confused:

---

### Post by gladstone on 2008-03-27
> **odin79 said:**
> Yes I have this EXACT same problem: I am using Pidgin 2.4.0 with msn and google talk. MSN doesn't drop all the messages, but some of my friends always sees me as offline (we can still chat). Also, it happens that they send me messages but I don't recieve them untill I log in with live messenger. Nedlees to say this is EXTREMLY annoying, and IMHO is a major usability issue for people new to Ubuntu. It should get the highest priority (if it is a bug that is)!

Anyone has any ideas how to fix? :confused::confused::confused::confused:
I'm glad someone else is having the same problem!

I posted this to the Pidgin bug reports a while ago:

[https://developer.pidgin.im/ticket/4704](https://developer.pidgin.im/ticket/4704)

and

[https://developer.pidgin.im/ticket/4181](https://developer.pidgin.im/ticket/4181)

Generally, I got the feeling that noone was really bothered about the situation. I gave up in the end and started using aMSN, which really does not suit my needs, but it works...just. (I still get a similar problem when using it, which leads me to believe this is a protocol issue rather than something with the client).

If you read further into it, you'll find:

> I am glad that someone at least confirm that MSNP14 would resolve this issue. Since it's been suspected that this is a server side problem I am not sure what we can do. So I guess we'll have to wait until they release MSNP14 with the next version(s) of Pidgin, or apparently use Mercury Messenger which allows you to use the new protocol version.

---

### Post by kevdog on 2008-03-27
I ended up compiling pidgin from source, and although it doesnt work 100% of the time, it works most of the time.  I have no idea if it was the compilation of pidgin (latest version), a MSN server side problem, or combination of both.

---

### Post by odin79 on 2008-03-27
As I said, in my opinion this is not a hardware/software problem because:
1. The problem doesn't exist on windows.
2. Severeal ppl have the same problem.

Again: This is a major usability issue (very many ppl are using msn on a daily basis), and may deter new users from choosing Ubuntu. :(

---

