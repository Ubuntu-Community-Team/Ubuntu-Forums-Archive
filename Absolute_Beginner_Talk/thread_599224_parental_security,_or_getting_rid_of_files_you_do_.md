---
title: "parental security, or getting rid of files you do not want..."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-01
5 ppl, one computer as of yet.

I know I can set up various ways of restricting what my kids access on the web. 

I know that they cannot open files that only I have permissions for (right?).

I hvae not restricted their access yet. Honestly I do not think I really need to BUT the oldest had some friends over and I heard what they were telling Aron to look for. He actually said no to them... but how can I check up on what he has been visiting?

in other words, where do I go to find all the histories, all the down loads, all the temp files, etc. to know just who has been looking at just what?


sorry for such a n00b question but with a 15 year old a 13 and an 11 year old  I get worried sometimes, esp. when the friends suggest stuff..

thanks

robi

---

### Post by damotor on 2007-11-01
There are several ways, for example if you are able to login with his user or if you have administrator access you could check the history and the downloads of his browser if he didn't deleted them. Other posibility will be to install a sniffer like wireshark wich records everything that goes by your network. Althoug I think that the best way to deal with this matter will be to talk calmly with your kids.
Anyway, mozilla & firefox history, downloads etc are in /home/YOUR_USER/.mozilla
depending on the browser he uses. look for the Cache directory, the file history.dat, download.rdf, etc

---

### Post by beanco on 2007-11-02
The serious, yet calm talks have taken place. Think that is one reason he said no to his friends.

I am not living in a fantasy world, I know kids will look for stuff they should not look for, heck we all did that when we were growing up. 

What I am more afraid of is stuff getting on that the youngest should not see.

The other thing is games, the kids are allowed to use the computer for school work, not for gaming/chatting, etc.

I would like to check that this is what they are actually doing...

I can log onto all of their accounts but they know enough to delete the histories in epiphany and firefox. That is why i need to know where to look on the computer.... 

thanks

robi

---

### Post by Officer Dibble on 2007-11-02
I'm in the process of learning my way around DansGuardian... which looks very promising.

For monitoring purposes, do you use a router? Many routers today, if not all, keep a log of sites visited. Mine mails me the log every day which allows me to just scoot through the list once a week. My children know about this so it isn't a mistrust thing its a anti-mischievousness measure. :)

But, like you, I want to protect them from the material and scenarios that are predatory and entrapping. They are only allowed to access the 'net with XP and Cybersitter until I get my head around Dansguardian,

---

### Post by beanco on 2007-11-02
wel I do not have a router yet since I have only one computer. We all share that.

one other thing just occured to me... besides knowing where they have surfed I would also like to be able to delete junk they down load.

The olest is getting into video editing and often downloads stuff to add to his films...he tends to be a pack rat and hordes stuff... I need to go routine cleansings to keep the computer uncluttered.

Now if I could find out where ubuntu stores things i would be able to delete at wil.


robi

---

### Post by ushills on 2007-11-02
Dansguardian is perfect for web access restriction and web logging, although it can be quite difficult to set up there are many how-to's on this site.

I have an installation guide and sample configuration that work on my site here [http://www.ushills.co.uk/ubuntu/dansguardian.html](http://www.ushills.co.uk/ubuntu/dansguardian.html), however, some of the setting will need to be changed.

---

### Post by stalker145 on 2007-11-02
On the interent side of the discussion:

If you are concerned about certain lewd or pornographic sites, you can use [OpenDNS]("http://www.opendns.com"). Setting up your DNS servers through the root account and not allowing your users to alter that should take care of that issue.
OpenDNS also allows you to look at any blocked sites that were attempted and makes pretty graphs of internet usage.

On the downloading (size) side of the discussion:

If it's the use of hard drive space that is the problem, you can always set up disk quotas for your users. You can set quotas so that they can only have a certain amount of disk space used or a certain number of files allowed. Once that limit is reached, they're not able to add anything until their space is cleaned out.



Neither of these "solutions" requires a lot of work nor massive download/installation of programs. OpenDNS requires nothing but changing your DNS settings and Quotas may require installing the appropriate programs from the Ubuntu repos.

Good luck, and check back if you need more.

---

### Post by gn2 on 2007-11-02
Come on, be honest, you don't want the kids (or the wife) to know what you've been looking at!

---

### Post by Xbehave on 2007-11-02
for a different problem i used a  permissions based solution and firefox profile switcher extension. this however depends on your user setup, e.g if your kids have separate accounts its much harder (but still simple enough)
if all thier directories have the group users
then all you have to do is give read writes to their profiles for groups
```
chmod u+r -R /home/<name>/.mozilla/ 
```
*check the code its just a guess
then set it up in the "firefox profile switcher extention" so you can switch into thier firefox's from your account

problems with this method
1) they would also be able to do this if they knew how (this can be got around with a 'firefox 'group theyre not members of but you are)
2) if they delete thier history and cookies then its gone

advantages
1)no extra software
2)familiar view of history

---

### Post by beanco on 2007-11-02
thanks for the info on opendns and dansgaurdian.

As for them seeing what I have been looking at, of course I do not want that but that is not the point of this thread.

robi

---

### Post by ushills on 2007-11-02
I use openDNS for remote logging as you can access it though any web browser, full installation instructions are on their website and you need to set up a dynamic IP service for full functionality.

Really easy to do and the reporting is top notch.

---

