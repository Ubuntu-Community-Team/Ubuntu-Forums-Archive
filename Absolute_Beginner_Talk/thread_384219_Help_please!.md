---
title: "Help please!"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-14
I'm trying to do this to get hotmail on evolution.

Code:

sudo apt-get update

Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:

sudo gedit /etc/inetd.conf

Look for a line like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:

sudo /etc/init.d/inetutils-inetd restart

If everything is working properly, you'll see this pop up on your screen:

Code:

* Restarting internet superserver inetd                            [ ok ]

Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

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



But when I get the the second code: sudo apt-get install inetutils-inetd it says this

sudo apt-get install inetutils-inetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package inetutils-inetd

What does it mean?

---

### Post by v8YKxgHe on 2007-03-14
Exactly what it says. Could not find the package. You most probably need to add more [Software Repositories]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

Then try again.

---

### Post by julie_lebou on 2007-03-14
I went on the link, but I don't get how to add Software Repositories.. i don't even know what it is. And do I have to install a particular one? Really new to linux... was windows for ever

---

### Post by hyper_ch on 2007-03-14
I just have two things:

(1) This is definitively not Absolute Beginner Level... most users don't even know how to setup pop3/imap accounts on a computer...

(2) Please chose next time a title that is more appropriate.... everybody who opens a thread in help forum is asking for some help...

Last but not least, plz move this thread to an according forum.

---

### Post by v8YKxgHe on 2007-03-14
> **julie_lebou said:**
> I went on the link, but I don't get how to add Software Repositories.. i don't even know what it is. And do I have to install a particular one? Really new to linux... was windows for ever

It shows you how in 5 very simple steps. It doesn't get any easier than that. Also if you read the link you would know what Repositories are.

Enable both Multiverse and Universe

---

### Post by lamalex on 2007-03-14
before you get too involved in this, do you have the pay-for type of hotmail account? The basic account does not allow you to pull your mail down with a client. I recommend you switch over to gmail.

---

### Post by julie_lebou on 2007-03-14
Ummm.... sorry hyper_ch.. I just though that Absolute Beginner talk was for help for the beginners... but I didn't think it was answered and only seen by beginners... I copied this treat somewhere else.. but since I think that competent linux people do read these treats, I'm going to leave it here too.

Thanks for you're comprehension

---

### Post by julie_lebou on 2007-03-14
Ummm. I don't know what's my hotmail type... I've had it for years? How do I check witch type I've got?

---

### Post by v8YKxgHe on 2007-03-14
If you're not paying any money for it, then you don't have the paid-version of Hotmail, which means you will not be able to access hotmail via pop3, but instead will have to use the Webbased version MS offers.

---

### Post by julie_lebou on 2007-03-14
Adding Extra Repositories

To install software from the “Universe” or “Multiverse” repositories:

   1.

      Open System->Administration->Software Properties .
   
................. Software properties is not there, only softwere sources...

---

### Post by v8YKxgHe on 2007-03-14
Then click Software Sources.

---

### Post by xyz on 2007-03-14
For Edgy,it's System > Administration > Synaptic Pack Manager > Settings > Repositories > now check the boces where it says (universe) and (multiverse)...to add repositories.

If ONLY totally totally beginners read these threads, no one would get any answers!:wink:

---

### Post by julie_lebou on 2007-03-14
THANK YOU for ur help, and thank you for this line: 

If ONLY totally totally beginners read these threads, no one would get any answers!

I found it!

---

### Post by xyz on 2007-03-14
You're welcome; hang in there and let us know how it goes...

---

