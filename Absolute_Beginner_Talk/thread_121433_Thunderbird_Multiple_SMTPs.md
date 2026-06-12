---
title: "Thunderbird Multiple SMTPs"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-25
Hello there,

1.) 
I would like to use two or more accounts with thunderbird. But multiple SMTP is becoming a problem. For instance, I have an outgoing SMTP server where I have two different accounts but using the same port(25) but different user names and passwords(only because of the matter of the university server policy). My department server and account is working without problems but the other one is issuing a message that the connection can not be established(after waiting and trying to connect 2-3 minutes.) So what is the problem?

2.)(maybe I should have asked in a different thread anyway...)

I first installed Mozilla-Thunderbird 1.0.7 which is in the repositories of Ubuntu then I read that it has a bug with multiple SMTPs and heard that Thunderbird 1.5 has fixed this bug and downloaded and installed it and then I uninstalled Mozilla-T. Now under Internet -> I have an empty(working) Thunderbird which does look like a Windows .exe icon but the real Thunderbird emblem(that blue bird carrying an envelope under the wings) does not appear. (Not a big problem actually but I want it to appear.)

Thx. :D

---

### Post by megamania on 2006-01-25
[QUOTE=utab]But multiple SMTP is becoming a problem. For instance, I have an outgoing SMTP server where I have two different accounts but using the same port(25) but different user names and passwords(only because of the matter of the university server policy)[/QUOTE]

I do use 3 or 4 different smtp's with no problem. I remember that the procedure to set them up was not straightforward to me, but it works perfectly.

I'm not using ubuntu/linux right now (I'm not at home) so I can't be specific, but if you need more help please let me know where exactly you're experiencing difficulties.

---

### Post by utab on 2006-01-25
So Now I am on Ubuntu side

Now I have a department account without problems.

But the other account is problematic:

Under Account settings I have configured Outgoing SMTP for my student user name and also wrote the smtp server name and for different accounts I have these options(no problem)

But when I click the box icon I get a message after a while connection to server xxx timed out. I checked all the settings again and they seem to be correct because they are the same settings I use on Win side.(I checked twice besides)

Is it a solution to uninstall and install again?(which does not seem reasonable to me :D)

thx.

---

### Post by utab on 2006-01-25
Could you please give me some information on how to uninstall applications installed without using Synaptic. 

Because I installed Thunderbird this way.

thx.

---

### Post by utab on 2006-01-25
[QUOTE=utab]So Now I am on Ubuntu side

But when I click the [COLOR="Red"]box[/COLOR] icon I get a message after a while connection to server xxx timed out. I checked all the settings again and they seem to be correct because they are the same settings I use on Win side.(I checked twice besides)
[/QUOTE]
[COLOR="Red"]box[/COLOR]=inbox 

Sorry

---

### Post by megamania on 2006-01-25
Are you sure that the second address is using the right SMTP and not the first one?

Uninstalling does not appear to be a good idea to me in general, and especially in this case, not only because thunderbird does not need to be installed/uninstalled, if I remember correctly.

Thunderbird creates a '.mozilla-thunderbird' directory in your /home. Just delete it if you want to start from scratch, but be warned that you'll lose **all** of you mail and settings!

I'd check the settings carefully before starting over.

---

