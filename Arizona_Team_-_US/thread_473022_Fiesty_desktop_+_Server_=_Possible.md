---
title: "Fiesty desktop + Server = Possible?"
date: 2007-06-13
forum: Arizona Team - US
---

### Post by pacman2440 on 2007-06-13
hey guys, this is jacob2440 from the IRC chats.

I posted this under the server section of the whole communuty but thought I would throw it in here. I don't have access to an IRC chat client while I am at work.

I have fiesty on my laptop, and I have just finished working on a website. I have a couple buddies that are working on the project with me, and want to view it and make changes to the site. I have a domain registered for the site, but I want to host it myself. I have a machine that will eventually be the main server for the site, but its being repaired right now (too many projects, GAH!).

Is there any way I can use something on my lap top that will allow the site to be hosted, I know that windows has one, but I dont have a machine with windows on it (thank god). I wasn't sure if Mysql is what I need to just host the site, or do I need more. And can it be run on linux? 

I will ask about this again later tonight on the IRC chat, but thought I would ask here too.

Thanks.

---

### Post by frolle on 2007-06-13
Apache, mySQL, PHP5 and you are up and running :)

---

### Post by derekr44 on 2007-06-13
LAMP (stated above)

Is your personal connection giving you a dynamic or static IP?  That's your tricky part.

---

### Post by pacman2440 on 2007-06-13
Its through Cox, I am 99% sure that it is static (non-changing)

Sweet I had a LAMP on an old box, and I didnt know that you could do that with linux desktop version.

---

### Post by DX 00 on 2007-06-14
Here is a link on how to install a LAMP server with Ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ubuntu_Feisty_LAMP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ubuntu_Feisty_LAMP_Server)

Here is how to install Apache:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)

For PHP:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP5](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP5)

For MySQL:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_for_Apache_HTTP_Server)

---

### Post by botulismo on 2007-07-16
Hey, it's martyd215 from IRC. I did the exact same thing with my cox connection (previously, it's now comcast as  Imoved) and it sucked. I know your plan decides whether you get a static IP or dynamic IP (having to do with businesses) but if you do have a dynamic IP, then take a gander at [http://www.zoneedit.com/](http://www.zoneedit.com/). I have  a python script that I use as one of my startup scripts that will update my IP with them during the occasional reboot. 

Anyway. Just throwing in my two cents.

---

### Post by derekr44 on 2007-07-16
If you're willing to shell in a few bucks, check to see if Speakeasy is available in your area.  They've got static IPs and great connections.

---

### Post by mesapiegrande on 2007-08-13
You may also want to be wary of the user agreement you sign with COX.  Depending on the contract/agreement you may not be legally allowed to host the site yourself over that connection.

I'm not saying you can't do it I am just saying that you could run into trouble should they find out.

Just letting you know.

---

