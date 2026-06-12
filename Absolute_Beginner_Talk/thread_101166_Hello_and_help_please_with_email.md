---
title: "Hello and help please with email"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by MartinS on 2005-12-09
Hello to all out there in Ubuntuland. First a few details.

I have been a pc twiddler for years, pre PC even, can recall playing with a PDP8 and 8 inch drives. Though these last years have been Windows driven I have always kept space on my drives for something else to play with from time to time. Right now I'm out to prove, for no good reason I guess, that I do not need any 'paid for' software. I have played with various flavours of Linux over the last few years but all seem to have fallen short of both my needs and expectations one way or another, but I'm always ready to try another flavour so here I am with Ubuntu 5.10 installed on partitions of both my desktop and laptop.

Installation was a great success in both cases and though I am less than enamoured with the menu appearance and the lack of some common entries all seemed to be good. Internet access seemed simple enough but then I ran into two snags both of which have me scratching my head and about which I seem to feel totally alone in having to resolve.

The first problem concerns both my desktop machine and my laptop machine and seems to affect all email programs. Despite having entered my details exactly as provided by my ISP and as used in my Windows email programs I am unable to get them to log on to the server and retrieve mail or send it. This affects both Evolution and Thunderbird and on the desktop it affects Opera as well. If I am unable to fix this there seems little point continuing and I really don't know where to start.

My second problem relates only tomy laptop. This is a recent Fujitsu S series lifebook and seems to work very well with Ubuntu but for one small snag at the moment. Both the Broadcom ethernet adaptor and the Intel wireless adaptor work fine but switching between them seems difficult without rebooting. In my Windows envirionment I can plug an play with these two as I wish and would ideally like to do the same in Ubuntu. Is there anyway that I can make this happen?

I would be happy to receive help on either of the above two points. I don not mind terminal typing though I would hope that any solution would be simple to incorporate on a permanent basis. I don't know if either point has been previously addressed, Google searches seem to indicate not.

Best wishes and thanks,

Martin

---

### Post by xmastree on 2005-12-09
I know you've checked it, but check again the outgoing smtp server. In thunderbird it's under Edit > Account settings.

Note the name of the server, **smtp.yourisp.com** and see if you can ping it. You should be able to. If not, it might be a DNS problem, since it affects all email programs.

---

### Post by MartinS on 2005-12-09
Thanks for the reply. Some success. Pinging both the POP and SMTP servers returns what look like aceptable results.

Just a further note, I see in Thunderbird that when I click on Get Mail I can see 'looking up XYZ' then 'Conecting to XYZ' but it just seems to stick there.

Hmm, what next?

Thanks,
Martin

---

### Post by xmastree on 2005-12-09
Check the username/passwords in edit > Preferences > Advanced
Are you using the correct port?
Can't think of much else...

---

### Post by MartinS on 2005-12-09
After my ping success I thought I would try fetchmail. Here is what I got.

martin@fujlin:~$ fetchmail -ku XYZ pop.myisp.com
Enter password for [email]XYZ@pop.myisp.com[/email]:
29 messages (25 seen) for XYZ at pop.myisp.com.
skipping message [email]XYZ@pop.myisp.com[/email]:1 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:2 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:3 not flushed

etc

skipping message [email]XYZ@pop.myisp.com[/email]:23 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:24 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:25 not flushed
reading message [email]XYZ@pop.myisp.com[/email]:26 of 29 (3454 header octets) ...fetchmail: SMTP connect to localhost failed
fetchmail: SMTP transaction error while fetching from pop.myisp.com
fetchmail: Query status=10 (SMTP)
martin@fujlin:~$
 
Seems I can get to the server so think the problem is my configuration.

Any more ideas?

Regards
Martin

---

### Post by deNoobius on 2005-12-09
I don't know if this is it in your case, but one thing I noticed when I set up my email is that you have to have the right type of security setting for your password login, or your email will just hang as you describe.  There are a number of possibilities, and you might want to try each one.

---

### Post by MartinS on 2005-12-09
I think that could be a worthwhile point to check. I have been through all of the Opera possibilities and tried to check 'supported types' in Evolution but that hangs as well.

Would be nice to find a box somewhere that just needs ticking

Getting quite grumpy with this now.

Martin

---

