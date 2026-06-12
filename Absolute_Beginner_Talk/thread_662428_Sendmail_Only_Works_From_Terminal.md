---
title: "Sendmail Only Works From Terminal"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by BlueKnight84 on 2008-01-08
Hi again everyone.

I've been having a problem with Sendmail that I could never diagnose very well here on this forum but hopefully it's easier for all you helpful people to understand now that I've had some more success/failure with it.

My Ubuntu server (7.04) has Sendmail as its mta.  I created a .forward file for my user account (which has root access, by the way) and when I'm in Terminal, I can send email to myself fine using the following command:

[INDENT]sendmail [email]exampleuser@domain.com[/email][/INDENT]

I check the forwarded mail account and sure enough, I got it.  But when I use other mail accounts like my hotmail or gmail to test "exampleuser@domain.com", the forwarded mail account never receives it.

What makes it worse is that I have two other users' accounts who have completely fine working .forward files but 3 others that don't work, including mine.  Does this problem have a source?  ANY information you can provide can only help me at this point!

---

### Post by blueridgedog on 2008-01-09
How about some more background.  

Is your sendmail server working in all other regards?  ie you can receive email from remote systems and that email is delivered into a mailbox on the system for your user account?

This would imply that your mail server is setup and running, that the domain into which you have placed it (example.com) has appropriate MX records (mail.example.com) pointing to your host and that your sendmail configuration is setup to accept mail to the domain in question.  Also implied is that your ISP is allowing inbound traffic on the smtp port.

Also, the email that is send using these remote accounts (hotmail etc), where does it end up?  Do they get a bounce?  What does the bounce contain?

---

### Post by BlueKnight84 on 2008-01-09
> **blueridgedog said:**
> How about some more background.  

Is your sendmail server working in all other regards?  ie you can receive email from remote systems and that email is delivered into a mailbox on the system for your user account?

To be honest, I am just now learning Ubuntu and am taking over a server for a school club.  All I know is that we use Sendmail for the site (php/mysql) and all mail sent to users goes to an address assigned by a .forward file.  When you ask about receiving mail from remote systems and checking to see if it was delivered to a mailbox on the system for my user account, I've Google'd how to check my mailbox using command line in Sendmail, and can't find the appropriate command.

When I send mail from my remote accounts (Hotmail, etc.), I receive "Delivery Status Notification (Delay)" in the subject (on my remote account) and it says:

[INDENT][INDENT]This is an automatically generated Delivery Status Notification.
 
THIS IS A WARNING MESSAGE ONLY.
 
YOU DO NOT NEED TO RESEND YOUR MESSAGE.
 
Delivery to the following recipients has been delayed.
 
       [email]xxx@www.xxx.org[/email]
 
 
 

    --Forwarded Message Attachment--
    From: [email]xxx@hotmail.com[/email]
    To: [email]xxx@www.xxx.org[/email]
    Subject: test
    Date: Tue, 8 Jan 2008 23:14:12 -0500






    test[/INDENT][/INDENT]



My forwarded email account (assigned from my .forward file) says:



[INDENT][INDENT]From:  	Mail Delivery Subsystem <MAILER-DAEMON@xxx.org>  	Wednesday - January 9, 2008 2:34 AM
To: 	<xxx@www.xxx.org>
Subject: 	Warning: could not send message for past 4 hours
Attachments: 	status.txt (305 bytes) 	[View] [Open] [Save As]
headers.txt (573 bytes) 	[View] [Open] [Save As]
Mime.822 (2703 bytes) 	[View] [Save As]
   **********************************************
   **      THIS IS A WARNING MESSAGE ONLY      **
   **  YOU DO NOT NEED TO RESEND YOUR MESSAGE  **
   **********************************************

The original message was received at Tue, 8 Jan 2008 21:53:25 -0500
from [www.xxx.org](www.xxx.org) [127.0.0.1]

  ----- Transcript of session follows -----
<xxx@hotmail.com>... Deferred: Connection timed out with mx1.hotmail.com.
Warning: message still undelivered after 4 hours
Will keep trying until message is 5 days old[/INDENT][/INDENT]


If you need more information or have further questions, PLEASE ask.  I'm at my wit's end with this.

---

### Post by blueridgedog on 2008-01-09
Ok, some questions.

Is this working for anyone?  Was this ever working for anyone?  Your original post implied it was a specific error with your account.  I am trying to determine if you need help setting up sendmail (complex) or getting your .forward to work (simple).

Can you post the output of 

```
ls -al /var/spool/mail
```

Log into your user account and type:

```
mail
```

If you are told there is no mail program, try:

```
sudo apt-get install mailutils
```

Then try mail.  Do you have any mail on the system?

Then send me an email from the command line of your server (replace AT with @)

```
mail jervinATgmail.com
```

Type me an email and end with a "." (dot without the quotes) on a line by itself.

---

### Post by BlueKnight84 on 2008-01-09
> **blueridgedog said:**
> Ok, some questions.

Is this working for anyone?  Was this ever working for anyone?  Your original post implied it was a specific error with your account.  I am trying to determine if you need help setting up sendmail (complex) or getting your .forward to work (simple).

You're right, it is a specific error with my user account.  Two other users have working accounts.  My .forward file works , i.e., if I do the command: ```
sendmail *myself*
```, I'll get mail in my forwarded remote mail account.  But any mail sent from a Hotmail or Gmail and the like to *myself@domain.com* don't end up in my forwarded remote mail account.

> **blueridgedog said:**
> Can you post the output of 

```
ls -al /var/spool/mail
```

Here it is:

```
lrwxrwxrwx 1 root root 7 2007-02-01 19:39 /var/spool/mail -> ../mail
```

> **blueridgedog said:**
> Log into your user account and type:

```
mail
```

If you are told there is no mail program, try:

```
sudo apt-get install mailutils
```

Then try mail.  Do you have any mail on the system?

I had to install mailutils and there appears to be 20 new messages.

> **blueridgedog said:**
> Then send me an email from the command line of your server (replace AT with @)

```
mail jervinATgmail.com
```

Type me an email and end with a "." (dot without the quotes) on a line by itself.

I went ahead and did this for you, but I should tell you: I performed ```
mail test@hotmail.com
``` and never got it.  I'm assuming you won't, either.

I hope this is fixable and I want to thank you for helping me!

---

### Post by BlueKnight84 on 2008-01-09
Interesting side note...

Remember when I said that when, from the command line, I

```
mail user@hotmail.com
```

that it doesn't work?  Well I tried emailing the remote mail account that's specified in my .forward file, and I got it.  (for example, "user@mail.com")

I thought maybe Hotmail is just being picky, but I tried the same thing with a Gmail account, and it doesn't work, either.  Hopefully this helps somehow.

---

### Post by blueridgedog on 2008-01-09
Ok, so it works for others, but not for you, that is a good sign.  So assuming your domain is domain.com and you have user1 and user2, and user1 has a .forward going to a hotmail account and user2 has a .forward going to a gmail account, it has been shown that user2 can get email, but user1 can not.

Show me:

```
cat ~/.forward
```

and 

```
cat /etc/aliases
```

Have you considered trying another email address to forward your email to?  (just on the off chance that the reason for the failure is that hotmail is rejecting your forwarded email).

---

### Post by blueridgedog on 2008-01-09
Additionally:

Try a test email to your hotmail account (I don't know your hotmail address, but let us call it test)

```
mail test@hotmail.com
```

Remember the dot on a line by itselft to end the email.  Something like:

```
james@ripstop:/etc/mail$ mail test@hotmail.com
Cc: 
Subject: test
This is a test.
.
james@ripstop:/etc/mail$ 
```

Then after you send it, try

```
tail /var/log/mail.err
```

You can try this command a bit and see reveals any errors.

Finally, you can see if there is a pile of mail qued to send:

```
sudo ls /var/spool/mqueue
```

---

### Post by BlueKnight84 on 2008-01-09
> **blueridgedog said:**
> Ok, so it works for others, but not for you, that is a good sign.  So assuming your domain is domain.com and you have user1 and user2, and user1 has a .forward going to a hotmail account and user2 has a .forward going to a gmail account, it has been shown that user2 can get email, but user1 can not.

Show me:

```
cat ~/.forward
```

```
sga_kctd@mail.ucf.edu
```

> **blueridgedog said:**
> and 

```
cat /etc/aliases
```

Sure.  Just to tell you, I changed the name to *original admin* here on this post.

```
# Added by installer for initial user
root: *original admin*
```

> **blueridgedog said:**
> Have you considered trying another email address to forward your email to?  (just on the off chance that the reason for the failure is that hotmail is rejecting your forwarded email).

I didn't mean to confuse you about the Hotmail and Gmail accounts.  I have a Hotmail and Gmail account, but those aren't the ones included in my .forward file.  I have tested my .forward file with them, but at the moment I'm testing it with the email the school provided to me.

Remember how I said that there are two working users' .forward files?  Well, one of them uses a Gmail account, and the other uses their email the school provided.  So either way, it *should *work.

I'm assuming there's a config file I need to tinker with, but I can't understand why the same configuation would work for two users, but not any of the others.  I observed the creation dates of the working users and the non-working users, and they're only minutes apart.  If you don't think you can help me, you can tell me.  But hopefully, there's something you can think of to try before we give up this thing!

---

### Post by BlueKnight84 on 2008-01-09
> **blueridgedog said:**
> Additionally:

Try a test email to your hotmail account (I don't know your hotmail address, but let us call it test)

```
mail test@hotmail.com
```

Remember the dot on a line by itselft to end the email.  Something like:

```
james@ripstop:/etc/mail$ mail test@hotmail.com
Cc: 
Subject: test
This is a test.
.
james@ripstop:/etc/mail$ 
```

Then after you send it, try

```
tail /var/log/mail.err
```

You can try this command a bit and see reveals any errors.

I think you're on to something.  Here's what came up:

```
Jan 8 20:08:02 www sendmail[4486]: My unqualified host name (www) unknown; sleeping for retry
Jan 8 20:08:06 www sm-mta[5343]: My unqualified host name (www) unknown; sleeping for retry
Jan 8 20:08:12 www sm-msp-queue[5402]: My unqualified host name (www) uknown; sleeping for retry
Jan 8 20:08:55 www sendmail[5859]: My unqualified host name (www) unknown; sleeping for retry
Jan 8 20:09:37 www sendmail[4486]: unable to qualify my own domain name (www) - using short name
Jan 9 18:04:32 www sendmail[8557]: NOQUEUE: SYSERR(mark): can not chdir(/var/spool/mqueue/): Permission denied
Jan 9 18:06:33 www sendmail[8592]: NOQUEUE: SYSERR(mark): can not chdir(/var/spool/mqueue/): Permission denied
```


> **blueridgedog said:**
> Finally, you can see if there is a pile of mail qued to send:

```
sudo ls /var/spool/mqueue
```

All kind of "djm04MrSov012189" looking lines popped up.  I hope we're on to something!  Thank you so much for all your help thus far!!!

---

### Post by blueridgedog on 2008-01-09
OK, several things.

First:  It looks like sendmail is choking on something.

Lets see the permissions it is complaining about:

```
sudo ls -al /var/spool
```

Then lets see why it is unhappy with it's host name.  Send the following if you can.

```
cat /etc/hosts

cat /etc/mail/local-host-names 
```

Your hosts file needs an entry with the IP of the host system and its host name and its fully qualified host name.  For example, my system is 192.168.1.102 and is named ripstop and is in the kites.org domain, so:

```
192.168.1.102   ripstop ripstop.kites.org
```

Also, after you hit the "dot" when sending mail from the command line is there a very long pause?

After you edit /etc/hosts you can:
```

/etc/init.d/network restart
/etc/init.d/sendmail restart
```

Then check the errors in the log:
```

tail /var/log/mail.err
```

This will get us to the next level, but I still want to see some of the output of
```

sudo ls -al /var/spool/mqueue
```

Just a sample will be fine (I want to see who owns the files and the parent directories).

---

### Post by BlueKnight84 on 2008-01-09
> **blueridgedog said:**
> OK, several things.

First:  It looks like sendmail is choking on something.

Lets see the permissions it is complaining about:

```
sudo ls -al /var/spool
```

```

total 36
drwxr-xr-x  8 root   root   4096 2007-02-10 17:17 .
drwxr-xr-x 16 root   root   4096 2007-02-01 20:58 ..
drwxr-xr-x  2 root   root   4096 2007-02-01 20:01 anacron
drwxr-xr-x  5 daemon daemon 4096 2006-10-25 09:28 cron
drwx--x---  3 cupsys lp     4096 2006-10-25 09:28 cups
lrwxrwxrwx  1 root   root      7 2007-02-01 19:39 mail -> ../mail
drwxr-s---  2 smmta  smmsp  8192 2008-01-09 19:31 mqueue
drwxrws---  2 smmsp  smmsp  4096 2008-01-09 19:14 mqueue-client
drwxr-xr-x  3 root   root   4096 2006-10-25 09:28 openoffice
```


> **blueridgedog said:**
> Then lets see why it is unhappy with it's host name.  Send the following if you can.

```
cat /etc/hosts

cat /etc/mail/local-host-names 
```

Starting with /etc/hosts

```
127.0.0.1       www.knightcast.org localhost
127.0.1.1       www
10.173.173.200  www.knightcast.org

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

> **blueridgedog said:**
> Your hosts file needs an entry with the IP of the host system and its host name and its fully qualified host name.  For example, my system is 192.168.1.102 and is named ripstop and is in the kites.org domain, so:

```
192.168.1.102   ripstop ripstop.kites.org
```

Also, after you hit the "dot" when sending mail from the command line is there a very long pause?

Nope, no pause, just displays the "$".

> **blueridgedog said:**
> After you edit /etc/hosts you can:
```

/etc/init.d/network restart
/etc/init.d/sendmail restart
```

When trying to "network restart", it gives me:

```
sudo: /etc/init.d/network: command not found
```

Restarting sendmail has never been a problem and I was able to do that.  Although I don't think I needed to edit my /etc/hosts file since it looked the way you described it to look.

> **blueridgedog said:**
> Then check the errors in the log:
```

tail /var/log/mail.err
```

Looks the same as the other post.

> **blueridgedog said:**
> This will get us to the next level, but I still want to see some of the output of
```

sudo ls -al /var/spool/mqueue
```

Here's some of it:

```
-rw-r----- 1 root  smmsp 1182 2008-01-09 19:18 qfm092cvdw010445
-rw-r----- 1 root  smmsp  940 2008-01-09 19:19 qfm092df3P011186
-rw-r----- 1 root  smmsp  948 2008-01-09 19:30 qfm092HMbK009006
-rw-r----- 1 root  smmsp  929 2008-01-09 18:34 qfm092rP3I012302
-rw-r----- 1 root  smmsp  939 2008-01-09 18:44 qfm093xMO1015751
-rw-r----- 1 root  smmsp  932 2008-01-09 19:08 qfm094jM8c018591
-rw-r----- 1 root  smmsp  955 2008-01-09 18:18 qfm09NFx0Q008807
-rw-r----- 1 root  smmsp  955 2008-01-09 18:18 qfm09NGok9008812
-rw-r----- 1 root  smmsp  938 2008-01-09 18:48 qfm09Nlnb7008877
-rw-r----- 1 root  smmsp  968 2008-01-09 18:52 qfm09NouVY008888
-rw-r----- 1 root  smmsp  958 2008-01-09 18:52 qfm09NpT2q008893
-rw-r----- 1 root  smmsp  957 2008-01-09 19:16 qfm0A0EvET008954
```

PS - I just now with the last command, tried copying and pasting the information from Putty and didn't know I could do that this entire time!  I've been hand writing it all the while!  I can reply much faster to you now!

---

### Post by dcstar on 2008-01-09
> **BlueKnight84 said:**
> 
........
Starting with /etc/hosts

```
127.0.0.1       www.knightcast.org localhost
127.0.1.1       www
10.173.173.200  www.knightcast.org

```

You are aware that these addresses are only for internal networks and will not be routeable from the Internet?

---

### Post by BlueKnight84 on 2008-01-09
> **dcstar said:**
> You are aware that these addresses are only for internal networks and will not be routeable from the Internet?

I know I'm going to get laughed at for this question, but how would I edit it so that anyone on the internet can send mail to [email]user@knightcast.org[/email]?

---

### Post by dcstar on 2008-01-09
> **BlueKnight84 said:**
> I know I'm going to get laughed at for this question, but how would I edit it so that anyone on the internet can send mail to [email]user@knightcast.org[/email]?

There is a lot more to setting up an incoming e-mail server than just changing your local IP address, anyway there is already a mail server for that domain:
```
dc@dc-desktop:~$ nslookup
> set type=mx
> knightcast.org
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
knightcast.org  mail exchanger = 10 mail.knightcast.org.

Authoritative answers can be found from:
knightcast.org  nameserver = ns1.knightcast.org.
knightcast.org  nameserver = ns2.knightcast.org.
mail.knightcast.org     internet address = 132.170.214.91
ns1.knightcast.org      internet address = 132.170.214.90
```

---

### Post by BlueKnight84 on 2008-01-09
> **dcstar said:**
> There is a lot more to setting up an incoming e-mail server than just changing your local IP address, anyway there is already a mail server for that domain:
```
dc@dc-desktop:~$ nslookup
> set type=mx
> knightcast.org
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
knightcast.org  mail exchanger = 10 mail.knightcast.org.

Authoritative answers can be found from:
knightcast.org  nameserver = ns1.knightcast.org.
knightcast.org  nameserver = ns2.knightcast.org.
mail.knightcast.org     internet address = 132.170.214.91
ns1.knightcast.org      internet address = 132.170.214.90
```

That's the one I'm trying to configure. :)

---

### Post by blueridgedog on 2008-01-10
I assume that 132.170.214.91 is the external address that is then portforwrded from some routing device into 10.173.173.200

More on the other items after a bit...I need to read through the output you sent.

You clearly have messages building up in your mail q.  Sendmail is unable to send them.

Try the command 

```
sudo mailq
```

Then try and force sendmail to clear the q with:

```
sudo sendmail -q
```

---

### Post by BlueKnight84 on 2008-01-10
> **blueridgedog said:**
> I assume that 132.170.214.91 is the external address that is then portforwrded from some routing device into 10.173.173.200

More on the other items after a bit...I need to read through the output you sent.

You clearly have messages building up in your mail q.  Sendmail is unable to send them.

Try the command 

```
sudo mailq
```

Thanks again for the help.  Here's a sample of what came up.

```
m066rTow015094     1594 Sun Jan  6 02:37 MAILER-DAEMON
                 (Deferred: Connection timed out with -----dashed out to protect my email from spam---.com.)
                                         me@.---------com
                Total requests: 108
```

Could my problem simply be that my home user account doesn't have the appropriate permissions to be readable and/or executable?  Do you know if sendmail is depending on that of my folders? 

> **blueridgedog said:**
> Then try and force sendmail to clear the q with:

```
sudo sendmail -q
```

I did that, but nothing printed on the screen or anything.  I hope whatever we did, well, did something.

---

### Post by blueridgedog on 2008-01-10
OK, your sendmail setup has over a hundred messages in the q.  It tries to send them and can't.  Dubuging this will be challenge via the forum.  I will send you a message with some ideas.

---

