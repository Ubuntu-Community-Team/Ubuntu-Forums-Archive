---
title: "Is Linux really for me?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by izacboy_123 on 2006-10-17
Hi.:) 

The whole reason i installed Linux was to use it for a Server. And now i am wondering. Is Linux right for me?:-k 

I want to run Windows programs on Linux. I only decided to use Linux as my server OS becuase one of my friends said it was safe, and my server wouldn't get hacked if i was running Linux. But running Windows programs on Linux sounds like a hell of a job! So i was wondering wether i should use a Windows OS for my server. E.G:Windows 2003?:-? 

I have no idea how secure Windows 2003 is. And i do not know how secure Linux is either. I'm only going by advice. Am i going to have some serious troubles running windows programs on Linux? Will it be very hard?

Can someone point me in the right direction?:-| 

Thanks8)

---

### Post by meng on 2006-10-17
What sort of Windows programs are you trying to run? And why would you run them on a server? What I'm driving at is a more fundamental question: do you need a separate machine? Then we can offer advice on whether to install Windows instead.

EDIT: Oh, a Linux box can be hacked, no doubt about it. So it's important to know what security you have in place and how vital it is that you don't get hacked.

---

### Post by matthew on 2006-10-17
If you want to run Windows programs without having to learn a new system and fiddle around with stuff then your best bet is to run Windows.

Your friend is right, though. Linux is substantially more secure.

If you decide you want to run Linux, though, you will need to spend some time learning how the system is designed to work. Once you do that you will appreciate it greatly. If that sounds like something you don't want to put effort into, then Linux probably isn't for you.

---

### Post by jeffathehutt on 2006-10-17
I guess there is no easy answer to this question.  The only way to get a Windows program to run under linux is to use the program wine or similar (there are a few).  However, even with wine, there is a chance the windows program will not run.

About security, both windows and linux *can* be secure.  As long as you take some measures in either operating system you shouldn't have to worry too much about hackers.  Things like strong passwords and a firewall will help to protect you no matter what operating system you run.

---

### Post by Sef on 2006-10-17
> my server wouldn't get hacked if i was running Linux

Linux can be hacked, but it is not as easy to hack it as Windows.  You need to set up your server correctly, so it can be harder to hack.  

> I want to run Windows programs on Linux.
> Am i going to have some serious troubles running windows programs on Linux? Will it be very hard?

You can use WINE or Crossover (a commercial version of WINE) for many Windows programs.  Why not use the Linux programs instead?

> I have no idea how secure Windows 2003 is.

Not as secure as Linux.

---

### Post by nalmeth on 2006-10-17
If you don't know how to properly secure a windows server *or* a linux server, then you could consider them both insecure. 

That said, linux servers (with knowledgable admins) have an excellent track record. It may be in your interest to use linux as your server.

As for your windows applications, post the apps you use/need. There may be equal/better equivalents, native ports, good performance in WINE, or it may be simply impossible to use your needed apps at all.

Let it be known what you need to do

---

### Post by John.Michael.Kane on 2006-10-17
izacboy_123 I would advise you to first learn how to install programs under linux,and deploy a fully working linux desktop. Then learn how to deploy a secure linux based server.

---

### Post by pbaehr on 2006-10-17
What sort of server are you setting up that you'll be running Windows programs on?

Are you using this as a server and personal desktop combined?

In general, I would say if you need to use Windows software, stick with Windows. But, if you give us an idea of what sort of Windows software you think you need maybe we can turn you on to some Linux alternatives.

---

### Post by in2media on 2006-10-17
untill 3 or 4 years ago all i could do was turn on the pc and turn it off again
then i moved to a new town and had no-one to sort out the pc when i made a mess of things i had to learn it myself. after a while i was sick of my pc ( running windows) going mental, spyware, adaware, virus after virus etc etc
then i heard of linux and ive never looked back as far as security. ok it can be a nightmare getting your favourite windows based program to run but then again windows was a nightmare untill you got used to ity wasn't it:)

---

### Post by starsky on 2006-10-17
> **izacboy_123 said:**
> Hi.:) 

Can someone point me in the right direction?:-| 

Thanks8)

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

Linux is a great kernel. Ubuntu is it's great child!. :)

---

### Post by seijuro on 2006-10-17
If you want to run windows programs run windows linux is definately more secure but you can help your windows server by putting a linux firewall/router between your server and your internet connection.

---

### Post by izacboy_123 on 2006-10-18
Oh, thankyou for so many replys!;) 

It's helped me think alot better.

I recently got my hands on an old dell server(yaaay!). And i was so pleased, becuase i can now make online games! Chat servers! Online registrations, etc etc.

Maybe alot of you don't know. But i'm going to be running a MMF2 Program on my server. It will be the server app. If none of you know what MMF2(Multimedia fusion 2) is, then look at this:[www.clickteam.com](www.clickteam.com)

Maybe that will give you an idea on what i will be using. I've already got Linux up and running on my server. Does anyone know of any really easy programs i can install and then remove for practise?

Thanks for so many replys!:)

---

### Post by Grey on 2006-10-18
Well, according to winehq, Multimedia Fusion runs perfectly on Linux.

[http://appdb.winehq.org/appview.php?iVersionId=5361](http://appdb.winehq.org/appview.php?iVersionId=5361)

That rather surprised me.  Although I think that the tester was probably not running the server on a seperate machine.  I don't have the software, and I'm not familiar with it, but that's a good sign.  It might be a little more buggy than running it on Windows however, so I might suggest sticking with a native Windows environment.  But your milage may vary.

There probably isn't (but someone is welcome to prove me wrong) a linux equivalent for this software, given how much support I've seen from Macromedia in the past.  ;)  Which leads me to believe that Linux isn't for you.

But nevertheless, I might suggest playing with it for a bit to try to familiarize yourself with it, and perhaps discover that Linux isn't the devil that people claim it to be.  Since you are interested in doing web work, and asked how to install software... I might suggest doing one of the following.

(command line method)
Go to Programs->Accessories->Terminal
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
Sit back and smirk.

(GUI method)
Go to System->Administration->Synaptic Package Manager.
Search for apache2, php5-mysql, libapache2-mod-php5, and mysql-server.  Mark each for installation, and then click apply.
Sit back and smirk.

That's ALL there is to installing software in Linux.  After you are done with that, point your web browser to localhost, and you should see the apache test page.  There's also other cool stuff you can install, such as forums, web administration tools, or other such stuff.

If you really want to make online games though, I might really suggest learning a real programming language.

---

### Post by izacboy_123 on 2006-10-18
Thankyou very much!

This server is connected with a network cable to my router. Is that secure?

I want this server to be as reliable, safe, and secure as i possibly can get it. Oh, and thanks for the help;) 

I think i might aswel stick with Linux. It sounds like the safest option. Even though it may take awhile, i will be learning at the same time, right?

Thanks8)

---

### Post by mozetti on 2006-10-18
> **izacboy_123 said:**
> This server is connected with a network cable to my router. Is that secure?

Well, the wire makes it more secure than wireless. And the router makes it more secure than directly connected to a cable/dsl-modem (assuming it's one of the routers w/built-in firewall, which it probably is).

> **izacboy_123 said:**
> I want this server to be as reliable, safe, and secure as i possibly can get it. Oh, and thanks for the help;)

Then you'll need to do some reading, practicing, and learning. There is a thread on here titled, "Securing Ubuntu", or something along those lines. Check it out. Also, search the internet for some tutorials and instructions on securing a linux server.

> **izacboy_123 said:**
> I think i might aswel stick with Linux. It sounds like the safest option. Even though it may take awhile, i will be learning at the same time, right?

Well, that's the right attitude to have. "Learning" is actually the main reason I started using Ubuntu/Linux. You sound relatively inexperienced with Linux in general, let alone operating & securing a server. My recommendations would be to install Ubuntu as a dual-boot with Windows on your regular home PC so that you can learn how to use linux in general.

Also, don't be discouraged if you FUBAR your server a few times and have to format & re-install as you practice/learn and try to secure it.

---

### Post by xpod on 2006-10-18
> I think i might aswel stick with Linux. It sounds like the safest option. Even though it may take awhile, i will be learning at the same time, right?

Thanks
Reply With Quote

You sound like you know a fair bit about things in general...
But even then i think the most common advice ive seen for someone in your position is to insatall a desktop ubu and get the feel for things first before
going at servers and stuff.

From what i`ve gathered so far those who are all the more experienced with windows etc find this all the harder to start so it`s best to make things as easy for yourself as possible.

I used windows for a few months and have now used ubunto for a few months
so servers are quite a way off for me to even contemplate....plenty old pc`s for one but nothing to "serve" so no need:D ..the only server in this house is "me" with my lots demands:-D 

I can tell you though that after a taste of wobbly windows i could never go back to my wonky windows....
Good luck with ubu and your servers

---

### Post by izacboy_123 on 2006-10-18
Thanks guys.

I'm going to have to make a list of to-do's:-D 

1-Install wine
2-Program server app
3-Secure Linux
4-Program my game
5-Release it!:-D 

yaaay!:D  hehe::)

---

### Post by xpod on 2006-10-18
look forward to playing it:D

---

### Post by nathan.renard on 2006-10-18
Make sure to keep posting your questions so we can help in the best way.

Remeber, there is no stupid question, all of us were newbies one day ](*,) 

And your problem might be of another ubuntu (or any other linux) user.

ps: when you get your game done make sure to make it available for us right? ^^

---

