---
title: "is it possible  to configure evolution with aol mail?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Jesus4life0412 on 2007-05-26
hi

i have configured evolution with gmail fine but i cant figure out how and if i can configure my aol account. so does anyone know how and if i can make aol mail work with evolution?


thanks

---

### Post by AAM on 2007-05-26
Hi j4l0412,

you need to determine whether AOL will permit you to download the emails using a POP server, or whether they have a different protocol.

---

### Post by joramdam on 2007-05-26
You moust find out if AOL support pop and smtp protocol, else its unpossible as far as i know

---

### Post by joramdam on 2007-05-26
I am pretty sure it does not, but just chek

---

### Post by deswalk on 2007-05-26
Not much help as I had the same problem with Evolution but Thunderbird mail works just fine with AOL and IMAP, no problems :);)

---

### Post by AAM on 2007-05-26
j4l0412

I have done some browsing, mainly because I had heard before that AOL email was problematic. The issue is that AOL doesn't use POP servers, but rather IMAP format. I have listed below the configuration options for Eudora - similar entries should work for Evolution.


> **      Create a New AOL® or AIM® E-mail Account in the Eudora      Software **

       The first step to setting up the Eudora software is to create an      AOL or AIM e-mail account. This will use your existing AOL®      or AIM® account. 
       To create a new AOL or AIM e-mail account in the Eudora      software:
     1. Launch the Eudora software. 
       Note: If Eudora is not your default mail      program, you may be prompted to specify whether you want to use it      as the default by clicking the Yes or      No button. 
       2. Click the Tools menu, then click      Options....
     3. Under Category:, click the Gettings Started icon.
     4. In the Real name: box, type your name      as you would like it to appear on your outgoing e-mail      messages.
     5. In the Email address: box, type your      full e-mail address, for example, [EMAIL="ZolaOnAOL@aol.com"]ZolaOnAOL@aol.com[/EMAIL] or      [EMAIL="GabbyGrace@aim.com"]GabbyGrace@aim.com[/EMAIL].
     6. In the Mail Server (Incoming): box,      type **imap.aol.com** or **imap.aim.com**.
     7. In the User Name: box, type your      **AOL®** or **AIM® screen name**.
     8. In the SMTP Server (Outgoing): box,      type **smtp.aol.com** or **smtp.aim.com**.
     9. Click the Allow authentication box to      place a check mark in it.
     10. Under Category:, click the      Incoming Mail icon.
     11. Next to Server configuration:, choose      the **IMAP** option by clicking it.
     12. Click the OK button. 


[ref: [http://help.aol.com/aimhelp/dynamickc.do?externalId=http--helpchannelsaolcom-kjumpadparticleId217451&sliceId=&command=show&forward=nonthreadedKC&kcId=http--helpchannelsaolcom-kjumpadparticleId217451]]("http://help.aol.com/aimhelp/dynamickc.do?externalId=http--helpchannelsaolcom-kjumpadparticleId217451&sliceId=&command=show&forward=nonthreadedKC&kcId=http--helpchannelsaolcom-kjumpadparticleId217451%5D")



---

### Post by AAM on 2007-05-26
I have just looked inside Evolution and it has IMAP format connections! (I knew this but thought I would check for sure)

---

### Post by Eycks on 2007-06-19
I was able to get evolution to send mail but not receive.  Sending uses smtp server and the server line is smtp.aol.com:587.  Does receiving require a port? The program hangs when I add a port to the receiving line, imap.aol.com.

---

### Post by ololad8 on 2007-07-01
no i dont believe there is a port required. i have aol mail in evolution my settings are

imap.aol.com
username

ssl encryption
password: check for supported types

---

### Post by iamdennisthomas on 2008-03-16
thanx buddy. ur setting info really worked for me.

---

### Post by malangaman on 2008-03-22
i just set up AOL mail on evolution using:
imap.aol.com ( for both send and receive).
username

ssl encryption
password: check for supported types

---

