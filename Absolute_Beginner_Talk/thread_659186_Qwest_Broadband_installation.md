---
title: "Qwest Broadband installation"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Michl on 2008-01-05
I am waiting for my Actiontec modem/router to arrive from Qwest and
preparing myself to install their broadband service.  My anxieties about 
installation would be greatly diminished if there is anyone who has or
could point to a faq about this.  Any pointers or brief list of hints would
be appreciated.

Thank you,
Michael

---

### Post by mkoyle on 2008-01-12
This really shouldn't be difficult.  You will get their router, connect it to the phone line, plug your computer into the ethernet port and then you will need to configure the device according to their instructions.

I did it several times with Ubuntu while living in Utah (probably the same actiontec device).

If you turn on your computer after the modem is on, you will get an IP from it and can edit the router settings according to Qwest's instructions.

Open firefox and type in 192.168.0.1

If their instructions don't get through, call them and they'll help (don't tell them you are using Ubuntu -- they will hassle you unnecessarily).

After it is running, if you have problems, post again... sometimes the actiontec modem gets carried away and you have to configure one thing manually so it doesn't give you trouble.  Don't worry about that unless it doesn't work right.

--Matthew

---

### Post by mkoyle on 2008-01-12
[http://ubuntuforums.org/showthread.php?t=120424](http://ubuntuforums.org/showthread.php?t=120424) Has several people who are currently using the exact setup you are talking about.

--Matthew

---

### Post by Michl on 2008-01-15
I received a 2wire modem/router/gateway and set-up was easy.  The only little hurdle was figuring out that I had to call tech support to get the id and password.  I am assuming that you would get this using the CD and the Quickconnect information, but without the CD you don't have that information.  But Techsupport was helpful.  One nice thing with this modem is that you access set-up, diagnostics and so on via the web browser, so there are no compatibility issues whatsoever.

Thanks,
Michael

---

### Post by mkoyle on 2008-01-15
Right before I left Qwest, almost two years ago, they started offering the 2wire modems.  I was wondering if they had gone back to the Actiontec modems...

I didn't expect you would have any problems-- I do remember I had to call support to get that username and password.  You might email that to yourself or something so you don't have to call them if anything happens.  I'm just overcautious, I suppose.

Glad it works!

--Matthew

---

### Post by ebozzz on 2008-02-04
Hello all. I'm a new Qwest customer and I would like to know if any of you were able to configure the q.com email account in Evolution? Thanks!

---

### Post by Michl on 2008-02-04
> **ebozzz said:**
> Hello all. I'm a new Qwest customer and I would like to know if any of you were able to configure the q.com email account in Evolution? Thanks!

Qwest has a forum and people there are helpful.  There are people
knowledgeable on it about linux and you can get good help.

It is my understanding (and this was confirmed I thought by technical
help) that their email accounts require Microsoft because you need
to download their software to use their accounts.  If you are using
linux, you can use them as an ISP, but you need to find an email
account compatible with linux.  I could be wrong, but that's the
information I was given.

---

### Post by apcfreak on 2008-02-04
I use Qwest, and although i had previously set it up on windows (i don't know what is going to happen on ubuntu), all i had to do was plug in the network cable. If you have a windows machine, i would recommend to try to set it up via that machine beforehand.

---

### Post by ebozzz on 2008-02-04
> **Michl said:**
> Qwest has a forum and people there are helpful.  There are people
knowledgeable on it about linux and you can get good help.

It is my understanding (and this was confirmed I thought by technical
help) that their email accounts require Microsoft because you need
to download their software to use their accounts.  If you are using
linux, you can use them as an ISP, but you need to find an email
account compatible with linux.  I could be wrong, but that's the
information I was given.

I've got it setup in Thunderbird on my Windows platforms and it's working just fine. You do **not** have to have MS products to make it work. I guess that I could download Thunderbird but the thing is that I prefer Evolution. I was hoping that someone has had some success with getting it configured.

---

### Post by ebozzz on 2008-02-04
I don't know if any of you are using Thunderbird but to get the q.com mail to work, use the following settings:

INCOMING
User name = [email]xxx@q.com[/email]
Server name: pop3.live.com
port 995
Use secure connection: SSL
Do **NOT** check "use secure authentication"

OUTGOING
Server name: smtp.live.com
port 25
User name = [email]xxx@q.com[/email]
Use secure connection: TLS if available

It may not be required but I restarted T-Bird after making the changes. It is tested and it works!

---

### Post by Michl on 2008-02-05
> **ebozzz said:**
> I've got it setup in Thunderbird on my Windows platforms and it's working just fine. You do **not** have to have MS products to make it work. I guess that I could download Thunderbird but the thing is that I prefer Evolution. I was hoping that someone has had some success with getting it configured.

Well, I was misinformed then.  If you can use Thurnderbird under Windows, I think for sure
you can assume that you can use Evolution under linux.

---

### Post by Michl on 2008-02-05
> **ebozzz said:**
> I don't know if any of you are using Thunderbird but to get the q.com mail to work, use the following settings:

INCOMING
User name = [email]xxx@q.com[/email]
Server name: pop3.live.com
port 995
Use secure connection: SSL
Do **NOT** check "use secure authentication"

OUTGOING
Server name: smtp.live.com
port 25
User name = [email]xxx@q.com[/email]
Use secure connection: TLS if available

It may not be required but I restarted T-Bird after making the changes. It is tested and it works!

Are you running this under linux?  WHat I was told is that you have to have
windows to use the 'live' server.

---

### Post by Michl on 2008-02-05
> **apcfreak said:**
> I use Qwest, and although i had previously set it up on windows (i don't know what is going to happen on ubuntu), all i had to do was plug in the network cable. If you have a windows machine, i would recommend to try to set it up via that machine beforehand.

Setting-up the modem and connection is easy in linux, too.  You access configuration through your
browser and enter 192.168.0.1  However, to configure, you need to call support to get your address and password.  That's the step you don't need to do in windows.  But once you have that log on info, the rest is easy.

---

### Post by ebozzz on 2008-02-05
> **Michl said:**
> Well, I was misinformed then.  If you can use Thurnderbird under Windows, I think for sure
you can assume that you can use Evolution under linux.

What I was saying is that Thunderbird is available for download from the Ubuntu repositories. I could just download it for use in Ubuntu. I'd prefer to use Evolution though....

---

### Post by ebozzz on 2008-02-05
> **Michl said:**
> Are you running this under linux?  WHat I was told is that you have to have
windows to use the 'live' server.

Those setting work if you use Mozilla Thunderbird. They work in Windows so i don't see why the same would not work in Linux.

---

### Post by ebozzz on 2008-02-05
> **Michl said:**
> Are you running this under linux?  WHat I was told is that you have to have
windows to use the 'live' server.

I just downloaded Thunderbird in Ubuntu and configured it using the setting listed above. Works like a charm.  ;)  I want my Evolution to work!

---

### Post by ebozzz on 2008-02-05
You know, I might be able to make this work if I can figure out how to change the ports that Evolution uses for POP3 and SMTP.  :-k

---

### Post by ebozzz on 2008-02-05
I've got it working now. The outgoing server would not work with SSL encryption. I selected TLS and "Server Requires Authentication" for SMTP ( smtp.live.com) and POP with SSL for thr incoming server (pop3.live.com).

This is what I configured.....

INCOMING
User name = [email]xxx@q.com[/email]
Server name: pop3.live.com
Use secure connection: SSL Encryption

OUTGOING
Server name: smtp.live.com
User name = [email]xxx@q.com[/email]
Use "Server Requires Authentication": TLS Encryption

I'm good to go!

---

