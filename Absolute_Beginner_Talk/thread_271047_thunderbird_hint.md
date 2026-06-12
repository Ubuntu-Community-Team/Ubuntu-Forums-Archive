---
title: "thunderbird hint"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-04
can anyone give me a clue of why does thunderbird give me this message: Could not connect to server localhost, connection refused! i'm trying to setup an account for may yahoo mail and i'm using mozilla webmail extension.

---

### Post by jaboua on 2006-10-04
Localhost should be forwarding everything back to your own computer. To check if it might be the "lo" "device" not working, check if you get response with "ping localhost" in a terminal.

---

### Post by bollix47 on 2006-10-04
See if anything [here]("http://www.ubuntuforums.org/showpost.php?p=1474681&postcount=14") helps.

---

### Post by Frak on 2006-10-04
What webserver are you trying to connect to?
(gmail,yahoo,hotmail)

---

### Post by mendingo84 on 2006-10-04
i'm trying to connect to yahoo...but i have to set an >1024 port...i guess here goes the problem

---

### Post by Frak on 2006-10-04
> **mendingo84 said:**
> i'm trying to connect to yahoo...but i have to set an >1024 port...i guess here goes the problem
Yeah I've had trouble with yahoo and Thunderbird too.
Your best bet would be to either switch back to Evolution, or change to Gmail.
(Personaly I would switch to Gmail, they give you detailed instructions on how to set up Thunderbird, and unlimited storage)

---

### Post by AmandaKerik on 2007-02-01
I had this problem too... even when I had the ports at 1111 and 2222... 

I found that it works if the ports are set to 1111 and 1112.

Change the port settings in the add-on:
Tools > Extensions > Click on WebMail > Preferences > Server > Status shows if you're getting through, and:
Tools > Extensions > Click on WebMail > [Preferences] > Server > Ports is where you change the ports.

Remember to save the changes, and maybe close down TB and restart it.

I hope this helps,
Amanda

---

### Post by Frak on 2007-02-01
> **mendingo84 said:**
> can anyone give me a clue of why does thunderbird give me this message: Could not connect to server localhost, connection refused! i'm trying to setup an account for may yahoo mail and i'm using mozilla webmail extension.
You are aware that yahoo doesn't support POP3, right?

---

### Post by AmandaKerik on 2007-02-02
> **Frak said:**
> You are aware that yahoo doesn't support POP3, right?

That's why there are programs like "ypops" and extensions like "Webmail" for Thunderbird - to get around that limitation :D

They act as (basically) a translator. It talks to Yahoo in the language of HTTP, and then translates it to POP3 for Thunderbird. Thunderbird doesn't know the difference, and just saves them as normal e-mails.

It's great! :D

Webmail also has versions that work with Hotmail, AOL, Mail.com and others.
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

Tip: Set up the ports in the extension first, then in the account settings after...

---

