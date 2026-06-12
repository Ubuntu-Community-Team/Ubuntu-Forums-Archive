---
title: "email in cli"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by ecto on 2005-12-01
Hello its me n0dl/ecto. Anyway, recently ive been getting deep into cli and liking it. I have gotten used to navigating, surfing the web using links, using irssi, and even watching videos in cli with mplayer (thanks to bored2k's brilliant how-to). But the only thing i am missing is e-mail. Everytime i try to access my email it says java script error. I heard there is a way to access email without the use of having to interact with the web-based email's log in page and stuff like that. From what I researched I need an MTA (mail transfer agent) MUA (Mail something something) and fetchmail. I have an MUA (mutt) but i still need an MTA. I heard postfix is good. I also heard that i need to configure fetchmail. I read the doc on it but i have no idea what they are talking about. Can someone help me in how to use an MTA MUA and fetchmail?
thanx.

---

### Post by Paul133 on 2006-11-24
What is irssi? I can't help you with e-mail, but I'm interested to find out how to do more things in the CLI and become less reliant on the GUI. So far, I have lynx, but that's it. Are there any CLI IM programs?

---

### Post by rlozano on 2006-11-24
> **Paul133 said:**
> What is irssi? I can't help you with e-mail, but I'm interested to find out how to do more things in the CLI and become less reliant on the GUI. So far, I have lynx, but that's it. Are there any CLI IM programs?

here ---> [www.irssi.org](www.irssi.org)

though things might be faster in CLI, im not sure if you really like to do e-mail in cli. imho, even if there is, it would be more productive to use a gui base e-mail than cli. e-mail primarily was designed as a productive and communication tool.... ;) 

but yeah, enjoy and have fun with your cli romance atm... should i find any email program for CLI, i'll post it back here....

---

### Post by mark_g on 2006-11-24
I use mutt with getmail and sSMTP, which is a very lightweight MTA that's only started when you send an e-mail. This is obviously better for security and performance reasons if you're a home user.
You just need to configure the /etc/ssmtp/ssmtp.conf file and add this line to .muttrc

```
set sendmail="/usr/sbin/ssmtp"
```

I prefer Getmail over Fetchmail, because I find it much easier to configure than fetchmail. It can be downloaded from the repositories and the docs are on it's website: [http://pyropus.ca/software/getmail/](http://pyropus.ca/software/getmail/) 
It can even get your mails from Gmail and alike.

Also, if you get a lot of mails, you might want to check out procmail and spamassassin. Procmail can put your sort out mails in a different folder, based on who sent it or on the subject with regular expressions. Spamassasin can put a spam rating in the subject line, which will save you time weeding out the spam.

---

### Post by mark_g on 2006-11-24
To comment on rlozano, I do think e-mail from the CLI is a better choice for a lot of people than a GUI one. Mutt's configurability is really phenomenal. There's no other MUA as flexible and powerful as Mutt, so for people who need to deal with a lot of mail, it's more than a worthy alternative to the GUI MUAs.
The only little annoyance might be MIME content, which isn't as pretty when using Lynx or Links2 in Mutt, but that's a sacrifice I'm willing to make.

If you're looking for a CLI IM tool, try centericq. It has a nice interface and supports a lot of protocols (not just icq).

---

### Post by Paul133 on 2006-11-27
Thanks. I just want to assemble a library of CLI programs I can use when I tire of the GUI. I'll try centericq. I'd use it for AIM by the way.

---

### Post by IYY on 2006-11-27
For more CLI fun, try the **mocp** media player, the **bitchx** IRC client, and the **alsamixer** volume manager.

---

### Post by flangemonkey on 2007-02-21
well, I found all this great and just what I was looking for, but I got a seg fault when running centericq and looking round forums this appears to be a common fault... 

but now tmsnc is my friend :D and recommended if all you need is MSN messenger over CLI.

---

### Post by andrew.46 on 2007-07-05
Hi,

 Can I cordially disagree with part of your post:

> **mark_g said:**
> I use mutt with getmail and sSMTP, which is a very lightweight MTA that's only started when you send an e-mail. This is obviously better for security and performance reasons if you're a home user.
You just need to configure the /etc/ssmtp/ssmtp.conf file and add this line to .muttrc

```
set sendmail="/usr/sbin/ssmtp"
```
.

ssmtp actually places symlinks that redirect sendmail commands to ssmtp. Therefore you will usually not need to specify ssmtp at all in your .muttrc file.

                        Andrew

---

