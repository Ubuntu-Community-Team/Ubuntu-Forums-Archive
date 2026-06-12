---
title: "Email previewer??"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-17
I like to preview my email on the server before downloading onto my computer. Can anyone recommend a package that can screen email on the server ?

Thanks again! ubuntu is awesome!

---

### Post by damonw5 on 2005-07-17
[QUOTE=grofaz]I like to preview my email on the server before downloading onto my computer. Can anyone recommend a package that can screen email on the server ?

Thanks again! ubuntu is awesome![/QUOTE]
 How are you accessing your email? POP is one option, but some email providers let you use an option called "IMAP" that lets you do exactly what you're talking about. The default Email client (Evolution) supports IMAP, I believe, so the question is whether your email provider does.

---

### Post by Nanaki on 2005-07-17
[QUOTE=damonw5]How are you accessing your email? POP is one option, but some email providers let you use an option called "IMAP" that lets you do exactly what you're talking about. The default Email client (Evolution) supports IMAP, I believe, so the question is whether your email provider does.[/QUOTE]
 Thunderbird is able to leave messages on the server with POP3.

---

### Post by aum11 on 2005-07-17
I guess You are seeking some software package similar to mailwasher under windows, which gives a view of the emails before they are actually downloaded to your machine.

I do not know the answer as I am a noob, but I too would also like this functionality.  The above responses don't seem to address this requirement.

---

### Post by grofaz on 2005-07-18
Yeah, I use Quick Delete in Windows. Very nifty! ICQ also has a previewer feature. But that's the idea. I want a package that allows one to look at email on the server before it gets on your PC. So anyone know of any packages ?? Thanks for the replies.

---

### Post by Kangaroo on 2005-12-23
The solution, that comes to my mind would be "Save my Modem" 

[http://savemymodem.sourceforge.net/]("http://savemymodem.sourceforge.net/")

I looks similar to Mailwasher, it's not as comfy to handle like Mailwasher, but still does the trick for me. 

Add this to your sources.list: 
deb [http://tassi.web.cs.unibo.it/debian/smm](http://tassi.web.cs.unibo.it/debian/smm) ./

then

```
sudo apt-get update 
```

then 

```
sudo apt-get install smm 
```

---

### Post by bscbrit on 2005-12-23
I'm sure that all of the suggestion given so far have merit but what is the main purpose of the program that you are looking for - to save download time or to provide additional security?  If it is the former, then I would suggest, as someone already has done, that you look at using IMAP or Thunderbird, the both of which seem to do as you ask and have ubuntu versions.  If you are concerned about security - forget it, that is not a major problem.  There are no significant viruses for linux (yet!) and adware does not exist in open source software.

EDIT Kangaroo's suggestion also seems to meet your needs.

EDIT2:  OK, there is no ubuntu version of IMAP, but plenty of ubuntu mail readers that will access IMAP - I knew what I meant when I typed it!

---

### Post by editrix on 2005-12-23
With KMail, if you set your POP filter to filter anything over 1Kb, it'll preview your mail for you. You'll be given the option to download now, download later, or delete from server.

---

### Post by WishMaster on 2006-07-15
smm (save my modem) won't install under Dapper (it used to work under Breezy. Now [smm has dependency issues with xlib]("http://ubuntuforums.org/showthread.php?t=192780")).

I am using "mail notification". It runs in the tray, so I don't have to manually check for mail, or I don't have to have thunderbird running for mail checking.
I do NOT want to open thunderbird, to fetch my mails (IMAP) just to delete them on the server. 
I want something like mailwasher:
- runs in the tray
- leaves mails on server
- fetch title and first part of body
- delete AND BOUNCE mails
- GUI

There is NOTHING in Linux that does all of that (windows has hunderds of programms that do that).
There is a Linux-version of mailwasher, but it stops working after 30 days.

---

