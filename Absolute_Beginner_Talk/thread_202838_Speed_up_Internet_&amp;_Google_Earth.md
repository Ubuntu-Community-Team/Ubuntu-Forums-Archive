---
title: "Speed up Internet &amp; Google Earth"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-06-24
This isn't anything new or my idea, I found it while searching through some of the old ubuntuforums posts.

It worked for me, it may work for you too.

Basically you disable ipV6 which apparently conflicts with ipV4, I'm no expert on the whys or hows but like I said, it worked for me.

1. Open your Gnome Terminal/ KDE Konsole and type :-
For Gnome
> gksudo gedit /etc/modprobe.d/aliases
or For KDE
> kdesu kate /etc/modprobe.d/aliases

2. Kate or Gedit will open and show you this file :-
   (scroll down to see what to copy and paste)

> # These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
alias net-pf-10 ipv6 off [COLOR="Red"]--[/COLOR]
alias net-pf-10 off       [COLOR="Red"]--    add these three lines here.[/COLOR]  
alias ipv6 off              [COLOR="Red"] --[/COLOR]
[COLOR="Red"]#[/COLOR]alias net-pf-10 ipv6 =========comment (put #) the original line
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet

3. Now "Save" and "Reboot" 

There's another way too: instead of changing aliases file, create fie named bad_list in /etc/modprobe.d containing this line:

> alias net-pf-10 off

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

Like I said these are NOT my ideas, I did them and now Google Earth and Firefox are noticeably faster for me.

---

### Post by loell on 2006-06-24
yes, it is noticeably faster.. thanks :)

---

### Post by catlett on 2006-06-24
Thanks Rich.
This is the best tweak yet. I have done all the other changes to about:config but this IS noticeable.

Thanks again for letting us in on your find.

Regards, Catlett

---

### Post by arochester on 2006-06-24
Good Heavens! What a difference!

---

### Post by WADemosthenes on 2006-06-24
Why does it work?

---

### Post by T700 on 2006-06-24
No idea how this works, but it certainly seems faster.

Paul

---

### Post by Drakkor on 2006-06-24
This for dial up or broadband ?

---

### Post by Chris03 on 2006-06-24
Nice!

---

### Post by catlett on 2006-06-25
[QUOTE=Drakkor]This for dial up or broadband ?[/QUOTE]
I don't know. I have broadband and it works. Also my /etc/hosts file has a bunch of parameters for Ipv6 (I'll post the file). It appears you should forget adding parameters and just disable it altogether because disabling it with Rich's tweak has given me the best result.

> # The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by Frank Golden on 2006-06-25
[QUOTE=catlett]I don't know. I have broadband and it works. Also my /etc/hosts file has a bunch of parameters for Ipv6 (I'll post the file). It appears you should forget adding parameters and just disable it altogether because disabling it with Rich's tweak has given me the best result.[/QUOTE]
Please explain in more detail (disable how etc). Do you mean disable the hosts file.? Thanks

---

### Post by K.Mandla on 2006-06-25
Wow. I use broadband, but I didn't expect the difference to be that much different. Thanks for this; this is an excellent tweak.

---

### Post by raptros-v76 on 2006-06-25
this is good for now. and i guess when ipv6 finally comes about as the standard everywhere, we can figure out how to disable ipv4

---

### Post by ihitf13anddied on 2006-06-25
In your code you list the three lines to add.......

alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here.
alias [COLOR="Red"]ivp6 [/COLOR]off --

should that red one read "ipv6" or is it correct as you posted it?

---

### Post by martypal2005 on 2006-06-25
I'm sure it is "noticably different", however here are some questions i have: 

Does it actually speed up download rates? (what did you guys use to have before and what about after)

Is it only when surfing and "hitting" the server? (not the actual download)

Perhaps these settings for ipv6 are tests that are performed at the beginning of a new connection and thereby slowing down.

---

### Post by Rory on 2006-06-25
If using Firefox, wouldn't a simpler way to accomplish the same thing would be to go: 

about:config

disableIPv6:  True

I recognize this thread's instructions might disable IPv6 for all internet connections.  But, if you're only using Firefox, should my litte Firefox tweak accomplish the same thing?

R.

---

### Post by raptros-v76 on 2006-06-25
actually, this is really useful. it made my connection quite a bit faster.

---

### Post by Rory on 2006-06-25
[quote=raptros-v76]actually, this is really useful. it made my connection quite a bit faster.[/quote]

I'm sure it is.  I'm just trying to establish if the Firefox tweak does the trick and makes the other instructions in this thread redundant.  

I have a 6 Mpbs connection and I typically get very, very close to that in Speed tests.  So, I'm not sure how much further I could go, no matter what tweaks I did.

---

### Post by raptros-v76 on 2006-06-25
well, this tweak prevents ipv6 from loading into the kernel, at least that is what it seems to be doing.

---

### Post by Rory on 2006-06-25
I suggest people do a pre/post test to see the actual difference they see in speed.  

Speedtest: [http://www.speakeasy.net/speedtest/]("http://www.speakeasy.net/speedtest/")

Try it 3 times with the city closest to you to get an average, then do the tweak and reboot, then try it again three times and post results.

---

### Post by Rory on 2006-06-25
[quote=ihitf13anddied]In your code you list the three lines to add.......

alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here.
alias [COLOR=Red]ivp6 [/COLOR]off --

should that red one read "ipv6" or is it correct as you posted it?[/quote]

Good catch.  Could the original poster update his instructions if this was a mistake.  Otherwise, people will cut n' paste in wrong code.

---

### Post by rifleman on 2006-06-25
You'll find that the reason this happens is because apps will first attempt a connection on IPv6. When this fails, they'll then switch to IPv4. It's this first attempt that causes the delay.

This tweak will NOT speedup downloads. Once the connection's made, you're gonna see it going at full speed.

Of course, the other way to tweak this is to get a proper IPv6 connection. :)

Oh and for the critics - this is in no way a shortcoming of IPv6 - it's merely caused by not having an actual IPv6 connection. If anything, it's proving the readiness of the apps concerned for IPv6.

---

### Post by s|k on 2006-06-25
Lol, this thread is on the front page of Digg. Apparently IPv6 isn't very popular.

---

### Post by Asraniel on 2006-06-25
well, this is one of the biggest bugs in ubuntu that no dev cares about.. but well, thats life (like the bug with my laptop ATI card that is on no fix for political reasons even if it is a one liner.. well.. im still using kubuntu, so it cant be that bad ;-) )

---

### Post by raptros-v76 on 2006-06-25
what we're waiting for is the blarging isps to get with the program and give ipv6 service

---

### Post by Rory on 2006-06-25
[quote=Asraniel]well, this is one of the biggest bugs in ubuntu that no dev cares about.. but well, thats life [/quote]

I'm not so sure this is a bug.  Seems to be Functioning As Designed.

---

### Post by Asraniel on 2006-06-25
when the internet is slow for a high percentage of users and they dont even know why, then yes, it is a bug.

---

### Post by jamesford on 2006-06-25
unfortunately this doesent work, not on my machine anyway. 
do 'ip a | grep inet6'

---

### Post by Rory on 2006-06-25
[quote=Asraniel]when the internet is slow for a high percentage of users and they dont even know why, then yes, it is a bug.[/quote]

So, what is the best solution?  To disable it by default so iPv6 users are automatically pushed down to iPv4?  Then, people would call that a bug, too.  

I think there are trade-offs in design.  If Ubuntu is designed to go to iPv6 and when not found move to iPv4, this might be a suitable approach.  But, they will have to weigh this approach against the length of the delay when switching from iPv6 to iPv4.  It's a cost-benefit analysis.  Remember: internet should not be slower once connected to iPv4.  It's the delay in switching that's at issue here.

---

### Post by fo0 on 2006-06-25
The delay is most likely in name resolution. In OpenBSD, the resolver will first attempt to find the IPv6 address: 

12:02:25.737880 1.2.3.4.2386 > 5.6.7.8.53:  40168+ AAAA? [www.ubuntuforums.org](www.ubuntuforums.org). (38)
12:02:25.752481 5.6.7.8.53 > 1.2.3.4.2386:  40168 0/1/0 (97)
12:02:25.753092 1.2.3.4.44300 > 5.6.7.8.53:  40280+ A? [www.ubuntuforums.org](www.ubuntuforums.org). (38)
12:02:25.768687 5.6.7.8.53 > 1.2.3.4.44300:  40280 1/5/5 A 82.211.81.186 (237)
12:02:25.769229 1.2.3.4.11726 > 82.211.81.186.80: S 2355536639:2355536639(0) win 16384 <mss 1414,nop,nop,sackOK,nop,wscale 0,nop,nop,timestamp 3187919881 0> (DF)

I assume it is the same in Ubuntu.

---

### Post by Rory on 2006-06-25
It's like this in most Linux distros.  This is not an issue specific to Ubuntu.

---

### Post by justinflavin on 2006-06-25
my firefox is a lot faster after doing that about:config tweak.

---

### Post by ihavenoname on 2006-06-25
I have a question, I have a problems with my network going down at random times, do you think that it might be related to ipv6? and would this help at all? (I am going to do it anyways, I am asking because I am trying to find reasons for why my network goes down. (It forces me to remove the ndiswrapper module and reinsert it before it will let me reconnect.

---

### Post by richbarna on 2006-06-25
[QUOTE=ihitf13anddied]In your code you list the three lines to add.......

alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here.
alias [COLOR="Red"]ivp6 [/COLOR]off --

should that red one read "ipv6" or is it correct as you posted it?[/QUOTE]
Firstly, I am glad that this has helped a few people,
Secondly, sorry guys !! :rolleyes: 

Yes it is ipv6 NOT ivp, it was a copy and paste typo.

Like I said, this isn't my personal tweak, I found it in the forums and it worked for me.

As ipv6 isn't currently as widespread as ipv4, time is lost while your system looks for an ipv6 and THEN ipv4.
see the wiki :-
[http://en.wikipedia.org/wiki/IP_address]("http://en.wikipedia.org/wiki/IP_address")

Obviously later we will all need ipv6 enabled, but at the moment it is causing a few problems (apparently).

---

### Post by richbarna on 2006-06-25
[QUOTE=Rory]If using Firefox, wouldn't a simpler way to accomplish the same thing would be to go: 

about:config

disableIPv6:  True

I recognize this thread's instructions might disable IPv6 for all internet connections.  But, if you're only using Firefox, should my litte Firefox tweak accomplish the same thing?

R.[/QUOTE]

If that works for you then do that, like I said, this isn't my tweak, I found it with a search of the forums and I thought it might be nice to post again for users that have missed it.

Personally, my internet connection is Whizzing! now.

I mean Firefox, and Google Earth, I use Ktorrent and that seems to be the same, as does amule.

As we know, internet speed depends on a LOT of factors :-
Time of day, users, nodes, modems, routers, setup, even RAM and if you keep your machine defragged.

So basically, for now this works in conjuction with all of the above. When ipV6  is widespread, we'll see what happens.

---

### Post by catlett on 2006-06-25
[QUOTE=Rory]I'm sure it is.  I'm just trying to establish if the Firefox tweak does the trick and makes the other instructions in this thread redundant.  

I have a 6 Mpbs connection and I typically get very, very close to that in Speed tests.  So, I'm not sure how much further I could go, no matter what tweaks I did.[/QUOTE]
Just for the sake of full disclosure. Yes you can go to about:config and change disableIpv6 to true and you will get the same response.
For others who don't know about about:config, I'll give the instructions. 
Clear the url in Firefox's address field. Enter ```
about:config
``` Hit "go" after the address bar.
This will take you to a page that has your firefox configuration. Enter this in the "filter" line . ```
network.dns.disableIPv6
```
This will bring up a line that says
```
network.dns.disableIPv6                user set   boolean   false
```
Double-click on the line to change the value from false to true.

P.S. This quote, which came from a Digg's site comment on this  thread,  pretty much sums up the explanation 
> The reason why it works is simple. The box will stop trying to do IPv6 DNS lookups. With IPv6 support enabled, you will notice the box trying to do AAAA record lookups. It will then fall back to standard A (IPv4) lookups. This takes extra time and slows down your browsing experience. You can observe this by running tcpdump while browsing.

---

### Post by richbarna on 2006-06-25
[QUOTE=s|k]Lol, this thread is on the front page of Digg. Apparently IPv6 isn't very popular.[/QUOTE]

I saw it.
The thing is, it's not even my idea, I was just searching for info on ipV6 and internet related slowdown.

I read some of the posts on Digg, some of them even commented on the thread without actually reading it, which was quite interesting.
Others were windows users that probably have problems sending emails.
Then there were some that said "It worked for me". I'm happy for them.

---

### Post by tchock on 2006-06-25
Any way to stop the ipv6 module from *loading*? I'm not sure if that was the intended outcome of the modification to the aliases file, but I made the changes and if i do an

```
lsmod | grep ipv6
```

I still get the ipv6 module showing up. Should this module still be loading after the changes, or would I need to recompile my kernel to prevent this?

---

### Post by SumBudE on 2006-06-25
My results from using the Speakeasy test. These are averages of three tests both before tweak and after:

Before tweak
downstream - 4875 kbps
upstream - 4031 kbps

After tweak
downstream - 4957 kbps
upstream - 4003 kbps

Doesn't appear too significant here. What are others getting?

---

### Post by tchock on 2006-06-25
I think that's probably w/in the margin of error SumBudE. I don't believe the intent is to improve overall bandwidth but rather the speed with which the initial connection is made, since any attempt at an IPv6 lookup is skipped.

---

### Post by gReEnT3a on 2006-06-25
question:

Do we still need to do this after we done tweaking the values in about:config ?:KS

---

### Post by catlett on 2006-06-25
[QUOTE=SumBudE]My results from using the Speakeasy test. These are averages of three tests both before tweak and after:

Before tweak
downstream - 4875 kbps
upstream - 4031 kbps

After tweak
downstream - 4957 kbps
upstream - 4003 kbps

Doesn't appear too significant here. What are others getting?[/QUOTE]
You're missing the point. It is not about download speed after the connection is made. It is about the time it takes to connect. The speedtest is about download speed after a connection is made.
Here is an explanation about ipv6. The time being saved is before you connect to a site. It is not going to be measured by speakeasy's test.
>  IPv6 is short for "Internet Protocol Version 6". IPv6 is the "next generation" protocol designed by the IETF to replace the current version Internet Protocol, IP Version 4 ("IPv4").

Most of today's internet uses IPv4, which is now nearly twenty years old. IPv4 has been remarkably resilient in spite of its age, but it is beginning to have problems. Most importantly, there is a growing shortage of IPv4 addresses, which are needed by all new machines added to the Internet.

IPv6 fixes a number of problems in IPv4, such as the limited number of available IPv4 addresses. It also adds many improvements to IPv4 in areas such as routing and network autoconfiguration. IPv6 is expected to gradually replace IPv4, with the two coexisting for a number of years during a transition period. Since ipv6 is in the minority you loose time searching for ipv6. By disabling it you will only search with ipv4 and you will connect right away. As you can see from the quote they are coexisting so you wil noit be kept out by only using ipv4.

---

### Post by lathiat on 2006-06-25
From what I've seen, in most circumstances, this really doesn't make much of a difference, unfortunately there are a number of ISPs using DNS servers (such as DJBDNS) which simply does not respond to a AAAA request (it just ignores it) - this causes the browser to wait and timeout before the IPv4 request is followed.

Unfortnuately DJBDNS breaks spec in this way, as far as I can tell, BIND and other servers do not have this problem - but it doesn't *always* happen when djbdns is used, i've yet to track down the exact case it really causes issues.

It's also worth noting that this would help on high-latency links.

---

### Post by Z-Bo on 2006-06-25
This thread is kind of horrorfying to me.

Everyone is following the suggestion of the OP without really thinking or even asking if it is a good idea to do this.

IPv6 is the next generation for IP headers, basically.  Disabling it is fine -- IF you use an old router that does not support IPv6, then it makes sense to disable your IPv6 settings.

IF you have a present generation router, then you should probably keep your IPv6 settings.

Edit: The reason being is that it's bad enough ISPs are dragging their feeton IPv6 support.

---

### Post by fragos on 2006-06-26
Allowing for both IPV4 and IPV6 isn't a bug.  It allows you to communicate with both IP versions.  When V6 becomes more used, V4 will still be used for some time.  Given the comments in this thread, the whole issue of V4 vs V6 isn't well understood -- it is afterall down at the extreem geek level.  Ubuntu and other distros are permitting you to not have to understand but still have things work.  Sounds well planned and executed to me.

---

### Post by Adjutant on 2006-06-26
Well how do you know if you can use ipv6 or not?

---

### Post by dking1525 on 2006-06-26
worked for me!

before disabling ipv6:
2180 kbps down
585 kbps up

after disabling ipv6:
4223 kbps down
606 kbps up[U][I][B]

;)[/B][/I][/U]

---

### Post by tchock on 2006-06-26
[QUOTE=Z-Bo]This thread is kind of horrorfying to me.

Everyone is following the suggestion of the OP without really thinking or even asking if it is a good idea to do this.

IPv6 is the next generation for IP headers, basically.  Disabling it is fine -- IF you use an old router that does not support IPv6, then it makes sense to disable your IPv6 settings.

IF you have a present generation router, then you should probably keep your IPv6 settings.

Edit: The reason being is that it's bad enough ISPs are dragging their feeton IPv6 support.[/QUOTE]

I don't think you should be so serious about this -- all of it can be easily undone. How long do you think it'll be until it actually *matters* if we have ipv6 support enabled? Until that time, it makes just as much sense to just disable it...

I'm still wondering how to prevent the ipv6 module from loading, now that it's presumably not being used ... or any module that i don't want for that matter. I am suspecting it's a matter of compiling my own kernel, and if that's the case I probably won't bother.

---

### Post by catlett on 2006-06-26
[QUOTE=tchock]I don't think you should be so serious about this -- all of it can be easily undone. How long do you think it'll be until it actually *matters* if we have ipv6 support enabled? Until that time, it makes just as much sense to just disable it...

I'm still wondering how to prevent the ipv6 module from loading, now that it's presumably not being used ... or any module that i don't want for that matter. I am suspecting it's a matter of compiling my own kernel, and if that's the case I probably won't bother.[/QUOTE]
There is tons of stuff in /etc/modprobe.d but I don't know enough to mess with them. I know you can do stuff with the blaclist but I don't know how. There is also an /etc/modules and an /etc/modutils. My system is running too good to start messing with those files but you may want to. If you figure anything out, post. I'd love to understand more.

---

### Post by Ichinichi on 2006-06-27
> **dking1525]worked for me!

before disabling ipv6:
2180 kbps down
585 kbps up

after disabling ipv6:
4223 kbps down
606 kbps up[U][I][B]

 said:**
> [/I][/U]

I used [http://help.sbcglobal.net/dsl/speedtest/](http://help.sbcglobal.net/dsl/speedtest/) for the tests.

BEFORE:
27.675 Mbps
29.083 Mbps
27.071 Mbps
AVG = 27.943

AFTER:
28.365 Mbps
29.007 Mbps
28.023 Mbps
AVG = 28.555

DIFF = +0.612 Mbps

---

### Post by snowx1000 on 2006-06-27
The three additions/bad_list file did not seem to do anything for me. ifconfig still had an ipv6 address and "ip a | grep inet6" revealed it was still active. To fully disable ipv6 I had to change "alias net-pf-10 ipv6" to "alias net-pf-10 off ipv6". After the reboot all traces of ipv6 were gone. I did not need extra entries or anything.

---

### Post by brslade on 2006-07-07
zowie it works!!

---

### Post by buddy_krish on 2006-08-14
Wow....Great.....this certainly works.....  :-)

---

### Post by Frak on 2006-10-06
Dude you are more than a genius,
you are a saint!!!!!!!!!!!!!!!

---

### Post by Big Fish on 2006-10-15
My speeds were exactly the same before and after. :(

---

### Post by sharperguy on 2006-11-25
For everyone who is posting their speed test results etc, this should make no difference to actual bandwitdth speeds.

What should be faster is the time it takes to make a connection, which will make browsing the web feel alot faster since the actual page dosnt take much downloading.

But downloads will not be any faster since the time is actualy spent downloading rather than just trying to make a connection (allthough it has to do that too)

Hope that made sence

:)

---

### Post by asistentu on 2007-03-21
Can I rely on this speedometer: [http://promos.mcafee.com/speedometer/test_0150.asp](http://promos.mcafee.com/speedometer/test_0150.asp) ? Are the results credible?

---

### Post by Frak on 2007-03-21
> **asistentu said:**
> Can I rely on this speedometer: [http://promos.mcafee.com/speedometer/test_0150.asp](http://promos.mcafee.com/speedometer/test_0150.asp) ? Are the results credible?
looks right to me, I'd say yes.

[IMG]http://i116.photobucket.com/albums/o3/frak10/Speedometer_1000.gif[/IMG]

---

### Post by dancer on 2007-04-14
Snowx1000, thanks.  You rock!  That did the trick.

---

### Post by dreamersword on 2007-04-23
Isn't that file design so that it go down the list of protocols? Won't it use IPv4 before it uses IPv6? I want a reason why this teaks works before i go and change how my kernel is suppose to work? Do i need to do a reboot after making these changes? Did you emepty your catches before you did the before and after speed test. Why would your computer try using IPv6 if you were on an IPv4 network?

---

### Post by ihavenoname on 2007-04-23
> **dreamersword said:**
> Isn't that file design so that it go down the list of protocols? Won't it use IPv4 before it uses IPv6? I want a reason why this teaks works before i go and change how my kernel is suppose to work? Do i need to do a reboot after making these changes? Did you emepty your catches before you did the before and after speed test. Why would your computer try using IPv6 if you were on an IPv4 network?

Umm, the change is "temporary" if you get problems then you can just uncomment the lines and your back. I have noticed that it speeds up my firefox results, because it no longer attempts to go through Ipv6 protocols BEFORE ipv4. This can be a waste of time since most servers/isps w/e don't use ipv6 yet.  Yes you would have to reboot. Remember though, this is just something that works for a few of us, no one is selling you this so if you don't want to do it you don't have to. This should cause no harm to your computer in anyway as the effects are temporary. Worse case scenario has you booting with a life cd and undoing what you just did and you "should" be back.

---

### Post by jaywee on 2007-04-26
cool! It works fine!though I don't know how does it work!!:) :)

---

### Post by blackdevil on 2007-05-04
I got a noticible difference on Firefox(64bit) but when running my Firefox(32) it runs the same, much slower. Is this due to running a 32bit app under 64 environment?

---

### Post by Frak on 2007-05-04
> **blackdevil said:**
> I got a noticible difference on Firefox(64bit) but when running my Firefox(32) it runs the same, much slower. Is this due to running a 32bit app under 64 environment?
Yep, as I recall, 32 bit apps require emulation of a 32 bit processor as long as you are using a 64 bit enviroment.

---

### Post by moore.bryan on 2007-05-04
*this was awesome... downloads went from ~15000kbs to ~22000kbs.  sweet.*

---

### Post by starcraft.man on 2007-05-04
YAY! Neat tweak should have tried it earlier.

---

### Post by Endolith on 2007-05-29
Is there any good reason to leave this turned on?

---

### Post by Darrious on 2007-06-03
WOW!

This is amazing. I never thought that this would actually work, but it does. 

Right now I'm performing an upgrade to 7.04. I've been sitting here for about 6 hours for the upgrade. I was nearly pulling my hair out watching it go from 2 to 8 hours in a split second. Now, it went from 28k/s to 112k/s. And now instead of it saying 1-2 hours left, it says 18 minutes left. Thanks so much for this post. I saw the original post, but I still did not understand it. Funny thing is that I did not even have to reboot.

---

### Post by pardesi on 2007-06-09
yes i am posting here since i got noo concrete answers elsewhere.i did what is given here and my FF showed up unlike before but now each time i start ubuntu the FF(though the net is connected) shows nothing and once i reboot everythng is fine:(

---

### Post by jcurran on 2007-06-17
> **Endolith said:**
> Is there any good reason to leave this turned on?
Short answer:  No, if your system is not acting as server connected to the Internet.  If you do intend to have your system act as a server, reachable from the entire Internet community, then you should:  1) Get IPv6 connectivity, and 2) Leave it turned on.    Not an expectation for most users, and it's rather strange that the Ubuntu implementation requires this turned off if you don't have IPv6 connectivity.

---

### Post by Brian96 on 2007-06-17
> **jcurran said:**
> Short answer:  No, if your system is not acting as server connected to the Internet.  If you do intend to have your system act as a server, reachable from the entire Internet community, then you should:  1) Get IPv6 connectivity, and 2) Leave it turned on.    Not an expectation for most users, and it's rather strange that the Ubuntu implementation requires this turned off if you don't have IPv6 connectivity.

What about if you "share" your internet connection with a VM? Will changing this setting affect that?

Thanks.

---

### Post by exchequer598 on 2007-10-20
Woks well for me!! Thanks friend! :guitar:

---

### Post by CypherHackz on 2007-12-30
it really works. i use the tweak and i disable ipv6 in my firefox and wooossshhhh... i surf website faster than before.

btw i hope this thread will has thanks icon so i can add thanks to his post.

-cypher.

---

### Post by misfitpierce on 2007-12-30
Yeah I found this on google and it worked on friends computer... Didnt notice anything on my lappy though with connection speeds but w/e :)

---

### Post by hobo on 2007-12-30
This worked for me. All dns resolves appear to be much quicker. Thanks

---

### Post by coolbrook on 2008-01-12
It's a little bit snappier.  A worthwhile tweak.

---

### Post by polytropos on 2008-01-18
I'll add my name to this list--I can tell that Firefox is now running faster.  If you've gotten this far and still haven't tried it, why don't you already?

---

### Post by buks on 2008-01-24
Downloads are not faster (ADSL Speed Test to Hellkom using FTP below), but browsing does feel faster. Probably because of the whole trying ipv6 and falling back to ipv4 as mentioned in earlier posts. I just thought I would give some real world stats:

Before:
Try 1) 5120000 bytes received in 129.10 secs (38.7 kB/s)
Try 2) 5120000 bytes received in 129.07 secs (38.7 kB/s)
Try 3) 5120000 bytes received in 134.87 secs (37.1 kB/s)

After:
Try 1) 5120000 bytes received in 122.84 secs (40.7 kB/s) (this one almost got me exited)
Try 2) 5120000 bytes received in 129.02 secs (38.8 kB/s) (but alas, its not faster)
Try 3) 5120000 bytes received in 129.09 secs (38.7 kB/s) (yip, downloads are are not faster)

I guess I will leave this tweak in since it "feels faster" :)

PS. I have made a new years resolution to go completely FOSS, and it feels great. I am using the latest daily build of Hardy (2008-01-14). I chucked vista (I only used it because I could not get XP installed on my new 250G laptop HDD) still battleing to get an alternative for outlook which works with works exchange serve, but please lets not get into that fruitless windows vs linux debate since I have my legal XP which came with the laptop running in vmware server as well. :lolflag:

---

### Post by Endolith on 2008-01-24
> **buks said:**
> browsing does feel faster. Probably because of the whole trying ipv6 and falling back to ipv4 as mentioned in earlier posts.

I think that's the *only* reason it's faster.  It won't make downloads any faster.

---

### Post by wilsonmuse on 2008-01-24
Is there a way to check whether you are on an ipv4 or an ipv6 connection?

---

### Post by phyrewall on 2008-03-30
I understand that this has nothing to do with bandwidth. Not sure why people post their speed tests, but whatever... 

My question is: Has anyone checked to see if torrent applications are getting resolution slow-downs due to trying to find the ip6 address first?

---

### Post by robertchahine on 2008-03-30
should i add in 
> alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here.
alias ipv6 off --

those " -- "

---

### Post by trebor on 2008-03-30
I tried this teak as well.   It did not increase my speed, but I did notice that it started the test much faster.  If the speed indicator on [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)  is accurate.  Then while my overall speed remains the same, my browsing does seems faster due to firefox connecting faster.

Download Speed: 7083 kbps (885.4 KB/sec transfer rate)
Upload Speed: 515 kbps (64.4 KB/sec transfer rate)

---

### Post by tad1073 on 2008-03-30
[[IMG]http://www.speedtest.net/result/253066935.png[/IMG]](http://www.speedtest.net)

With speakeasy speed test:
```
Download Speed: 6324 kbps (790.5 KB/sec transfer rate)
Upload Speed: 430 kbps (53.8 KB/sec transfer rate)
```

---

### Post by Frak on 2008-03-30
> **trebor said:**
> I tried this teak as well.   It did not increase my speed, but I did notice that it started the test much faster.  If the speed indicator on [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/)  is accurate.  Then while my overall speed remains the same, my browsing does seems faster due to firefox connecting faster.

Download Speed: 7083 kbps (885.4 KB/sec transfer rate)
Upload Speed: 515 kbps (64.4 KB/sec transfer rate)

> **tad1073 said:**
> [[IMG]http://www.speedtest.net/result/253066935.png[/IMG]](http://www.speedtest.net)

With speakeasy speed test:
```
Download Speed: 6324 kbps (790.5 KB/sec transfer rate)
Upload Speed: 430 kbps (53.8 KB/sec transfer rate)
```

All this does is increase the speed that a request is processed and resent. This has NOTHING to do with bandwidth.

---

### Post by robertchahine on 2008-03-31
so can anybody help me?
when i modify the alias document , should i add those bars to the end of the three lines? ```
--
``` 
and thx.

---

### Post by robertchahine on 2008-03-31
ok, now everything works amazing but when i did these easy steps from this guide, it becames really more faster. try it.

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by mobileking on 2008-05-25
Thanks  ~ worked a lot good :)

---

### Post by Sealbhach on 2008-06-03
> **robertchahine said:**
> ok, now everything works amazing but when i did these easy steps from this guide, it becames really more faster. try it.

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

I did the tweaks on that page and it does seem a lot faster, especially after one major change - increasing the amount of cache memory for Firefox.

I’ve got 2GB of RAM so I changed the memory cache to 102400.

This is because when I put

about:cache

in the address bar it showed it was using more memory than I had available! It’s made a huge difference to page loading (along with all the other tweaks).

---

### Post by robertchahine on 2008-06-04
yep.it's a nice guide

---

### Post by Channon on 2008-06-04
> **Sealbhach said:**
> I did the tweaks on that page and it does seem a lot faster, especially after one major change - increasing the amount of cache memory for Firefox.

I’ve got 2GB of RAM so I changed the memory cache to 102400.

This is because when I put

about:cache

in the address bar it showed it was using more memory than I had available! It’s made a huge difference to page loading (along with all the other tweaks).

Are you using Firefox 3?  Just wondering if this will work in Hardy.

---

### Post by Sealbhach on 2008-06-04
> **Channon said:**
> Are you using Firefox 3?  Just wondering if this will work in Hardy.

Yes, the Firefox 3 beta that came with Hardy. All the same stuff was there in  about:config so I just did them.


.

---

### Post by gfern on 2008-06-04
Well, I gotta be honest... for me this is going the other way around. It feels like its actually slower when I apply the changes above. Could I be right? Could it have the opposite effect?

---

### Post by Sealbhach on 2008-06-04
> **gfern said:**
> Well, I gotta be honest... for me this is going the other way around. It feels like its actually slower when I apply the changes above. Could I be right? Could it have the opposite effect?

Do you mean page-loading? From what I gather, these tweaks have no effect on connection speed, so there might not be any objective test. Your connection speed might have slowed down temporarily?

For me, when I go to a site with lots of images and animations, the page loads a lot quicker (or seems to). As I have a dial-up modem, it makes a difference to the browsing experience.


.

---

### Post by gfern on 2008-06-04
> **Sealbhach said:**
> Do you mean page-loading? From what I gather, these tweaks have no effect on connection speed, so there might not be any objective test. Your connection speed might have slowed down temporarily?

For me, when I go to a site with lots of images and animations, the page loads a lot quicker (or seems to). As I have a dial-up modem, it makes a difference to the browsing experience.


.

YES, I mean page-loading. I checked for a difference on the speed and it was the same before and after the tweak. However, page-loading speed was noticeably reduced AFTER the tweak. I've edited and unedited the aliases file a few times and I keep getting the same result. Its actually faster with the default configuration... maybe I'm not doing it right. Do I have to add "--" after the lines? I don't add them, but I don't suppose that would do any difference, would it? 

Medical mystery, I get the shinning pager. ; )

---

### Post by Sealbhach on 2008-06-04
> **gfern said:**
>  Do I have to add "--" after the lines? I don't add them, but I don't suppose that would do any difference, would it? 

Medical mystery, I get the shinning pager. ; )

Sorry, I have no idea. If the default settings work better for you then stick to them, i suppose.:confused:


.

---

