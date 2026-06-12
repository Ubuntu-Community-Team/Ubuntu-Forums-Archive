---
title: "Internet Connection"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2006-11-27
I contacted Linuxant and installed their recommended generic Debian modem drivers, but I still can't connect to the Web with my internal dial-up modem. It worked perfectly under windoze so it isn't the modem.
  When I go to System > Administration > Networking > Modem Connection is enabled. In Properties > Modem, there are different options for the Modem port: /dev/modem, then /dev/ttyS0 to S3. Which should I be selecting? Also, I keep selecting TONES under Dial Type but it keeps changing back to PULSES. Does anyone know why that is happening?
  Is there a way to directly connect to the Internet without first going through Firefox or Evolution? On my Macs and Windoze computers, I first connect to my ISP provider and then open my browser or mail.
   Everthing else works perfectly under 6.10 but without a web connection, it will be useless. 
   Thanks in advance for any help.

---

### Post by 56phil on 2006-11-27
What type of modem do you have? I thinking that you may have a 'winmodem' where most of the work is done in software. If that's the case, you may need to invest in a slightly more expensive 'hardware modem.'

On the other hand, it could be a configuration problem. What have you done so far in that area? It takes more than installing a deb to get a modem working. Good luck.

---

### Post by orangemoose on 2006-11-27
Do yourself a big favor and go buy a cheap($20) 3Com 56k Modem PC Card.
Then go to a console and type 

sudo pppconfig

Use the tab key to navigate and accept defaults for tone, etc.

You will need to have a dialup number for your ISP and maybe play around with the port I used SSO.  Exit and save changes.

At the console you type pon Earthlink or whatever you named the connection.
When you're done type poff Earthlink.

Good Luck.

---

### Post by ReaderRat on 2006-11-27
See if any of these links help:
**[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=modem&titlesearch=Titles)**

---

### Post by Stunt Double on 2006-11-28
Thanks for the advice but still no success. I'll give Conexant another try tomorrow (yes, it is a software modem that has been configured). 
    Are other internal cards available in 1/2 height?

---

