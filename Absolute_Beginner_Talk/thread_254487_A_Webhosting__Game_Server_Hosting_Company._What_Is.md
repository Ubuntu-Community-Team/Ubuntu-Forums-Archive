---
title: "A Webhosting / Game Server Hosting Company. What Is Best To Use For Linux?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by RackNetz on 2006-09-10
Hello All.

I Just Found This Great Software Through A Freind Of Mine.

My Questions Is:

is this like linux but with a desktop feel so you don't need to use SSH to do stuff like make folder, delete, copy and paste and install apps?

My company uses linux systems to host the following:

- Game Servers E.G Call Of Duty, Counterstrike,Battlefield etc
- Webhosting, Using Webpanels Like Plesk,Cpanel,Xpanel,Layerd Panal
- Teamspeak Server Hosting (Veriety Of Ports Need To Be Open)
- Shoutcast Hosting (Veriety Of Ports Need To Be Open)

What product would you advise me to use to host these services on a linux system?

Do you need to have centOS or Debian installed to run the product you advice me on using?

Finaly last question : Does The product You Advise Me To Use Install These Softare Packages Aswell as the actual product:

- Apache
- PHP 4 or 5
- MySQL
- SSH
- FTP Server
- DNS Server
- Email Server

If you can answer these questions I would appriciate it. I am always willing to try new things out. The way I see it I am having to use linux for my servers. I have no linux experience what so ever and know not a single code. People say you can only use SSH to control the system to do things but I may be misunderstood but I belive I have found these products which will act just like windows or similar but on a linux system, Correct me if i am wrong please.

I thank you all in advance for your help.

Kind Regards,

Carl Garside
Rack Networks, LLC
Managing Director

---

### Post by bodhi.zazen on 2006-09-10
> **RackNetz said:**
> Hello All.

I Just Found This Great Software Through A Freind Of Mine.

My Questions Is:

is this like linux but with a desktop feel so you don't need to use SSH to do stuff like make folder, delete, copy and paste and install apps?

My company uses linux systems to host the following:

- Game Servers E.G Call Of Duty, Counterstrike,Battlefield etc
- Webhosting, Using Webpanels Like Plesk,Cpanel,Xpanel,Layerd Panal
- Teamspeak Server Hosting (Veriety Of Ports Need To Be Open)
- Shoutcast Hosting (Veriety Of Ports Need To Be Open)

What product would you advise me to use to host these services on a linux system?

Do you need to have centOS or Debian installed to run the product you advice me on using?

Finaly last question : Does The product You Advise Me To Use Install These Softare Packages Aswell as the actual product:

- Apache
- PHP 4 or 5
- MySQL
- SSH
- FTP Server
- DNS Server
- Email Server

If you can answer these questions I would appriciate it. I am always willing to try new things out. The way I see it I am having to use linux for my servers. I have no linux experience what so ever and know not a single code. People say you can only use SSH to control the system to do things but I may be misunderstood but I belive I have found these products which will act just like windows or similar but on a linux system, Correct me if i am wrong please.

I thank you all in advance for your help.

Kind Regards,

Carl Garside
Rack Networks, LLC
Managing Director

In my opinion:

1. Versions of Linux: I would stay with Centos, Debian, or possibly FreeBSD.

2. Since you are talking about a production server and you have no Linux experience it will take you some time to migrate. I would bring a Centos server on line, and add 1 service at a time starting with the easiest and working to the most complex. Keep you current server as a backup. Easiest = Start with a project you are al least familiar with (Apache or mail server) and work to the unfamiliar.

Before I did that I would use any version of Linux as a primary desktop OS to get familiar with what you are getting into.

3. Obviously this is an ambitious project if you have no Linux experience.

4. Install the base system (server install) and add only what software you need. If you do not know what you need you have a lot of reading ahead of you. Linux/BSD server installs typically do not have a GUI. You can of course add one but most in the industry would advise against a gui on the type of server we are discussing here.

---

### Post by RackNetz on 2006-09-10
All of my questions were in relation to ubuntu server / ubuntu desktop (No idea of what the differenc is though)

My main concern is that I read that ubuntu server had a GUI (Like a desktop) and that it installed these apps for you as default:

- Apache
- PHP 4 or 5
- MySQL
- SSH
- FTP Server
- DNS Server
- Email Server

was just seing if this was true.

P.S downloaded the ubuntu iso and booted from cd. thought it was very nice, confusing but easy to adpt from the outlook. however the system kept crashing for some rason could have been the cd or cd player highly doubt as both a brand new lol i have a 3.2 processor and 2 gig ram so i have no idea why it crashed. all i was doing was typing an address google.com in the browser.

Anyway could you please answer the main  question above?

---

### Post by bodhi.zazen on 2006-09-10
An ubuntu server install is not the same as the desktop live CD or desktop install.

Afer a server install there will be no GUI and minimal applications.

I think there is an option to install LAMP. Be prepaired to install most of the above software for yourself.


Guides:
[The Perfect Setup](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
[Ubuntu How-to server install](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

