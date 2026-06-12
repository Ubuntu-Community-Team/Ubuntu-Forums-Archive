---
title: "Internet problems"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by larrypinsupplync@msn.com on 2006-03-22
I installed Ubuntu last night with few problems.:)  Now i try to use firefox and, get nothing. I've read over a hundred threads, but most of them go way over my head. when i open the browser ican type in 192.168.1.1 and this will direct me to my ISP login and fromthere ican see that my modem is connected. Therefor I know i'm getting out but i can't access any other page.
Please help! My technical understanding is low so be gentle.

---

### Post by gabruo on 2006-03-22
Are you connecting to a wireless router?  Or a DSL/cable modem?

---

### Post by larrypinsupplync@msn.com on 2006-03-22
DSL modem

---

### Post by larrypinsupplync@msn.com on 2006-03-22
thanks you guys this was sooooooooooo helpful

---

### Post by Brunellus on 2006-03-22
[QUOTE=larrypinsupplync@msn.com]thanks you guys this was sooooooooooo helpful[/QUOTE]
1) if you're connecting directly via an ADSL modem, then you're using PPPoE.  

2) We're not paid here.  Our only reward is the satisfaction of a good deed done.  So don't abuse the patience of the people in this community.  Ubuntu means "humanity towards others."  it does not mean "being obliged to take abuse from strangers."

---

### Post by noswal on 2006-03-22
See what you get if you type the commands listed in this post
[http://ubuntuforums.org/showthread.php?t=141464](http://ubuntuforums.org/showthread.php?t=141464)

---

### Post by larrypinsupplync@msn.com on 2006-03-22
i'm not trying to be pushy, but I am very frustrated. One of my online friends has been pushing Ubuntu at me for quite some time now, and assured me that
I would have NO problems. that this was soo much better thatn windows. It looks great, but i cant tell too much more about it. when i installed it last night I had no othe computer to access the web with. I was driving a half an hour to town to a coffee shop to get support. I picked up this win95 box im on now at a pawn shop for 50 bucks. so here i sit trying to work though this.
the last response told me to type a command. I can't even find a command prompt on here.

---

### Post by user1397 on 2006-03-22
To type a command go to Application==>Accessories==>Terminal

---

### Post by Sef on 2006-03-23
> i'm not trying to be pushy, but I am very frustrated. One of my online friends has been pushing Ubuntu at me for quite some time now, and assured me that
I would have NO problems.

I understand where you are coming from.  You were overpromised, and now (rightfully) you are upset.  I would be too if I was in your situation.

Linux advocats (myself among them) don't become evangelical and then end up overselling Linux.  It's a great operating system, but it does have its limitations, so please remember to tell others the good points and the problems they may encounter  with Linux.

---

### Post by John.Michael.Kane on 2006-03-23
@larrypinsupplync you need to make sure you network card is active. thats one.
next open the terminal which is in applications->accessories. then type  sudo pppoeconf follow the onscreen prompts, and you should have your Dsl up and working.

---

### Post by larrypinsupplync@msn.com on 2006-03-23
[QUOTE=SD-Plissken]@larrypinsupplync you need to make sure you network card is active. thats one.
next open the terminal which is in applications->accessories. then type  sudo pppoeconf follow the onscreen prompts, and you should have your Dsl up and working.[/QUOTE]
It says it scanned but did not get response.
I know that its gotta be doing something because i can acces my dsl site, but no others

---

### Post by Gordonbp531 on 2006-03-23
[QUOTE=larrypinsupplync@msn.com]I installed Ubuntu last night with few problems.:)  Now i try to use firefox and, get nothing. I've read over a hundred threads, but most of them go way over my head. when i open the browser ican type in 192.168.1.1 and this will direct me to my ISP login and fromthere ican see that my modem is connected. Therefor I know i'm getting out but i can't access any other page.
Please help! My technical understanding is low so be gentle.[/QUOTE]

You may need to disable ipv6 in Firefox. I know I have to. In a new Firefox window, in the location bar type "about:config" (without the quotes) and scroll down to the network section. Double-click on the line that reads 
network.dns.disableIPv6. Close and re-open Firefox. See if that helps

---

### Post by larrypinsupplync@msn.com on 2006-03-23
[QUOTE=gendibal]You may need to disable ipv6 in Firefox. I know I have to. In a new Firefox window, in the location bar type "about:config" (without the quotes) and scroll down to the network section. Double-click on the line that reads 
network.dns.disableIPv6. Close and re-open Firefox. See if that helps[/QUOTE]
I love you! works like a dream. but how do you even know to do things like that?

---

### Post by Iowan on 2006-03-23
[QUOTE=larrypinsupplync@msn.com]I love you! works like a dream. but how do you even know to do things like that?[/QUOTE]I'd bet there are a few head-shaped dents in gendibal's wall. ](*,)

---

### Post by Gordonbp531 on 2006-03-24
[QUOTE=Iowan]I'd bet there are a few head-shaped dents in gendibal's wall. ](*,)[/QUOTE]

ROTFL!

I found this when I was experimenting with Fedora Core (I think........)

---

### Post by Gordonbp531 on 2006-03-24
[QUOTE=larrypinsupplync@msn.com]I love you! works like a dream. but how do you even know to do things like that?[/QUOTE]

the other thing you might need to know is that if you can't get Synaptic to work, you may need to edit your /etc/dchp3/dhclient.conf file. 
Uncomment the line that starts "prepend domain-name-servers" and replace the default 127.0.0.1 with the dns servers of your ISP.......

---

### Post by kiff on 2006-03-26
I'm also a Ubuntu newbie, but after following your instructions I've managed to get firefox working. (I seemed to be having the same trouble as [email]larrypinsupplync@msn.com[/email]).

The problem is that I still can't get synaptic or evolution to work. I tried to follow the last post, but there doesn't seem to be a file called dhclient.conf on my system, so when I typed "sudo gedit /etc/dchp3/dhclient.conf" it created a new blank file. Can you tell me what I might be doing wrong?

---

### Post by Sef on 2006-03-26
Kiff:

It would be best to start a new thread with your problems.  People would be more likely to view it, and it wouldn't look like u are hijacking it (which I don't think you are.)

---

### Post by kiff on 2006-03-26
Thanks Sef. I'll do that.

---

### Post by Gordonbp531 on 2006-03-26
[QUOTE=kiff]I'm also a Ubuntu newbie, but after following your instructions I've managed to get firefox working. (I seemed to be having the same trouble as [email]larrypinsupplync@msn.com[/email]).

The problem is that I still can't get synaptic or evolution to work. I tried to follow the last post, but there doesn't seem to be a file called dhclient.conf on my system, so when I typed "sudo gedit /etc/dchp3/dhclient.conf" it created a new blank file. Can you tell me what I might be doing wrong?[/QUOTE]

My typo! Sorry, should be /etc/dhcp3/dhclient.conf, not "dchp3"

---

### Post by kiff on 2006-03-26
[QUOTE=gendibal]My typo! Sorry, should be /etc/dhcp3/dhclient.conf, not "dchp3"[/QUOTE]

Thanks again gendibal - I tried that, but still no luck.

I've moved my question to a different thread (as per Sef's suggestion) - "PPPoe problems". Perhaps if you have any other suggestions you could put them there? Thanks heaps for the help you've given me already anyway.

---

