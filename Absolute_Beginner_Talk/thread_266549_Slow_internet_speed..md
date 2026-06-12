---
title: "Slow internet speed."
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by tombean on 2006-09-27
Hey all,

I got myself Ubuntu Linux 6.06 a few days ago and I'm haveing a pleasant time with it. Cause I'm new to Linux I'm haveing problems setting it up.

Everything runns really fine, ---> except my internet.

It takes several seconds to only connect to Google start-up page (like 15 seconds).

I can't figure out what the probem is -- I also checked around for some information about it, but didn't see a solution which solved my problem.

I got Windows still on my 1st harddrive, Ubuntu Linux on my 2nd. I got a router which contains a modem, too. With Windows my surfing speed is like 10 times faster.

Although my downloading speed under linux is always around 80-110kbps -- same as my Windows system. 

I really don't get it.

Hope that someone of you can figure it out. Thanks for the great communtinty pages/forums/support!

Best Regards
-tom

---

### Post by wieman01 on 2006-09-28
Known trouble with **[COLOR="Red"]"ipv6"[/COLOR]**. Disable it globally (system-wide) as well as in Firefox. There solutions described in here somewhere.

---

### Post by xpod on 2006-09-28
Type "about:config" in the browser then "ipv6"....
and double click to change to true.

EDIT:ipv6 in the search field of course

;)

---

### Post by wieman01 on 2006-09-28
> **xpod said:**
> Type "about:config" in the browser then "ipv6"....
and double click to change to true.

EDIT:ipv6 in the search field of course

;)
Yes, mate. But that's not all, you should KNOW that. But if you had a useful link for the remaining stuff I would be very grateful.

---

### Post by wieman01 on 2006-09-28
Found it... The remaining bit is here:

[http://www.ubuntuforums.org/showthread.php?t=87798&]("http://www.ubuntuforums.org/showthread.php?t=87798&")

And XPOD: Stop following me! ;-)

EDIT:
And I stop being a step ahead of your...

---

### Post by xpod on 2006-09-28
Nope....I just see all the experts banding that advice about with little or no explanation as to what it does but this is what i read...:D 

[http://ubuntuos.wordpress.com/2006/07/28/howto-speed-up-firefox-internet/](http://ubuntuos.wordpress.com/2006/07/28/howto-speed-up-firefox-internet/)

---

### Post by xpod on 2006-09-28
If you had gave the chap the "full" info in the first place i wound`nt need to keep keeping you right would i;) :-# 

LOL...Good day mate,off work again with my boy who fell out the tree so you got me all day again:mrgreen:

---

### Post by tombean on 2006-09-28
Wow!!!

My internet is like flying away now :D 
Faster than in Windoze Xp:cool: 

Thanks for the great support and the help!
1 more reason to completely remove Windoze from the HD...

Thx all
--tom

---

### Post by uBo on 2006-09-29
my internet connection is deteorating for the last few days and today is really bad.

it is definitelt ubuntu, because windows is doing just fine in terms of internet speed.

i did the two tricks above but to no avail. any other suggestions??

I am using the Mozilla Firefox bt the way.

---

### Post by xpod on 2006-09-29
Try "swiftfox"..dont know much more than that im afraid.
Mabey it`s not a prob with FF...??

---

### Post by uBo on 2006-09-29
it is definitely not firefox, it is the same with opera.

very strange, because i am using ubuntu for at least 2 months and it was fine, it must have been some of the last uprages. please help me, otherwise i am forced to go back to the dreaded MS product.

---

### Post by bulldog on 2006-09-29
> **uBo said:**
> it is definitely not firefox, it is the same with opera.

very strange, because i am using ubuntu for at least 2 months and it was fine, it must have been some of the last uprages. please help me, otherwise i am forced to go back to the dreaded MS product.

Feels a little like blackmailing us....................:D :D

---

### Post by xpod on 2006-09-29
You have used Ubunto fine for 2 months but suddenly you encounter a problem and will give up and return straight to M$.......mmmmmmmm

I wish i knew how to offer you more assistance but this is not a problem i have really had much trouble with,Although i have had many many others and would not know how to give in so easily.
Mabey someone who knows more about these things can help you

---

### Post by uBo on 2006-09-29
heh, do not worry i will not give in so easily but if ultimately i do not solve the problem i really do have to use another os. its unbearably slow. and because for the next few months i really will not have too much time for installing a new distro or reinstalling ubuntu i will have to go back to checking for spyware, viruses and all that crap in MS. 

once again, the connection is not slow in itself, opera and firefox are extremely slow in downloading sites. and it happened "almost" overnight. windows is doing fine in terms of internet speed.

the IPv6 stuff is set correctly according to the links you gave in this thread.

---

### Post by bulldog on 2006-09-29
Well I'm only using swiftfox but it's almost the same as firefox,and no prob's here.

Have no idea what slows your connection so badly,sorry to say.:(

---

### Post by wieman01 on 2006-09-29
Could you tell us a bit more about your network? E.g. 

1. What network is it (wireless, ethernet)?
2. What hardware are you using (adapter)?
3. DHCP, encryption?
4. Firewall?
5. What exactly is slow and how does it manifest itself?
6. If wireless, do you use any kind of tool: wireless assistant, wifi radar, etc.

Please try to describe your problem a bit and then we continue...

---

### Post by uBo on 2006-09-30
> **wieman01 said:**
> Could you tell us a bit more about your network? E.g. 

1. What network is it (wireless, ethernet)?
2. What hardware are you using (adapter)?
3. DHCP, encryption?
4. Firewall?
5. What exactly is slow and how does it manifest itself?
6. If wireless, do you use any kind of tool: wireless assistant, wifi radar, etc.

Please try to describe your problem a bit and then we continue...

1. Wireless DSL, PPPoE connection, no problem with that
2. Centrino Wireless Card
3. No encription as far as I know
4. Firestrter is running sometimes, is off a the moment, and the slowness is there.
5. Loading websites is slow initially after a click, then normal. It needs seconds to do something (Opera and Firefox). Same with Thunderbird, it needs a few seconds before downloading the new mail at, I think, a normal speed. This is so painfully slow since yesterday. I have the feeling it was getting slower for a while though.
6. No tools.

Thanks for the help. It is terribly frustrating.

---

### Post by FireFighter on 2006-09-30
uBo, I don't know the answer to your problem, but wanted to let you know that I had the same problem and gave up on Ubuntu. There was no post until yours that I could find. I really wanted to use Ubuntu (still do for that matter). I am following your post and hope that it can be solved! Then, I will become a happy Ubuntu user!

---

### Post by wieman01 on 2006-09-30
> **FireFighter said:**
> uBo, I don't know the answer to your problem, but wanted to let you know that I had the same problem and gave up on Ubuntu. There was no post until yours that I could find. I really wanted to use Ubuntu (still do for that matter). I am following your post and hope that it can be solved! Then, I will become a happy Ubuntu user!
But you have also disabled IPV6, right?

---

### Post by wieman01 on 2006-09-30
UBO:

Do you use DHCP by chance? I have helped another users with setting up Static IP rather than DHCP and it DID make a big difference in terms of performance:

[http://www.ubuntuforums.org/showthread.php?t=265955]("http://www.ubuntuforums.org/showthread.php?t=265955")

---

### Post by uBo on 2006-10-01
@wieman01

somehow miracolousy the problem solved iself. internet is fast again. i cannot tell why.

i did not have DHCP, it was not the problem. i played with the other firewall settings, but nothing immediately changed. then after a new boot some time later things a woring normally again. among others i disabled the ICMP filtering.

thanks for the interest and for trying to help.

i hope the problem does not occur again.

---

