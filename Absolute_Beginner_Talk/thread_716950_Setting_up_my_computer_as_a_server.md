---
title: "Setting up my computer as a server"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by elpichi on 2008-03-06
Alright i'm planning to set up my computer as a Server for a small website with a forum dedicated for an Online Multiplayer Game that i will be hosting in the same computer. 
This is probably going to be my biggest project ever done, but i like the thrill of learn/use.

And i'm having various questions:
1. Would it make a noticable difference in performance if i change my ubuntu system, to the server edition?
Considering i'm only going to be using my computer as server, until i get some popularity, if i get any, then i'm probably switching to a dedicated server.

2. Will there be any problems with the IP provided by my ISP and trying to maintain the website online with my domain name?

3. If the answer for the 2 previous questions are positive... does anyone have a good tutorial for learning to use php with mysql for my website, since i may have to display/edit/delete some info from the database of the game(mysql) with the website interface?
I'm expecting to have mysql as a big dependable Database for this project.

I have tested apache/php/mysql/webadmin, and the game server all running in my computer smoothly, even though i only have 1gb in ram =], what worries me the most is the domain name and my IP which has a tendency of being dynamic whenever my ISP decides to cut off my internet for maintenance.

---

### Post by Cypher on 2008-03-06
If you convert your Desktop Ubnutu to a Server edition, the biggest difference is that you're going to lose the desktop and you really do want to disable that for a "Server" anyway. Apart from that, if you're current system is working properly, there's no real need to switch to the Server edition, just disable GDM/KDM and you should be good.

If you were to use something like DynDNS or No-IP to make your DHCP IP to a domain name, there are tools that both of those provide to ensure that a new DHCP IP from your ISP will get sent over to their DNS servers to keep your domain working.

The only issue you have to deal with here is your ISP shutting you down if you end up using too much bandwidth. Virtually all ISP's don't want customers running webservers on the network, and if the site is a low trafic one, it'll be ignored, but the traffic spikes, then you're  going to have to deal with your ISP..

---

### Post by Nevon on 2008-03-06
I'd recommend that you contact your ISP and simply ask them if they allow for home servers. My ISP is great. They allow non-commercial servers, which is all I need.

---

### Post by justin whitaker on 2008-03-06
> **elpichi said:**
> Alright i'm planning to set up my computer as a Server for a small website with a forum dedicated for an Online Multiplayer Game that i will be hosting in the same computer. 
This is probably going to be my biggest project ever done, but i like the thrill of learn/use.

Congrats! Always fun to have projects! 

> 1. Would it make a noticable difference in performance if i change my ubuntu system, to the server edition?
Considering i'm only going to be using my computer as server, until i get some popularity, if i get any, then i'm probably switching to a dedicated server.

No, not really. The core performance issue is going to be whether you run a GUI or not all the time. The underlying platform is not all that different. Just turn off GDM and X and you will see quite a performance increase! 

> 2. Will there be any problems with the IP provided by my ISP and trying to maintain the website online with my domain name?

Depends on the ISP. Some are cool supporting home servers, others want to upsell you to a business or home office package. Find out from your ISP first, before they shut off your service. :)

> 3. If the answer for the 2 previous questions are positive... does anyone have a good tutorial for learning to use php with mysql for my website, since i may have to display/edit/delete some info from the database of the game(mysql) with the website interface?
I'm expecting to have mysql as a big dependable Database for this project.

I'll dig around and see what I can find. I have about 1700 links on del.ici.ous...I'm sure I bookmarked a good tutorial site at some point. :)

> I have tested apache/php/mysql/webadmin, and the game server all running in my computer smoothly, even though i only have 1gb in ram =], what worries me the most is the domain name and my IP which has a tendency of being dynamic whenever my ISP decides to cut off my internet for maintenance.

You are going to need a static IP address if that is the case.

---

### Post by Woody AZ on 2008-03-06
Hi elpichi,

Sounds like you have quite the project coming up.  Here's my two cents:

1.  I believe you'll have better manageability by using the server edition of Ubuntu.  I currently have a development server configured, and it works great.  You should, howerver, be very comfortable with using Linux via the command line before going this route.  I suppose you could always install X, but that's for another post. :)

2.  ISP's can be tricky when it comes to hosting a server from your home.  You'll want to check your providers Terms of Service before setting up anything that could be bandwidth intensive.  I know for a fact that most cable ISP's frown on that sort of thing!  If all is well, but you have a dynamic IP address, you may want to look into something like[ dynamic dns]("http://en.wikipedia.org/wiki/Dynamic_DNS").

3.  As far as tutorials go,  I'm a big fan of [W3CSchools Online]("http://www.w3schools.com/").  They have a ton of web development tutorials.  Don't forget to check out the genera[l php documentation]("http://www.php.net/docs.php") as well.  And when you're in a pinch, there's always google. :)

I hope this helps you out a bit.  Be sure to keep us posted on your project.  I for one enjoy a good game.  Thanks for using Ubuntu!

---

### Post by elpichi on 2008-03-06
Whoa, Thanks a bunch for all the replies I think they all answered my doubts.

Seems like my safest bet for now is turning off my GUI, 
And yes i can live with a terminal 

Once as i get the green light with my ISP, I can get started with php and mysql and start building the website. And with the replies i just got i'm pretty sure i can take care of the IP in a fly ;-). 

I'm probably going to make another post later on with progress of my project and with a link for anyone that wants to test my game server :smile:

Alot of work ahead so i should get started :grin:

---

