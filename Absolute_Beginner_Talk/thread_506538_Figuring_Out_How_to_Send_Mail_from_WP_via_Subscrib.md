---
title: "Figuring Out How to Send Mail from WP via Subscribe2 Plugin"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by JeniQ on 2007-07-21
Greetings. 
Let me catch you up. :) 
I am attempting to move [my blog]("http://www.jeniqblog.com") from Blogger but am having a difficult time replacing the BlogSend/Send to Email feature that works so easily in Blogger. I am running Wordpress 2.2.1 and S2 3.6 on a local Ubuntu Server (ver: Fiesty Fawn). My domain is hosted by GoDaddy and am using DynamicDNS to host the site off my Ubuntu server. 

I am trying to use a plugin called Subscribe2 to email posts to my blog to subscribers. I am having difficulty. Here is the [letter I wrote]("http://subscribe2.wordpress.com/2007/06/24/subscribe2-220-and-36/") to the Subscribe2 author:

"I installed ShiftThis Swift SMTP and have successfully sent e-mail from the test page. I was able to get the Subscribe2 plugin installed and activated. I got my Subscriptions page created and it's working, too. I changed `@wp_mail(` to `@mail(` in my Subscribe2.php file. Now I am able to successfully create posts and use the Write | Mail Subscribers features without getting any errors. I get success notes, in fact! 

However, I've never actually received any email from posts or the Mail Subscribers feature. (I have one registered and two confirmed user signed up.) 

I know you suggest that we contact out hosting service to see if our outbound email is getting blocked. Does that mean I need to have some sort of mail service established with my hosting service, GoDaddy? When I set up my domain, I simply pointed it to the DynamicDNS servers of the service I provided. I didn't use any of their other tools. 

I am a novice with all of these products (WP, Ubuntu, etc.). I feel like I'm missing some essential, vital, obvious piece of information, like I need to have Exchange installed, hahaha! 

I would love any troubleshooting suggestions you could make about why mail is not getting sent. (I've checked spam folders and mail's not being diverted.) Thanks, in advance, for your help." 

This is the reply I got today:
"First if you are using a local server to host your blog you really shouldn't need to use Swift SMTP and by changing instances of wp_mail to mail you are bypassing it anyway. 
If your emails are not arriving then I can only presume that sendmail (or an alternative) is not running on, or is blocking, your emails on your local server. To solve this I'd guess you need to check in the Ubuntu forums or post a question." 

So, here I am. I don't really know what I'm doing but I can follow instructions and I'm not intimidated by my CLI. :) I think that the guy is right, some mail program/service/thingy is not installed on my machine. 

After searching through the forums, I attempted to install Postfix by running `apt-get install postfix` (via SSH). It seemed to work OK until it got to the Postfix Configuration page. It give me a detailed description of the 5 different configuration choices. I have to hit Esc to get out of this window and then it takes me to a window where I can actually pick one of the 5 different configuration options. I'm convinced I want to choose Internet Site, so I arrow down to that choice, then right arrow to hit OK. When I hit Enter, the screen flashes and I'm back to the detailed description page. It's a loop I can't figure out how to get out of. I have to just close down the SSH window and reopen it. 

I also [tried this]("https://help.ubuntu.com/community/Postfix") but it errored out and said that several of the libraries couldn't be found.

Can anyone offer me advice as to what might remedy my situation? Would having PostFix installed, or SendMail installed fix my problem? Is there an solution made for people like me? Thanks, in advance, for your help.

---

### Post by tarek on 2007-07-22
OK. What I understand is that you cannot send mail from Ubuntu.

Does your ISP provide an smtp service?

TK

---

### Post by JeniQ on 2007-07-22
By my ISP, I'm guessing you mean Time Warner, which provides my internet service, and not GoDaddy, which provides my Domain Hosting service. 
I do not know if SMTP hosting is possible/available with the service I have from Time Warner. I thought, for some crazy reason, that it would try to send on behalf of my gmail address, as that's the address I have set up in WordPress.

---

### Post by HermanAB on 2007-07-22
Most ISPs block port 25 to prevent dumb Windows users from flooding the world with junkmail.  Therefore you have to configure postfix to relay mail via your ISP mail server for example add to the end of main.cf:
relayhost = mail.timewarner.com
(or something like that)

See the postfix.org site for details.  Otherwise, if you are lazy like me and just want to set your servers up with a point and click, use Mandriva, install the 'wizards' package and click away...

'Hope that helps!

Herman

---

### Post by JeniQ on 2007-07-23
Hello Herman, 
I attempted to install PostFix three times. 
The first two times, this happened: After searching through the forums, I attempted to install Postfix by running `apt-get install postfix` (via SSH). It seemed to work OK until it got to the Postfix Configuration page. It gave me a detailed description of the 5 different configuration choices. I have to hit Esc to get out of this window and then it takes me to a window where I can actually pick one of the 5 different configuration options. I'm convinced I want to choose Internet Site, so I arrow down to that choice, then right arrow to hit OK. When I hit Enter, the screen flashes and I'm back to the detailed description page. It's a loop I can't figure out how to get out of. I have to just close down the SSH window and reopen it. 

Then, I tried using the instructions here: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but during the installation, it errored out saying that several of the libraries couldn't be found. 

So PostFix is not wanting to install, for whatever reason. 

Your other suggestion, for lazy people (which I am!) was to use Mandriva. I'm checking out the Mandriva website and I'm not sure exactly which product you're suggesting. It looks like a paid operating system, not a mail program like PostFix. I have the Ubuntu OS installed. Does Mandriva have some kind of mail program that works on Ubuntu?  
Thanks, Jennifer

---

### Post by JeniQ on 2007-07-23
Ah-ha, I got PostFix installed! Yay me. 

So, how do I know if Time Warner is blocking my outbound mail? Do I have to call them? Can someone arm me with something intelligent to say when I do call?

---

### Post by JeniQ on 2007-07-23
PostFix installed, but I'm not surewhat to do with it. How do I make it "work?" 

Is there some basic tutorial out there that someone could point me to about how to achieve my goal, which is to send email to a few email addresses once my blog is updated? 

Thanks,
Jennifer

---

### Post by JeniQ on 2007-07-25
Well, I installed PostFix and restarted my server, and now somehow, I have no how, Subscribe2 appears to be working. I am mystified.

---

