---
title: "evolution has broken pipes"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by kathytaylor on 2008-01-06
my evolution for emails use to work until a few days ago now it wont work i get a message saying broken pipes when  i push send/received.i have tryed redoing my emails account but still get nothing  i do have Ubuntu dapper 6.06

---

### Post by daverich on 2008-01-06
that sounds like theres a problem with your email server, try contacting your isp if they provide your email account.

Kind regards

Dave Rich

---

### Post by kathytaylor on 2008-01-06
my isp provider dont deal with ubuntu only with widows xp

---

### Post by kathytaylor on 2008-01-06
bump

---

### Post by dcstar on 2008-01-06
> **kathytaylor said:**
> my evolution for emails use to work until a few days ago now it wont work i get a message saying broken pipes when  i push send/received.i have tryed redoing my emails account but still get nothing  i do have Ubuntu dapper 6.06

Post the exact messages (or screenshots), and try a reboot.

---

### Post by kathytaylor on 2008-01-06
this is the screen shot

---

### Post by dcstar on 2008-01-07
> **kathytaylor said:**
> this is the screen shot

As it clearly says in the screenshot: "Host lookup failed".

You have an incorrect setting in your e-mail account setup, there is no such thing as "bigpond" that resolves on the Internet.

Find your ISPs instructions for setting up your e-mail account and follow them **exactly**.

---

### Post by kathytaylor on 2008-01-07
i did everthing i did before when i first set up the email but still nothing

---

### Post by ellis rowell on 2008-01-07
In the UK, very few people know about Linux and even fewer know about Ubuntu. I have used Thunderbird for a long time (under Windoze and Ubuntu), I have never come across this problem. It should not matter what the operating system is if the settings are correct.

---

### Post by kathytaylor on 2008-01-07
i just cant work out why all of a sudden it just stopped working and why i cant get it working again

---

### Post by dcstar on 2008-01-07
> **kathytaylor said:**
> i did everthing i did before when i first set up the email but still nothing

The screenshot shows that Evolution is trying to do a DNS lookup on something called "bigpond" (which does not exist), it probably should be bigpond.com or bigpond.net.

Check your settings.

---

### Post by Kevin Funnell on 2008-01-07
Kath,  
I agree with David -  if you are on a Bigpond dial-up service then it is [email]username@bigpond.com[/email]  if you are on broadband then it is: [email]username@bigpond.net.au[/email].   Setting-up or editing your account from within Evolution / Edit / Preference 
Old Kevin

---

### Post by kathytaylor on 2008-01-07
when i do it i put bigpond.net.au and it still dont work

---

### Post by caravel on 2008-01-07
From the screenshot it looks as if the hostname is wrong in your account setup.  It could be just the name of the "service" though and not the actual hostname that the error is showing, check that the pop3 and smtp servers are entered correctly and that you're not confusing the service name with them, it's a while since I've used evolution so I can't remember the exact layout.

If this fails to help then you need to check your account details again and re-enter them exactly.  If this still doesn't work contact your ISP.  If they won't help you because you're running Ubuntu then they're not fulfilling their part of the contract.  There is no way they can dictate what OS you use.  They should at least be able to send you the correct settings by post.  For windows, ISPs usually use .ins script files to install all of the email, connection and browser settings in one go.  If you're on dial up this is very likely to be the case anyway.  You may have this with the disc your ISP sent you to install or it may be in a file they emailed to you?  Also if they can send you the installation file(s) again to a remote mail account such as gmail, hotmail or yahoo account, then you can obtain the .ins from that and print it off from another machine and obtain the correct settings from it for your email.  I assume your web browsing is ok?  No problems with DNS lookups there?

---

### Post by kathytaylor on 2008-01-07
web browser is working good and i dont use dial up .with my isp provider if you use a dual boot system they wont help you unless you use windows xp as i cant use my windows xp they wont help.

---

### Post by caravel on 2008-01-07
Why can't you use your Windows XP?  Is your system a dual boot or is there another problem?

---

### Post by kathytaylor on 2008-01-07
well windows xp has a corruption in it that happen last year .

---

### Post by caravel on 2008-01-07
Have you tried safe mode?  I'm suggesting this as it may be a good way for you to retrieve your email account settings?

---

### Post by kathytaylor on 2008-01-07
this is every thing i have been doing with the account this is screen shots of it .

---

### Post by caravel on 2008-01-07
and you're certain that those are the correct SMTP and POP hostnames?  Can you try pinging those hostnames from a terminal and post the output?

---

### Post by kathytaylor on 2008-01-07
yes i am certain they are the correct host name and stmp ,how would i do the other thing the ping

---

### Post by Kevin Funnell on 2008-01-07
kathy,
While the Forum members works through your Evolution problem and I believe you said you have Internet Access, you could log into Bigpond's Web mail - fill in the requested info (Name Password etc) from there you can receive and send e-mails that is on the Bigpond Server.  Hope this help until the problem is fixed.
At work, Old Kevin

---

### Post by caravel on 2008-01-07
Open a terminal and do:

```
[B]ping smtp.bigpond.net.au
ping mail.bigpond.net.au[/B]
```

I just tried both of those and couldn't find either (This is from Windows because I'm at work):

```
C:\>ping smtp.bigpond.net.au
Ping request could not find host smtp.bigpond.net.au. Please check the name and
try again.

C:\>
```

Example:-
```
C:\>ping mail.btinternet.com

Pinging pop-smtp1-f.bt.mail.vip.ird.yahoo.com [217.146.188.192] with 32 bytes of
 data:

Reply from 217.146.188.192: bytes=32 time=21ms TTL=59
Reply from 217.146.188.192: bytes=32 time=19ms TTL=59
Reply from 217.146.188.192: bytes=32 time=22ms TTL=59
Reply from 217.146.188.192: bytes=32 time=19ms TTL=59

Ping statistics for 217.146.188.192:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 19ms, Maximum = 22ms, Average = 20ms

C:\>
```

This points to the hostnames being somehow incorrect.  In fact if I google those hostnames I see only one resullt!  This is highly unlikely unless no one has ever had a problem before.  Googling the BT hostnames gave pages and pages of results.

Could you instead try the following hostnames:

SMTP: "mail-hub.bigpond.net.au" or "mail.bigpond.com"
POP: "pop-server.bigpond.net.au"

Those are the only possibilities I could find and are all pinging ok.

---

### Post by Kevin Funnell on 2008-01-07
Kathy,

If you goto: [http://www.bigpond.com/help/email/](http://www.bigpond.com/help/email/) I think it will give you all the answers you need. To setuo your email account goto Set up Microsoft Outlook 2000/XP to send and receive your BigPond email (same Web Page just pan down)  Goto Step 4 & 5  as the information required is the same for what ever email program is used.
Old Kevin

---

### Post by Seisen on 2008-01-07
You need to enter the port numbers so they look like this:

```
mail.bigpond.com:25 
``` for smtp 

and for POP

```
mail.bigpond.com:110
```

---

### Post by dcstar on 2008-01-07
> **Kevin Funnell said:**
> Kathy,

If you goto: [http://www.bigpond.com/help/email/](http://www.bigpond.com/help/email/) I think it will give you all the answers you need. To setuo your email account goto Set up Microsoft Outlook 2000/XP to send and receive your BigPond email (same Web Page just pan down)  Goto Step 4 & 5  as the information required is the same for what ever email program is used.
Old Kevin

Exactly, Bigpond have obviously changed their mail server names and no longer use the ones currently configured.

I would imagine that they sent out something informing all users to change (probably quite a while ago), but as we can see, not all people have changed.

---

