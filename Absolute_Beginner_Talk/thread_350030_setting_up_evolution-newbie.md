---
title: "setting up evolution-newbie"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ubromtoo on 2007-01-31
How can I find the answers to the few(but baffling) questions which Evolution

expects me to answer , to get the email thing going?  I just installed a dualboot

(Windows XP home/ Ubuntu 6.06 Dapper Drake ) a couple days ago.

  My web browser& email in Windows are via MSN Explorer.  Broad band is  Cox Cable.

     -email server type is ????

     - mail server name is ????

      -OWA URL is ????

       -outgoing mail server type is ??

       -outgoing mail server name is ??

 I have spent quite a while Googling, prowling forums threads, and have not learned

much at all.  The "system Administrator" I'm supposed to ask about these things , is me.

How do I ask my ISP(or whoever) for this info?   :guitar:

---

### Post by muguwmp67 on 2007-01-31
You will have to get the mail server names from Cox cable.  Their website should likely have something in their internet support area regarding this.  They won't likely have a listing for linux, but their information for Eudora, Outlook, etc will still apply.  Your recieving mail will server will most likely be POP, and your sending will probably be SMTP.

If you have to talk to a Customer Service, be tactful.  You might not want to mention that you are using linux until you are sure you have a rep with a clue.  Otherwise you might get the 'we don't support linux' answer.

---

### Post by yigal.weinstein on 2007-01-31
You will have to know exactly what you are dealing with.  It this sounds a bit strange but go with me for a little bit.  You said you have set up an account with MSN does this mean hotmail.  If so there is a special program called gotmail that you may need to use to retreave your messages.  Your ISP has nothing to do with your mail unless your email is with them.  So what service are you using for email.  After answering this for yourself we all can help you.

---

### Post by ubromtoo on 2007-01-31
Yes, MSN Explorer apparently uses Hotmail....so should I google "gotmail"?  s'pose so.


   Thank you both for your help :o

---

### Post by yigal.weinstein on 2007-01-31
I wouldn't suggest google just go through the Ubuntu forum just do a search for gotmail you will most likely find a guide + any problems others have in setting up there mail with evolution.

---

### Post by yigal.weinstein on 2007-01-31
gotmail breaks sometimes also so an alternative search is simply how to set up hotmail with evolution

---

### Post by psyne on 2007-01-31
As stated above you will need to answer a few questions for the best support if you are using Hotmail as your primary email service it will depend on if you have popmail access. If you don't have pop access or if you are not sure then you can use gotmail which was mentioned earlier.

Best way to know if you are using hotmail is if your email address is something like 

[email]bob@hotmail.com[/email] or [email]bob@msn.com[/email]

Here is a link to howto for setting up Gotmail and Evolution to get the hotmail in evolution.

[http://www.ubuntuforums.org/showthread.php?t=200408](http://www.ubuntuforums.org/showthread.php?t=200408)

If your email address is something like [email]bob@cox.net[/email] then go to the link below to get your pop3 settings

[http://support.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=fcb44db0-3835-491c-bca8-2d56ac32a574](http://support.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=fcb44db0-3835-491c-bca8-2d56ac32a574)

The rest of the information is simple at that point 

email server type would be pop3

POP3 Server settings
Incoming mail would be your POP Server
Outcoing mail would be you SMTP Server

user name = [email]XXXX@cox.net[/email]
Password = XXXX

---

### Post by ubromtoo on 2007-01-31
Psyne:

  My primary email is indeed "bob@msn.com"- so does this mean i'm NOT

using Hotmail?

  sorry I can't try any of the sugestions right now - am down w/bronchitis.

hope to be back in the saddle in 24-48 hours.

  sincere thanks for the help  :)

---

### Post by psyne on 2007-02-01
ubromtoo:

That means you are using Hotmail as your main email provider. So you will want to follow the instructions here

[http://www.ubuntuforums.org/showthread.php?t=200408](http://www.ubuntuforums.org/showthread.php?t=200408)

---

### Post by ubromtoo on 2007-02-13
thanks all for the help, I finally got my "bob@cox.net" email working via Evolution.

However, still no luck figuring out what server types/names to use , in order to

get my "bob@msn.com" mail via Evolution.

  I've emailed MSN Explorer customer support for the info, but no response so far....

after trying every combination of "pop" server name that I can think of, with no luck, 

I may have to consider making my  cox.net email account the main one I use, and

just phasing out the msn.com account.

   Well, at any rate, at least now I can send & receive email (on cox.net) !!!!!

=D>     #-o               \\:D/

---

