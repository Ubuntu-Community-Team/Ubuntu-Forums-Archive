---
title: "Email trouble"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DRoll221 on 2007-05-13
Hello all...I recently came over to Ubuntu.  I have set up my email address in Evolution, and enjoy using the program to receive mail.  However, whenever I try to send mail I get the following error:

"Error while performing operation.

RCPT TO <xxxxx> failed: <Rollend7@msn.com>... Relaying denied. Proper authentication required."

where xxxxx is the email address...which doesn't seem to matter whoever I try to send mail to.  I'm pretty sure it has something to do with my password, but I don't ever recall it asking me for a password.  Can anyone help?

---

### Post by DRoll221 on 2007-05-13
anybody?

---

### Post by Stunt Double on 2007-05-14
Are you using DSL?

---

### Post by alienexplorers on 2007-05-14
Have you tried using Thunderbird.  I had problem with Evolution and ended up switching to Thunderbird.

---

### Post by freebird54 on 2007-05-14
Probably just a configuration error.  It asks for a password the first time it successfully contacts the smtp server, and needs it.  Try a couple of different authentication types if necessary.

Here is a typical setup:

Server Type     **SMTP**
Server Name   **smtp.*whatever.which*.com**
Server requires authentication  **Checked**
Auth type  **Login       Check for Supported Types**
username        **your_name_as_known_to_your_ISP**
Remember password     **checked**

It is not unusual to mistype something in there, or use the incoming for outgoing, or use the wrong authentication type - so try this :)  Also - if you have a set up on another system that works, double check the settings there.

Hope that helps....

---

### Post by irish_flu on 2007-05-14
As others have noted, the server you're having trouble with is the SMTP (outgoing) server.

I see a couple of possible scenarios (sorry, I don't use evolution so these suggestions are kinda generic):

- You need to add your username and password to the setup for the outgoing (SMTP) server

-you've already added your username and password, but the SMTP server you're talking to doesn't support that.  Uncheck the "server requires authentication" box.  Sometimes, the only "authentication" an SMTP server does is checking to see if you're on the proper network or not, and it doesn't want a username and password.

---

