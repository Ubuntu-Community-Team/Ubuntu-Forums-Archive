---
title: "*Help* cant get into router"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by endo666 on 2007-10-27
ok i have a linksys router_ befw11s4 version 4_ now i need some help. im using ubuntu and firefox to try to access the router.

i did the 192.168.1.1

i reset the router

linksys tech guys were no help

installed internet explorer and that will not let me into the router.

cant even get to where i put in the password.

this has taken hours to fix. please help. using ubuntu 7.04 tried it with firefox.

cant even get to where i put in my password.

---

### Post by dpar on 2007-10-27
Maybe 192.168.0.1
That works for dlink and a lot of others.

---

### Post by endo666 on 2007-10-27
ya i tried it. i even just tried https:// instead of just http://

---

### Post by dpar on 2007-10-27
Oooops, just checked linksys site......it is 192.168.1.1
My bad, sorry that was my best guess.

---

### Post by endo666 on 2007-10-27
its ok i appreciate the help.

---

### Post by kerry_s on 2007-10-27
yeah linksys just sucks.
anyway you just got to play with it, press the reset, then while your waiting for the lights to stop flashing have the address in the browser ready, as soon as the lights stop flashing, try to connect, also make sure your connected to #1 on the router.

if you still can't get in, get yourself a belkin.
also save the password and bookmark it for easy access. i keep mine under "Other" in my bookmarks.

---

### Post by endo666 on 2007-10-28
i have now tried 3 different web browsers. along with internet explorer through wine.

---

### Post by Incense on 2007-10-28
Are you wired or wireless? Just bit of randomness, but maybe you are connected to someone elses wireless, and you're trying to get into their router which may not be a linksys, and would not accept that IP address. I know it's out there, but you never know...

---

### Post by n3tfury on 2007-10-28
> **kerry_s said:**
> yeah linksys just sucks.
anyway you just got to play with it, press the reset, then while your waiting for the lights to stop flashing have the address in the browser ready, as soon as the lights stop flashing, try to connect, also make sure your connected to #1 on the router.

if you still can't get in, get yourself a belkin.
also save the password and bookmark it for easy access. i keep mine under "Other" in my bookmarks.

linksys sucks???  and compared to belkin?  LOL  

also, BAD advice saving/bookmarking passwords.  tsk tsk.


also, Incense has good advice.  what did you name your router?  are you SURE that's what you're connected to?  you get net access but can't get INTO the router? or you get no net access at all?

---

### Post by endo666 on 2007-10-28
yep im wired into my router.

and i know that it is 192.168.1.1 to get into it

---

### Post by n3tfury on 2007-10-28
i understand that you're wired into it, but you have internet access or no?

---

### Post by so7777777os on 2007-10-28
Wait for superior reply.....:lolflag::popcorn:

---

### Post by tmcmulli on 2007-10-28
Back to the basics... can you ping 192.168.1.1?  what is your host's IP address... if DHCP is disabled on the router, you might be getting a zero-conf address.

Do an ifconf and post.

---

### Post by endo666 on 2007-10-28
> **n3tfury said:**
> i understand that you're wired into it, but you have internet access or no?

yes im online rite now through the router. problem is i did a hard reset so now my wireless signal is being broadcast with no encryption. 

> **tmcmulli said:**
> Back to the basics... can you ping 192.168.1.1?  what is your host's IP address... if DHCP is disabled on the router, you might be getting a zero-conf address.

Do an ifconf and post.

endo@endo-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

ok what is ifconf. i typed that into the terminal and nothing happened.

---

### Post by llamakc on 2007-10-28
"ifconfig" not "ifconf".

---

### Post by endo666 on 2007-10-28
```
endo@endo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:93:06:0B  
          inet addr:**.***.**.7  Bcast:**.***.**.255  Mask:***.***.***.0
          inet6 addr: ****::***:8dff:****:60b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:293000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70294554 (67.0 MiB)  TX bytes:10322666 (9.8 MiB)
          Interrupt:19 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:***.*.0.*
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:548 (548.0 b)  TX bytes:548 (548.0 b)
```

i replaced some of the numbers with *********

---

### Post by tmcmulli on 2007-10-28
What is your IP address?  Is it in the same subnet as 192.168.1.1??  It would need to be 192.168.1.x to be able to see the Linksys default setting.

---

### Post by llamakc on 2007-10-28
inet addr:**.***.**.7 

If each of those * are representative of ONE number each, you're not getting an IP from the router's DHCP>

---

### Post by endo666 on 2007-10-28
> **llamakc said:**
> inet addr:**.***.**.7 

If each of those * are representative of ONE number each, you're not getting an IP from the router's DHCP>

ya each * is one number.

---

### Post by Edgeworth on 2007-10-28
What service provider are you using? With my dsl, [http://dslrouter](http://dslrouter) gets me in.

---

### Post by endo666 on 2007-10-28
it is cable internet and i dont have this problem in windows. but i dont have windows anymore

---

### Post by llamakc on 2007-10-28
Have you ever edited your /etc/hosts file?

What was the result of pinging 192.168.1.1?

---

### Post by endo666 on 2007-10-28
> **llamakc said:**
> Have you ever edited your /etc/hosts file?

What was the result of pinging 192.168.1.1?

nope never edited that file 

endo@endo-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

---

### Post by llamakc on 2007-10-28
So ping doesn't return any data like this:

```

ken@llamakc 01:02:37:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.905 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.673 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.728 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.673/0.768/0.905/0.104 ms

```

Are you certain you're plugged into one of the 1-4 ports on the back of the router?

Does your ip begin with a 192.?

---

### Post by n3tfury on 2007-10-28
that'd be a good one if his nic/CAT5 was bad and he was piggybacking on his neighbor's LAN.

---

### Post by endo666 on 2007-10-28
> **llamakc said:**
> So ping doesn't return any data like this:

```

ken@llamakc 01:02:37:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.905 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.673 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.728 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.673/0.768/0.905/0.104 ms

```

Are you certain you're plugged into one of the 1-4 ports on the back of the router?

Does your ip begin with a 192.?

im trying again maybe it is just taking some time. and yes im plugged into the router.

> **n3tfury said:**
> that'd be a good one if his nic/CAT5 was bad and he was piggybacking on his neighbor's LAN.

that would be hard for me to do i have no wireless card in my computer.

---

### Post by llamakc on 2007-10-28
So why do you use a router? Why not plug directly into the cable modem? Are there other computers on the LAN? What does trying from one of those result in?

---

### Post by endo666 on 2007-10-28
well i used to have my 360 hooked up to it but rite now there are no other computers hooked up to it. but i need to get this to work.

---

### Post by Mondoman on 2007-10-28
Presumably he uses a router for its firewall features.

---

### Post by endo666 on 2007-10-28
> **Mondoman said:**
> Presumably he uses a router for its firewall features.

there we go i knew i had it for a reason. but now after i reset it and i cant get into it im not able to turn wireless of so im broadcasting my internet to everyone.

---

### Post by llamakc on 2007-10-28
1. The router does not respond to pings.
2. You are absolutely certain you are plugged into the router.
3. You have restarted the router[B] AND the cable modem.
[/B]4. You have tried getting into the router's web interface by pointing your web browser to 192.168.1.1 and you do NOT get the password prompt.

Correct?

---

### Post by endo666 on 2007-10-28
> **llamakc said:**
> 1. The router does not respond to pings.
2. You are absolutely certain you are plugged into the router.
3. You have restarted the router[B] AND the cable modem.
[/B]4. You have tried getting into the router's web interface by pointing your web browser to 192.168.1.1 and you do NOT get the password prompt.

Correct?

1. guess not.
2.yes im certain unless my video card gets a wireless signal. which would be cool.
3.yep done that.
4.yep doesn't give me the password prompt. gives me the this page cannot be displayed.

---

### Post by llamakc on 2007-10-28
I hate recommending this but it sounds like your router went tits-up and broke. Unfortunately that happens from time to time. 

No other computers in the house to attempt getting into the router with?

---

### Post by ciscosurfer on 2007-10-28
Have you done the following:

[LIST=1]
[*]Reset your router/firewall (often this is a recessed button)?
[*]Plugged directly into your cable modem to see if direct access works?
[*]Reset interfaces to pull new IPs / set static IPs if this is your setup?[/LIST]If you have done all of the this and followed others instructions as well, I have to agree that your router is toast.

---

### Post by endo666 on 2007-10-28
> **llamakc said:**
> I hate recommending this but it sounds like your router went tits-up and broke. Unfortunately that happens from time to time. 

No other computers in the house to attempt getting into the router with?

no not rite now anyway. the thing is why am i able to get online if the router is broke. could it be that linux web browsers cant access and only IE through windows can.

i may have to find a computer with windows to try it on.

---

### Post by ciscosurfer on 2007-10-28
> **endo666 said:**
> no not rite now anyway. the thing is why am i able to get online if the router is broke. could it be that linux web browsers cant access and only IE through windows can.

i may have to find a computer with windows to try it on.

Do you have a proxy set up when using IE?  Otherwise, the browser won't have anything to do with it.  Try using Firefox (or any other browser) in Windows to see what I mean.

---

### Post by chunderbunny on 2007-10-28
I've had this problem before with my Linksys router. One day the web interface just stopped working. It came back after a few weeks, I have no idea what happened. 

But yeah, it is possible for the web interface on the router to break but that the router still routes.

---

### Post by endo666 on 2007-10-28
> **ciscosurfer said:**
> Do you have a proxy set up when using IE?  Otherwise, the browser won't have anything to do with it.  Try using Firefox (or any other browser) in Windows to see what I mean.

how would i find out. i have IE installed in ubuntu through wine.

---

### Post by ciscosurfer on 2007-10-28
> **endo666 said:**
> how would i find out. i have IE installed in ubuntu through wine.If you didn't change the default configuration, chances are you aren't using a proxy.

At the risk of sounding like we are putting you off, I would also suggest giving a search on your favorite engine a go.  For instance, I came up with page after page of good info from a Google search with the search parameters of **linksys router problems**.

---

### Post by djsroknrol on 2007-10-28
I've been using Linksys routers and cards for years...and they've all worked fine for me in Ubuntu from Dapper all the way thru Gutsy and a few other distros as well.....Sounds like the router went south (the big wireless signal in the sky). 

Can you borrow/find another router to confirm everyone's suspicions?

---

### Post by n3tfury on 2007-10-28
> **ciscosurfer said:**
> For instance, I came up with page after page of good info from a Google search with the search parameters of **linksys router problems**.

um, you can do that with any piece of hardware.  give me a break.

---

### Post by endo666 on 2007-10-30
i got this fixed. i followed this guide.

[http://www.dd-wrt.com/wiki/index.php/Recover_from_a_Bad_Flash](http://www.dd-wrt.com/wiki/index.php/Recover_from_a_Bad_Flash)

---

### Post by llamakc on 2007-10-30
Glad to hear you fixed it. Had you tried to flash it before, or was this just a serendipitous fix?

Cheers all the same.

---

### Post by ebozzz on 2007-10-30
Curious about this one myself. Any updates?

maybe a simple *ifconfig* from terminal will yield more insight as to what the actual router IP (gateway) is?

EDIT: Replied prior to reading through the entire thread.

---

### Post by endo666 on 2007-10-30
> **llamakc said:**
> Glad to hear you fixed it. Had you tried to flash it before, or was this just a serendipitous fix?

Cheers all the same.

nope never flashed the bios. updated the firmware but i got into it after that too. so woot. thank you all

---

### Post by xapper on 2007-11-01
I am having a similar problem with a belkin router!!!

I have Ubuntu/xp dualboot. I can access the router by 192.168.2.1 from IE7 in XP but cannot do the same in firefox browser- Ubuntu.

Maybe ill try giving ithe flash a thorough  hard reset and see if that helps... :confused:

---

### Post by xapper on 2007-11-03
Well I followed for the instructions and performed a hard reset of the router/adsl modem and it solved the problem. Thanks ! :)


> **xapper said:**
> I am having a similar problem with a belkin router!!!

I have Ubuntu/xp dualboot. I can access the router by 192.168.2.1 from IE7 in XP but cannot do the same in firefox browser- Ubuntu.

Maybe ill try giving ithe flash a thorough  hard reset and see if that helps... :confused:

---

### Post by endo666 on 2007-11-03
sweet glad it worked

---

