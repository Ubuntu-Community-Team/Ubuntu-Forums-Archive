---
title: "slow web browsing"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by s_x_g_t on 2007-01-02
I have pipelining enabled and set to 40 requests and i thought doing that would boost Mozilla. It hasn't sometimes its so slow its like I have dial up!  I ran a band width test ( i am on wireless) and i got 400kbs one day and 1200 the next.  It seems to be pretty inconsistent but has never been as fast as my laptop running from the same router.. 

any tweek ideas?

---

### Post by jpeddicord on 2007-01-02
Try setting Pipelining to 8. Anything more than that and the connection quality may drop a little bit.

Jacob

---

### Post by s_x_g_t on 2007-01-02
> **jacobmp92 said:**
> Try setting Pipelining to 8. Anything more than that and the connection quality may drop a little bit.

Jacob

Hmm   the tutorials said between 30 - 40. I think i have it to 40 on my laptop and its just fine. Ill let you know it putting it at 8 makes a difference or  not, it seems to be running very smooth tonight how ever.   TY

---

### Post by s_x_g_t on 2007-01-02
ok so i set it to 8 on my linux machine and 30 on my  Macbook.   The macbook loaded a page in 1 full second.  Linux took about 7 seconds.

---

### Post by jpeddicord on 2007-01-02
Hmm, I may have been looking at a different setting.

If your connection wired or wireless?

---

### Post by s_x_g_t on 2007-01-02
> **jacobmp92 said:**
> Hmm, I may have been looking at a different setting.

If your connection wired or wireless?

wireless.  This is also a dual boot computer. IN windows its snappy fingers. with ubuntu its a slug. I know i have excellent signal.

---

### Post by r4ik on 2007-01-02
Setting pipelining to 40 works like a charm with ipv6 blacklisted also browsing gets more normal.
Thanks !
(wired connection from modem/router)

---

### Post by s_x_g_t on 2007-01-02
> **r4ik said:**
>  with ipv6 blacklisted )


IDK what that is.


<==noob sauce

---

### Post by jpeddicord on 2007-01-02
Don't go worrying about IPv6 just yet, it will only mess around with the problem even more.

Wireless does make a difference here, as some chipsets do not work well with Ubuntu. Post your wireless card + Ubuntu version and I may be able to help you out. :) 

Jacob

---

### Post by r4ik on 2007-01-02
about:config =>IPV6 set it to true
To blacklist it globaly as root,

echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

---

### Post by s_x_g_t on 2007-01-02
i need the pre command to run as root.    sudo?

---

### Post by r4ik on 2007-01-02
Type about:config in the location bar type ipv6 and double click it.
see if it works.
Than you might concider to kill it not needed though.

---

### Post by s_x_g_t on 2007-01-02
it was off and now its on.

---

### Post by r4ik on 2007-01-02
You're right it is ipv .
stupid typo, sorry.

---

### Post by Frak on 2007-01-02
> **s_x_g_t said:**
> wireless.  This is also a dual boot computer. IN windows its snappy fingers. with ubuntu its a slug. I know i have excellent signal.
I've had problems with mine, I recompiled the kernel with the closed source driver on mine though, because apparently, if the drivers weren't open source by the Ubuntu developers, the play it safe and underpower the card, which can cause horrible reception.

---

### Post by s_x_g_t on 2007-01-02
> **Frak said:**
> I've had problems with mine, I recompiled the kernel with the closed source driver on mine though, because apparently, if the drivers weren't open source by the Ubuntu developers, the play it safe and underpower the card, which can cause horrible reception.

I took that into consideration.   Iam going to do a bandwidth test now and  do some bench marking


OHhh snapp the macbook just got burned!!

---

### Post by r4ik on 2007-01-02
> **s_x_g_t said:**
> it was off and now its on.

Any difference ?
If not you might want to redo it the same way.

---

### Post by s_x_g_t on 2007-01-02
hmm  ... its noticeably faster but 

522 kbps  for Ubuntu  


yet..   1.2MB/s  for the macbook  and its DL/ULing a movie

---

### Post by r4ik on 2007-01-02
OHhh snapp the macbook just got burned!![/QUOTE]

You must be joking there is no way changing IPV could do that.
if it is it sucks badly.

---

### Post by s_x_g_t on 2007-01-02
> **r4ik said:**
> OHhh snapp the macbook just got burned!!

You must be joking there is no way changing IPV could do that.
if it is it sucks badly.[/QUOTE]

it loaded winn-dixie.com noticeably fast then my macbook did.    before hand  it was 6  or 7 full seconds slower.   and these arnt on the cache.

---

### Post by r4ik on 2007-01-02
Got it.
Scared me for a moment :)

---

### Post by s_x_g_t on 2007-01-03
It looks like i got my hopes up to soon. Its being a SLUG again. so i did a band width test and it said

1.1 megabits per second
Communications 1.1 megabits per second
Storage 134.9 kilobytes per second
1MB file download 7.6 seconds



it took forever to run the test tho. maybe a full 40 seconds....  so i too watched my Network monitor and it has dips. It will being 100/bs...102/bs   then dip to zero for a second and go back up to 90/bs the dip to zero again. this applys to sent and received  and it is simultaneous

---

### Post by richpor_1 on 2007-01-03
I have posted in other posts as well.

This is a me2 post.  

I have disabled all the IPV6 stuff, fixed the resolv.conf, blacklist. etc..etc..etc..  But the DNS resolution takes forever in 6.10 and is lightning fast in XP. 

 I am running a gigabit (on board) Yukon M]arvel adapter with the drivers included in Edgy.  Could this be the problem?](*,) 

Thanks,

---

### Post by s_x_g_t on 2007-01-03
...so my antenna broke off...

---

### Post by Frak on 2007-01-03
Like broke like have to replace, or broke like just fell off...?

---

