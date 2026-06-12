---
title: "Proposal"
date: 2007-06-23
forum: California Team - US
---

### Post by miggl on 2007-06-23
I would like to make a proposal for a project we could undertake. I haven't researched if any other teams are already working on this (but if there are, we could have joint efforts). Here's the concept:

Create an application suite and configure in Ubuntu in such a way, that it can be implemented in enterprise environments.

This means finding alternatives to, and integrating, the following enterprise software:
- ActiveDirectory (domain configuration, user policy administration)
- Exchange (centralized email server, using domain and user profiles)
- Outlook (robust email, calendar, task, and meeting management system)
- Ghost (a network deployment mechanism for administrators)

Some specialized software, for specific business needs:
- Quicken (financial software package for small and medium businesses)

This also may incorporate thick- as well as thin-client scenarios.

I see the following requirements for this project:
1) Provide OpenSource (not necessarily free) alternatives to the above mentioned applications.
2) Provide migration mechanism to painlessly migrate your systems.
3) Provide the ability for any of the windows systems to work with any of the linux systems, and vice-versa, should a business decide to only implement certain aspects.

The ultimate goal is to be able to replace what businesses have taken for granted from Microsoft, and show them that Ubuntu can do it as well. There are several businesses that have moved to Ubuntu (I saw a page with the listing somewhere, I'll have to look for that again) successfully. Perhaps we can learn from their experiences and build a pre-set package to achieve this. We could call it Enterbuntu (Enterprise Ubuntu), or BUbuntu (Business Ubuntu), or something like that.

I think this would make many other endeavors possible, and would achieve Ubuntu, and Linux, to be recognized as viable alternatives in business as well as on private desktops.

What are your thoughts?

Cheers,
Mike

---

### Post by gaten on 2007-06-23
This would be a project I would dive head first into. I am a computer consultant for small businesses, and as anyone who works the SB knows, 

Small Business == Windows, Office, Outlook, Exchange and Quicken.

And it annoys me. The businesses that need to save money the MOST are paying the most for bloated software because Techs are too afraid to try something else. 

Am I willing to try something else? Yes, but my boss isn't ;) So I would need a working prototype/ demonstration to prove to him that Ubuntu IS worth spending time on, and is a viable solution. 

The biggest hurtle that I see is exchange. Yes, I know Linux has a **ton** of mail servers, but if a company already has a Windows 200x server, they would be **loosing** money by changing to an Ubuntu one. 

So, we would need to be able to talk to Exchange with its native protocol. An idea that has yet to be implemented in any respectable fashion, from what I've read.

---

### Post by miggl on 2007-06-24
Great to see someone else shares my pain! :) hehe
I am starting up a small business with a partner, and we want to start with Ubuntu from the get-go. Currently we haven't seen anything that can integrate as well and compete with the windows (shmindows) products.
I would love to be able help contribute and develop (not necessarily program, but put together, and integrate) a small business version of Ubuntu as I described in the above post for my company.

I don't want to keep this for myself of course, especially if we decide to adopt it as a LoCo Team project; it should be made available to the entire world to use, and see how great Linux (and Ubuntu) really is.

I see the following requirements for this project:
1) Provide OpenSource (not necessarily free) alternatives to the above mentioned applications.
2) Provide migration mechanism to painlessly migrate your systems.
3) Provide the ability for any of the windows systems to work with any of the linux systems, and vice-versa, should a business decide to only implement certain aspects.

Cheers!
Mike

---

### Post by miggl on 2007-06-25
I have been able to dig up the following tools that would potentially help replacing the respective Windows equivalent:
- Norton Ghost: G4L [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
- ActiveDirectory: OpenLDAP [http://www.openldap.org/](http://www.openldap.org/)
- Exchange: Mail Master(?) [http://www.linuxmailmanager.com/;](http://www.linuxmailmanager.com/;) Scalix(?) [http://www.scalix.com/](http://www.scalix.com/)

Any other suggestions?

---

### Post by gaten on 2007-06-25
Mail Master demo didn't work for me, so as of now I'm not impressed. I've been looking at SquirrelMail ([http://squirrelmail.org](http://squirrelmail.org)) + Courier IMAP + PostFIX MTA etc. It looks like a LONG and complicated setup, so I'll let you know if I ever actually get it up and running. A good tutorial (Ubuntu specific) is here: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by cb951303 on 2009-03-03
There is [Zimbra]("http://www.zimbra.com/") which for many people is really a lot better than Exchange but I think it has 2 versions. OSS and commercial. I don't know the difference between them

For Outlook, why not use Evolution? or Thunderbird with calender plugin?

If you need webmail, there is a very cool looking AJAX client in development: [http://roundcube.net/](http://roundcube.net/) It needs some time but when it's done it will rock. For now I don't recommend it. My apache log is full of roundcube looking bots, meaning it has a lot of security vulnerabilities right now. Not a shock since it's a beta software.

osalt.com's alternatives to active dirictory:
[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)
[http://directory.apache.org/](http://directory.apache.org/)

---

### Post by grantbow on 2009-03-27
Hey there.  This sounds interesting.  You guys are welcome to post to the mail list or come into IRC and talk about it with whoever is online at the time.

[https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-ca](https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-ca)

[https://wiki.ubuntu.com/CaliforniaTeam/Meetings/](https://wiki.ubuntu.com/CaliforniaTeam/Meetings/)

---

