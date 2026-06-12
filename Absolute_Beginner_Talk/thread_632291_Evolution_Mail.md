---
title: "Evolution Mail"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by mattroy89 on 2007-12-05
How do I set up Evolution Mail for use with my Hotmail account? Is there a different email application that is better to use? Thanks.

---

### Post by LowSky on 2007-12-05
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

---

### Post by mattroy89 on 2007-12-05
That is for gmail not hotmail. I use hotmail. Thanks though. Still looking for help guys.

---

### Post by LowSky on 2007-12-05
replace the gmail codedl ines with hotmail references

ie: mail.hotmail.com
smpt.hotmail.com

---

### Post by LowSky on 2007-12-05
heres what i found by using GOOGLE

[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html](http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html)


If you want to use you Evolution mail client to send and receive your hotmail messages use the following procedure.

First, make sure your system is up to date. Open up a terminal and type

sudo apt-get update

First You need to install the inet daemon

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies.

Next You need to install pop3 server and hotsmtp

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtp, which allows you to send e-mail through hotmail using SMTP.

By default, however, only hotway gets installed properly to your inet daemon, so let&#8217;s fix this.

sudo gedit /etc/inetd.conf

Look for the following line

pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server but if you don&#8217;t feel like filling up your hotmail box, change the line to add &#8220;-r&#8221; to the end, complete line looks like below

pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste the following line at the bottom of the file

2500 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server using the following command

sudo /etc/init.d/inetutils-inetd restart

If everything is working properly, you&#8217;ll see the following pop up on your screen

* Restarting internet superserver inetd [ ok ]

Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here&#8217;s your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)

---

### Post by nne2 on 2007-12-05
hello-can someone please just tell me where to ask a question about installing ubuntu on a pc running windows xp home?  i wrote months ago and somebody bitched at me.  can somebody help?  ed.

---

### Post by asmiller-ke6seh on 2007-12-05
> **nne2 said:**
> hello-can someone please just tell me where to ask a question about installing ubuntu on a pc running windows xp home?  i wrote months ago and somebody bitched at me.  can somebody help?  ed.

First - don't tack on to an existing thread unrelated to the subject of your question ... that will usually get you ignored - instead, start a new thread AFTER YOU HAVE SEARCHED TO SEE IF SOMEONE HASN'T ALREADY ASKED THE SAME QUESTION. This is the right section to post such questions.

Alternatively, you could check out the [COLOR="DarkRed"]New Ubuntu User's Resource [/COLOR]- there's a link to it in my SIG (below).

---

### Post by nne2 on 2007-12-05
hello-i do not know where to post.  please do not tell me what not to do.  i would like to know about how to install ubuntu.  i do not know what a sig is.  ed.

---

### Post by asmiller-ke6seh on 2007-12-05
> **nne2 said:**
> hello-i do not know where to post.  please do not tell me what not to do.  i would like to know about how to install ubuntu.  i do not know what a sig is.  ed.

SIG=Signature - the thing that appears after the main post.

I would like to suggest that you be more considerate in your replies. We are here trying to help each other. Gentle language gets better response than the tone that you are using. In other words, chill out. We've all been in your shoes, and we understand new users' frustrations.

Look at the bottom of my message. See the underlined stuff that is written in blue - those are links to the listed subjects. Click on the one that says "New Ubuntu User's Resource."

Good luck.

---

### Post by LowSky on 2007-12-05
EDIT: see next post

---

### Post by LowSky on 2007-12-05
go to ubuntu.com, order a CD to be shipped to your house takes a fe weeks to get, put in your computer at start up before windows starts, hopefully it will boot into the LIVE cd version.

otherwise download the iso, use a probgram like nero in windows do make a bootable cd, then put in your computer at start up before windows starts, hopefully it will boot into the LIVE cd version.
 click on install, if you dont want to loose windows use the option to install using open disk space. and follow the instuctions

---

### Post by nne2 on 2007-12-05
hello
thanks for reply.  first ever reply i received from this forum was somebody telling me i was trying to "hijack the forum" because i posted in the wrong place.  forgive my edge when posting.  i will go to the blue information below and try to figure out what to do.
thanks.  ed.

---

### Post by nne2 on 2007-12-05
hi-thanks for reply.  i have downloaded ubuntu onto my desktop.  think i read that i need to make a cd to use it.  tried to burn cd got message that it is bigger than 700mb or kb or something so could not make cd.  website says it may take ten weeks to get cd.  true?
ed.

---

### Post by LowSky on 2007-12-05
what version did you download, regular ubuntu  is only 693MB

---

### Post by asmodaous on 2007-12-05
It should not be that big. The live cd should only be about 650mb.  Go ahead and burn it to a dvd, that will fix it for you. I am new too so I know how it is to try to get help. To be honest the Ubuntu forum is one of the most helpful places. Just about any answer can be found here. The members are really helpful and nice.

---

### Post by nne2 on 2007-12-05
thanks lowsky and asmodaous for replies.
not sure what version-just what seemed right from ubuntu site.  does this include firefox and thunderbird?  i already have them.  can i download selectively?  i will try again to download to cd.
thanks much for help.  are you folks using ubuntu now?  if so how is it?  ed.

---

### Post by asmodaous on 2007-12-05
Yes it has firefox on it, as far as thunderbird I am not sure it loads it or not. I am using Ubuntu 7.10 right now. I left windows about 3 months ago, haven't looked back since. There are a few apps I can use that are windows based but I will just bite the bullet. I won't tell you Ubuntu is better, just that it is a different way of doing things which fits my way of thinking, and in that sense it's just logical for me to use Ubuntu. So much so that I have even installed it on my mothers computer this past Thanksgiving. I do have my share of problems, but at lest it is not windows related and I can find a fix via the forums. I have tried a few other distros and Ubuntu just works for the most part, I also like Fedora.

---

### Post by nne2 on 2007-12-05
well, i fought with system to burn disk.  no luck.  so then i fought with site to order a cd.  unbelievable.  finally a disk of ubuntu is coming, in only 6 to 10 weeks.  if ubuntu is anything like this, i am worried.
thanks to both of you for helpful posts.  i am sure you will hear from me.  ed.

---

