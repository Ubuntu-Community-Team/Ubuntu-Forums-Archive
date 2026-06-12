---
title: "A Newbie Lost in LINUX NEEDS Help"
date: 2008-05-31
forum: Alabama Team - US
---

### Post by SCURVER on 2008-05-31
****** I am reading all that I can find, but at this point am about to go under for the third time! I have an old Dell desktop running MS XP Pro onto which I have loaded UNBUNTU 7.10. This is running alongside the MS O.S. and it seems okay; my problems are that while I have LINUX up and running I have a LOT of headaches such as can't send e-mail (receiving seems to work o.k.), and can't load any updates, (up-date manager thingy seems broken.)

     So where do I find help for all of this? 

                                   Scurver

---

### Post by Eutaw on 2008-05-31
> **SCURVER said:**
> ****** I am reading all that I can find, but at this point am about to go under for the third time! I have an old Dell desktop running MS XP Pro onto which I have loaded UNBUNTU 7.10. This is running alongside the MS O.S. and it seems okay; my problems are that while I have LINUX up and running I have a LOT of headaches such as can't send e-mail (receiving seems to work o.k.), and can't load any updates, (up-date manager thingy seems broken.)

     So where do I find help for all of this? 

                                   Scurver
A little more specific info would help us help. Which email client are you trying to use? Are you getting any popup messages when you try to update? Any other problems, try to be as specific as possible, as that will give us clues for help.

---

### Post by crane on 2008-06-02
Like Eutaw said, I little more info would be real helpful. Double check you sever settings in your email client. Make sure nothing is mistyped or set wrong. Make sure you have the correct protocol set (POP or IMAP). It seem odd that you can recieve and not send. That really sounds like a server setting.
 Also have you tried using apt-get commands to get update?
sudo apt-get update
sudo apt-get upgrade

This could let you know if it is apt getting the error or the update manager program.

Just a couple of thoughts. If you have tried them then please let us know what errors you have seen.

---

### Post by SCURVER on 2008-06-02
> **Eutaw said:**
> A little more specific info would help us help. Which email client are you trying to use? Are you getting any popup messages when you try to update? Any other problems, try to be as specific as possible, as that will give us clues for help.

****** Okay and thanks for the response! I am using Evolution as my e-mail client. And yes, regarding popup messages I get this message that says that I should report the faulty update manager thingy. That's great, but how would I do that? I can find no instructions applying to such reporting...

     A long time ago, when the Internet was in it's infancy, those of us working with such communications had to contact others who were using the same stuff. Today I have this problem with my communications software, but when my e-mail is shut down, I have no way to communicate this problem with anyone. The name/tel #/ e-mail address of someone in my area with whom I might communicate regarding LINUX would be a godsend. I live in Daphne, AL, Zip code 36526, with my tel # as 251-626-9345. I know that there is at least one UBUNTU user in Mobile, across the bay from me, but don't know how to contact this person.

     And yes, it may be that I've messed up the sending aspect of the protocol associated with EVOLUTION, but I can't figure out what to do about that as it appears to me that it is all set up correctly... I just need to have someone with whom to speak about LINUX......

                           Thanks,

                              SCURVER

---

### Post by SCURVER on 2008-06-02
> **crane said:**
> Like Eutaw said, I little more info would be real helpful. Double check you sever settings in your email client. Make sure nothing is mistyped or set wrong. Make sure you have the correct protocol set (POP or IMAP). It seem odd that you can recieve and not send. That really sounds like a server setting.
 Also have you tried using apt-get commands to get update?
sudo apt-get update
sudo apt-get upgrade

This could let you know if it is apt getting the error or the update manager program.

Just a couple of thoughts. If you have tried them then please let us know what errors you have seen.

Okay.....I had not tried the sudo get thingy until right now. I entered in "sudo apt-get UBUNTU8.04" and got nothing.....But I'm now thinking that I'm way off base again.....I think that my email client protocol is POP and that's what I did enter already........Still lost at sea in LINUX I need someone with whom I may speak about this operating system. I located the mapping thingy and saw that there is at least one UBUNTU user over in Mobile, but don't know how to contact that person. The mapping thingy is, to me at least, just like all of the LINUX stuff, a lot of material, but no instructions on how to use it all, or any at all......Thanks for your response....................SCURVER

---

### Post by crane on 2008-06-02
> **SCURVER said:**
> Okay.....I had not tried the sudo get thingy until right now. I entered in "sudo apt-get UBUNTU8.04" and got nothing.....But I'm now thinking that I'm way off base again.....I think that my email client protocol is POP and that's what I did enter already........Still lost at sea in LINUX I need someone with whom I may speak about this operating system. I located the mapping thingy and saw that there is at least one UBUNTU user over in Mobile, but don't know how to contact that person. The mapping thingy is, to me at least, just like all of the LINUX stuff, a lot of material, but no instructions on how to use it all, or any at all......Thanks for your response....................SCURVER

OK, while your running Ubuntu, open a terminal.
Click on accessories>terminal
now when the terminal opens.
Type the following
sudo apt-get update
it should ask for a password.Enter you password and hit enter.
Then after it updates everything type the following.
sudo apt-get upgrade.
It may ask you if you want to install updates type Y for yes and let it do it's thing. This will upgrade your system. It may even fix the updater problems.
If it gives you any errors post them here and we can help out. 

Also on our mail account. I may have said it wrong earlier. Depending on who the account is with. Alot of the ISP's account a POP for incoming mail and the outgoing should be smtp. example:
outgoing server : pop.charter.net
incoming server : smtp.charter.net

if that does not work you could try mail protocol. (example : mail.charter.net) some use that as well. If you are able to receive emails then there is no reason to mess with your incoming server settings.

if none of this works. The first thing I would suggest is calling your ISP or your mail provider and finding out what the protocols should be.

Good Luck.

---

### Post by Tomatz on 2008-06-02
Sounds like an mtu packet size problem to me. Do you use an asdl modem provided by your isp or your own router?

---

### Post by SCURVER on 2008-06-02
> **crane said:**
> OK, while your running Ubuntu, open a terminal.
Click on accessories>terminal
now when the terminal opens.
Type the following
sudo apt-get update
it should ask for a password.Enter you password and hit enter.
Then after it updates everything type the following.
sudo apt-get upgrade.
It may ask you if you want to install updates type Y for yes and let it do it's thing. This will upgrade your system. It may even fix the updater problems.
If it gives you any errors post them here and we can help out. 

Also on our mail account. I may have said it wrong earlier. Depending on who the account is with. Alot of the ISP's account a POP for incoming mail and the outgoing should be smtp. example:
outgoing server : pop.charter.net
incoming server : smtp.charter.net

if that does not work you could try mail protocol. (example : mail.charter.net) some use that as well. If you are able to receive emails then there is no reason to mess with your incoming server settings.

if none of this works. The first thing I would suggest is calling your ISP or your mail provider and finding out what the protocols should be.

Good Luck.

******

     I followed your instructions re the sudo apt-get update  and upgrade, but there were a lot of errors so nothing actually worked. I'll try the incoming/outgoing protocols for my mail client and get back to you on that...............Thanks,

                                SCURVER

---

### Post by crane on 2008-06-02
[QUOTE=SCURVER;5102721]******

     I followed your instructions re the sudo apt-get update  and upgrade, but there were a lot of errors so nothing actually worked. I'll try the incoming/outgoing protocols for my mail client and get back to you on that...............Thanks,

                                SCURVER[/QUOTE

Also be sure to post some of the errors you get from the console. Could help with finding the problem.

---

### Post by michaelramm on 2008-06-03
Scurver,

I have added you to the Ubuntu LoCo map. It looks like that there are 2 folks in the mobile area (PharmD24 and BrooksofSheffield). You can try to send them a Private Message via the forums, and I think that they may subscribe to the mailing list also.

There is a South Alabama Linux Users Group that is based out of Mobile. They have an email address at [email]nullpointer@salug.org[/email]. You might send them an email explaining your situation and see if someone might be willing to visit your home.

It is very hard for us to try to diagnose your problem from so far away. Computer troubleshooting is so hands on that it is difficult to understand what you are trying and the output that you are getting.

But we will continue to help in any way possible.

Michael

---

### Post by Tomatz on 2008-06-03
> **crane said:**
> [QUOTE=SCURVER;5102721]******

     I followed your instructions re the sudo apt-get update  and upgrade, but there were a lot of errors so nothing actually worked. I'll try the incoming/outgoing protocols for my mail client and get back to you on that...............Thanks,

                                SCURVER[/QUOTE

Also be sure to post some of the errors you get from the console. Could help with finding the problem.

Does this page load quickly?

[http://www.orangeproblems.co.uk/phpBB2/](http://www.orangeproblems.co.uk/phpBB2/)

Also you could try this:

[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by SCURVER on 2008-06-03
> **crane said:**
> [QUOTE=SCURVER;5102721]******

     I followed your instructions re the sudo apt-get update  and upgrade, but there were a lot of errors so nothing actually worked. I'll try the incoming/outgoing protocols for my mail client and get back to you on that...............Thanks,

                                SCURVER[/QUOTE

Also be sure to post some of the errors you get from the console. Could help with finding the problem.

***Okay...I checked back with my ISP re the problematic e-mail client's failure to send messages and got the same protocols that I was using, so that's not a problem. And interestingly, yesterday I replied to a long message from a step-daughter re my wife's Alzheimer disease and the e-mail client sent the message! In fact, it sent a host of un-mailed messages that were in the outbox, all except those containing photographs. So one problem clears up (for some unknown reason), yet the new problem of not sending photos rears it' ugly head.....Anyway, thanks very much for sharing your comments and suggestions with me; now to move on to the new problem and the problem about getting the updates and upgrades...

                                   Thanks,

                                 SCURVER

---

### Post by SCURVER on 2008-06-03
> **crane said:**
> [QUOTE=SCURVER;5102721]******

     I followed your instructions re the sudo apt-get update  and upgrade, but there were a lot of errors so nothing actually worked. I'll try the incoming/outgoing protocols for my mail client and get back to you on that...............Thanks,

                                SCURVER[/QUOTE

Also be sure to post some of the errors you get from the console. Could help with finding the problem.

***Okay...I checked back with my ISP re the problematic e-mail client's failure to send messages and got the same protocols that I was using, so that's not a problem. And interestingly, yesterday I replied to a long message from a step-daughter re my wife's Alzheimer disease and the e-mail client sent the message! In fact, it sent a host of un-mailed messages that were in the outbox, all except those containing photographs. So one problem clears up (for some unknown reason), yet the new problem of not sending photos rears it' ugly head.....Anyway, thanks very much for sharing your comments and suggestions with me; now to move on to the new problem and the problem about getting the updates and upgrades...

                                   Thanks,

                                 SCURVER

---

### Post by cptr13 on 2008-09-10
Hey!!!  Fairhope here *waves madly*.  Unfortunatly I'm one of the least technically savvy people on these forums, but I'm fairly comfortable with Ubuntu as I've been putzing with it a little over a year.  Feel free to pm me and I'll give you my contact info.  Otherwise, as noted above, there is a somewhat active Linux users group in Mobile with plenty of Ubuntu users there to talk to.  The website is SALUG.org and there's a meeting this saturday in mobile.  

Hope to hear from you....

---

### Post by kg4cna on 2008-09-11
> **SCURVER said:**
>  So one problem clears up (for some unknown reason), yet the new problem of not sending photos rears it' ugly head.

                                 SCURVER

So, it sends text messages fine...but not photos. Have you thought about the file size on the photos you're trying to send?  Maybe they're too big and the server won't allow it.  Just something to think about.

Thanks,
A

---

