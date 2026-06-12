---
title: "Can't send emails"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by flash on 2005-10-13
I'm trying to get my email working. I can recieve but can't send. It keeps asking for the password to connect to the server. I've tried every password that I ever could have possibly used and can't get it to go. I have sbc yahoo dsl. I've opened everything on evolution to see if there is anything about passwords and also checked help which were of no use. Anyway I can start over and maybe pay a little more attention this time? Anybody got any ideas?

---

### Post by GreyFox503 on 2005-10-13
I don't use Evolution, but it sounds like it has nothing to do with Ubuntu.  I think it's just the password needed by your ISP to give you your email.  If you don't remember setting a pword with SBC, then I'd give them a call, or visit the SBC website and try to view your mail or set up an account there.

---

### Post by ddemers on 2005-10-13
Not sure about evolution, but seems as though you have it set up wrong.  Chances are you dont need a username/password to be able to send emails (usually just to receive, although it depends on the email service).  Check the settings for the email servers and try setting it up to not require a username/password for sending emails.

---

### Post by flash on 2005-10-13
So where do I look to find the email servers? I've clicked on just about everything on there. Somewhere I read that sbc didn't require a password for email anyway, maybe that's it. I still don't know how get to the server settings. Isn't there one of these command line thingies I could do to just stop it from looking for a password? Isn't that how it's suppose to work?

---

### Post by flash on 2005-10-13
Just a little update. I just got off the phone with sbc and they can't help me much. What we did determine was that the acct. that I created does indeed work( we set it up in OE and the password worked). So it's something in the settings in evolution that is screwing things up. Any ideas will be tried.

---

### Post by GreyFox503 on 2005-10-14
This isn't a true solution, but you could try another email client like Thunderbird (from Mozilla) or Kontact (part of KDE).

---

### Post by flash on 2005-10-14
Is there a way to uninstall evolution and reinstall and go through the setup again? Sbc said it uses authentication but not a certain kind(I forgot what kind it was) and I'm thinking that's the problem.

---

### Post by ddemers on 2005-10-14
In Outlook the settings are 
Tools->Accounts-> Mail Tab, double click on your account and go to the servers tab.  I think kthere is a check box for something about authentication required for outgoing mail.  

These settings are probably under either

Edit->Preferences
or
Tools->Accounts/Options
Ive never used Evolution, but its probably similar to other email clients.

---

### Post by flash on 2005-10-14
We did the outlook thing on my windows machine to see if there was a problem with the acct. I can't find anything like that on evolution. The only thing I can find that would be close is about proxy servers and I don't think that has anything to do with it. What I was thinking was if I could get back into the setup program, maybe there was something in there that needed to be checked or unchecked. I tried the clear password button and tried it again and that made no difference.

---

### Post by xeta on 2005-10-14
Go to:

Edit
Preferences
Click on "Mail Accounts"
Select your profile on the right and click "Edit"
Go to the "Sending Email" tab and make sure "Server requires authentication" is NOT checked. Also make sure you are usign the proper SMTP server.

---

### Post by flash on 2005-10-14
OK, did that and it was not checked. (This is the section I've been trying to get to  for the last day and a half). smtp server was also correct, I thought I might have had a typo. Any other ideas?

---

### Post by rjwood on 2005-10-14
your password is probably the same as your incoming

---

### Post by rjwood on 2005-10-14
[quote=xeta]Go to:

Edit
Preferences
Click on "Mail Accounts"
Select your profile on the right and click "Edit"
Go to the "Sending Email" tab and make sure "Server requires authentication" is NOT checked. Also make sure you are usign the proper SMTP server.[/quote]
make sure it is checked

---

### Post by n9uib on 2005-10-14
I have Ameritech and had no problems setting it up....so if you still need help, get  in touch with me and i will walk you thru it....

steve

---

### Post by flash on 2005-10-14
I tried it both ways and still the same. Steve, if you mean a phone call, I have unlimited long distance so I could call you.

---

### Post by flash on 2005-10-14
I just had a thought. Info I got from sbc about pop and smtp also had info on incoming and outgoing ports.  Is it possible for these ports to be wrong? Anyway to check this info?

---

### Post by xeta on 2005-10-14
[QUOTE=flash]I just had a thought. Info I got from sbc about pop and smtp also had info on incoming and outgoing ports.  Is it possible for these ports to be wrong? Anyway to check this info?[/QUOTE]

hmmm..good thought but, since it worked in windows automatically I would assume the ports are default. What are you using for an SMTP server?

---

### Post by flash on 2005-10-14
smpt.sbcglobal.yahoo.com

---

### Post by n9uib on 2005-10-14
well, i dont think a phone call would be neccessary, but what ever u wanna do.... i have all the messangers...... i would be willing to help u on there

steve

---

### Post by flash on 2005-10-14
Just did a reread, and you might be mistaken. The test was on a completly different computer. The one I'm trying to get going is a stand alone with only ubuntu on it.

---

### Post by flash on 2005-10-14
Steve, just saw your thread and whatever you think would help

---

### Post by n9uib on 2005-10-14
if you have any messangers....... i owuld like to talk to you on there....... if not , my email is     [email]n9uib1967@ameritech.net[/email] and i will get u the phone number on there


steve

---

### Post by n9uib on 2005-10-14
well, that was stoopid..... sorry.......    number is  317-889-9776

steve

---

### Post by flash on 2005-10-14
Steve, you're a genus! Problem solved everyone. The solution, To click on "never" for using a secure connection.

---

### Post by n9uib on 2005-10-15
*bows to the crowd*   , it wasnt really a big deal......   good old stoopid ameritech and their dumb settings !!!!!

---

