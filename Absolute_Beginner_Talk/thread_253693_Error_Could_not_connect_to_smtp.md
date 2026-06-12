---
title: "Error: Could not connect to smtp"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by clesage on 2006-09-08
Hi everyone, I am stumped. :-k 

In Evolution, I am able to receive e-mail via POP, but I cannot send via SMTP. After about 5 minutes of sitting on "sending" I get the following error. 

Error while performing operation
Could not connect to smtp.[myisp]: Connection timed out

(And I've tried my ISP's STMP, my website's SMTP, and my work's SMTP, same problem.)

I have tried the different security settings, and have ensured all my options are correct multiple times. (the only option I can't verify, and my ISP won't support me, is "Authentication Type" though I have tried different ones and it makes no difference.)

I've seen similar threads that talk about port 25 being blocked or unavailable because of incorrect DNS settings. I have a feeling that this is the direction I should be looking.

I am on DSL high speed, running from a laptop to a router to a DSL modem. I have used this router, e-mail account and Evolution for years with no problem. The ISP (Bell), the laptop, and Dapper Drake are the 3 new variables.

Under Network Settings -> DNS, my "search domains" is set to "no-domain-set.bellcanada". Does that seem strange? Should it be setting a domain? I've also been having inconsistent delays during host lookup. A webpage will sit there "looking up [hostname]" for sometimes 10 seconds, and then once it starts transferring, it speeds up and works fine.

If anyone has any suggestions, I would appreciate it.

Thank you,
Chris Lesage

Edit: as for DNS delay, I just found this: [http://www.linuxquestions.org/questions/showthread.php?t=475132](http://www.linuxquestions.org/questions/showthread.php?t=475132)  which I am going to read through.

---

### Post by Handssolow on 2006-09-09
I only recently discovered I had a similar problem, being able to receive emails but not sending, I got an error message about SMTP authentification.

My problem sending emails in Evolution was solved this way-

select

edit>preferences>highlight mail account>edit>sending Email

then I unchecked the box for server authentification and found I could then send and receive emails.

Hope that helps.

---

### Post by clesage on 2006-09-10
Hi Hands, thanks.

No that doesn't help. I've tried different settings, and the various smtp servers just doesn't respond.

Anyone: How would I diagnose if port 25 is blocked? Or something similar. (Like is smtp as a service blocked? I don't really even know where to begin.)

The help on domains and dns usually seems to assume a knowledge of how things work. (The help on search domains basically says "this is where you enter your search domain. :) 

-sage

---

### Post by clesage on 2006-09-10
Ok I found some clues:
[http://www.linuxforums.org/forum/linux-networking/68019-smtp-error-mail-client.html](http://www.linuxforums.org/forum/linux-networking/68019-smtp-error-mail-client.html)

I did nslookup on smtphm.sympatico.ca  and it gave me a "canonical name:

```
$ nslookup smtphm.sympatico.ca
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
smtphm.sympatico.ca     canonical name = smtp.bc.hotmail.com.
Name:   smtp.bc.hotmail.com
Address: 65.54.191.190

```

Should it be saying the server is my local router? Is that could be messing me up? (192.168.2.1#53) What is the 53?

So anyway I tried using the canonical name (is that Ubuntu lingo, or is that where canonical gets its name? (confused)) and the ip address as the smtp server. Same thing, EXCEPT when I turn off "Secure Connection" I finally get an error from the server! (good news)

```
MAIL FROM command failed: Must issue a STARTTLS command first
```

So it's responding. Plus, following the link above, I tried telneting the address, and it responded fine. So I am going to keep fiddling with the security settings. I think the server is just ignoring me when I don't have the "type of authentication" correct. (though I've tried them all...)

Frustrating. I'll update if I get any results.

-sage

---

### Post by woodythdog on 2007-02-03
Hi I had the same trouble with bell sympatico No matter what I tryed I could not get an outgoing SMTP connection with[COLOR="DarkOliveGreen"] smtphm.sympatico.ca[/COLOR]

After several searches I found an old post from som "Mac" users experiancing problems with sympatico smpt

Long storie short tryed   [SIZE="4"]smtp1.sympatico.ca[/SIZE]  works no problem

---

### Post by reja on 2008-01-18
I have the same problem. I thought the problem was with my SMTP also, but it turned out that the problem seems to have something to do with the "send" in Evolution. I found a temp workaround:

1) open a new message window
2) copy the original outgoing message into it (manually add recipient and subject)
3) delete the original outgoing message(s) from the outbox
4) bring up the inbox so focus is not on outbox
5) send new message

This works for me. Afterwards, all the messages I sent go out immediately, until the next Evolution session, when I have to start all over. The problem only seems to be with the first outgoing message of each session. Sometimes I have to do this two or three times at the start, but so far it has always worked for me.

---

### Post by NEKOKONEKO on 2008-02-04
I use yahoo.se mail and i can't conncet to the smtp server. I tried to ping the server and it worked. But i can't send i have smtp enabled in guarddog. But it seems its not working any thougths ?

---

### Post by plucky on 2008-02-04
NEKOKONEKO,

Yahoo mail in the uk required us to use different ports.

For receiving mail we have to use **pop.mail.yahoo.co.uk:995** i.e use port 995,and for sending we have to use **smtp.mail.yahoo.co.uk:465**. These are not the default ports used by Evolution.

I don't know if the setup with yahoo.se is the same but you need to check out the Yahoo email requirements for your country.

Hope this helps..
Good luck

---

### Post by NEKOKONEKO on 2008-02-04
But I'm Swedish and its right but its smtp.mail.yahoo.se in Sweden. I can't connect to smtp so i think i done something wrong when i set up guarddog. Everything else is working what protocols does smtp need to work ?. and im useing kmail

---

### Post by plucky on 2008-02-04
I just thought that they too might be using a different port which you have to specify by putting **port number** after the smtp server name.You need to check yahoo.se for the smtp server settings.Also yahoo in the UK uses SSL encryption on their SMTP server.

Might be different in Sweden.

---

### Post by NEKOKONEKO on 2008-02-05
Now its working ^^ the thing I've done wrong was that i didn't put a special rule that enabled the smtp port ^^ thanks any way

---

### Post by Paul86fxr on 2008-02-22
Having the same problem with a router, not when using wired connection, what special rule did you use? and how did you apply it?

---

