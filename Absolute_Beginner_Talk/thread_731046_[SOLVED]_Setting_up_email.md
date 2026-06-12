---
title: "[SOLVED] Setting up email"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by vmeek on 2008-03-21
Hi,
I am an absolute Ubuntu begginer. I would like to move over to the Linux operating system. I am using a live cd version 7.04 of Ubuntu which accompanied the Computer Active magazine Ultimate Guide to getting started with Linux, try out the Linux system.

The problem I need help with is getting my email settings to work. I am able to get on line and browse the internet using Firefox but I cannot get my emailing to work. I have worked through the workshop in the magazine but cannot send or receive emails. My internet service provider is Karoo. 

I would appreciate any help anyone can give.

Thankyou,

Vic Meek.

---

### Post by plucky on 2008-03-21
Welcome to Ubuntu.

The email client that Ubuntu uses is called **Evolution**

The setup information you need is the name and type of servers that your ISP use.For you from the Karoo website, they are POP for incoming email and SMTP for outgoing email.

The server names are for pop [indent]pop.karoo.co.uk[/indent] and for SMTP [indent]smtp.karoo.co.uk[/indent] and your username should look like [indent]username@username.karoo.co.uk[/indent] 

Your password is that provided by your ISP and is case sensitive.

Remember to tick the **"Remember password"** box when you setup the account.When you finish and click the Send/Receive box,Evolution will ask for your password,enter it and press return.

You should now be set.


Good luck

---

### Post by vmeek on 2008-07-10
Thank you Plucky for your response to my problem. Sorry it has taken so long to get back in touch. I have now upgraded to Ubuntu 8.04. I can now send emails as well as being able to browse the internet. I am still unable to receive emails. If I send myself an email I receive it in Outlook Express but not in Evolution. 
I get the following error message:- 

Unable to connect to POP server popmail.karoo.co.uk.

Error sending username:- ERR unknown command "Pass".

Please enter the POP password for vmeek@karoo on host popmail.karoo.co.uk.

Is there a difference between POP3 and POP. Karoo refer to POP3 as being the mail server but Evolution refer to POP.

I'm desperate to get Evolution working fully so I can dich XP. 
Any  help would be greatly appreciated.

Vic Meek.

---

### Post by plucky on 2008-07-10
> Is there a difference between POP3 and POP. Karoo refer to POP3 as being the mail server but Evolution refer to POP.

No there isn't any difference.According to the karoo.co.uk site,you set up is the same as for Outlook express i.e your username = "username@username.karoo.co.uk" and not your email address which is "myname@username.karoo.co.uk"

This is what it says on the karoo site >     *  The outgoing mail server (SMTP) should be set to smtp.karoo.co.uk
    * The incoming mail server (POP) should be set to pop.karoo.co.uk
    * In the 'Incoming Mail Server' section, 'Logon using' should be selected, and you should enter your username and password in the boxes provided.
    * Your username and password were chosen when you set up your account with Karoo.
    * As a guide, if your email address was, for example, 'myname@username.karoo.co.uk', your username would be 'username@username.karoo.co.uk'. Your password is case sensitive, so you must enter it in lower case letters.
    * 'Logon using Secure Password Authentication' should not be selected.
    * In the 'Outgoing mail' section, the 'My server requires authentication' option should not be selected.



Good Luck

---

### Post by vmeek on 2008-07-11
Hi Plucky,
Thank you for your very quick reply. After working through your instructions I am delighted to say that Evolution is now working fully. I am over the moon. 
Many thanks,
Vic Meek.

---

