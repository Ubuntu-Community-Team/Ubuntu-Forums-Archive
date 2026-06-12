---
title: "Convince me to use Ubuntu as a Webserver"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by localfiend on 2008-04-18
Here's the thing.  I'm looking to build a website for my local church as well as upgrading a business website at work.  I want to do this all myself, to gain experience, and because life has taught me not to trust other humans. ;)

I am going to start completely from scratch - meaning I'll build a server and run everything from my house on a DSL connection.  I am quite competent when it comes to doing such things, however I have almost zero experience running operating systems other than windows, and have done very little HTML.

The current business website I'm running has been cobbled together using XP Pro, IIS 5.1, and an old version of frontpage. (Hey, it was the best I had at the time).

Ok, now that the background info is taken care of here's a few questions:


1.  Is it a good idea for newbie to doing all of this on an unfamiliar operating system?  I would really like to save money and go with this route - but I have limited amounts of time to learn a whole new operating system.  Is a Windows Server OS of some kind perhaps a better choice?
2.  If I go with ubuntu what would be the best program out there to actually design my website with. (I know that hand coding is probably best, but keep in mind that I have very little experience with HTML, PHP, CSS or any of that)
3.  Would it be best to try and design the website on the actual server (linux), or use a different PC (My x64 Vista Ultimate system is the most likely candidate)
4.  I would like to set up streaming video & audio, use flash, and perhaps add email and forum functionality.  Can a beginner figure out this stuff in linux without hours, and hours of hair pulling?  I have already done enough hair pulling with windows operating systems and don't know if I want to go through the process again.

I've got lots more questions of course, but the above seem to be the big ones.  

Thanks

---

### Post by HermanAB on 2008-04-18
Well, Ubuntu is a DESKTOP system.  The server version is rather limited still.  If you want to run a server with minimum hassle and wish to configure things the point-and-click way, then you will do better with Suse or Mandriva.  Mandriva has wizards for everything - Ubuntu doesn't yet.

That being said, Windows Server 2003 ain't bad, but it is expensive and no easier to manage than Mandriva, since a mouse only has so many buttons...

Cheers,

Herman

---

### Post by hyper_ch on 2008-04-18
> **localfiend said:**
> 1.  Is it a good idea for newbie to doing all of this on an unfamiliar operating system?  I would really like to save money and go with this route - but I have limited amounts of time to learn a whole new operating system.  Is a Windows Server OS of some kind perhaps a better choice?
There are howtos that give you an excellent setup. I prefer the perfect Howtos over at [http://www.howtoforge.com](http://www.howtoforge.com) ( [http://www.howtoforge.com/perfect_setup_debian_etch](http://www.howtoforge.com/perfect_setup_debian_etch) and [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10) ). I would however prefer debian as server...
By following those howtos you don't need to learn everything by heart, you will be up and running in quite a short time - however it is mandatory that you will keep informing and education yourself on that topic ;)

> **localfiend said:**
> 
2.  If I go with ubuntu what would be the best program out there to actually design my website with. (I know that hand coding is probably best, but keep in mind that I have very little experience with HTML, PHP, CSS or any of that)
Well, for a server it does not matter what you created the stuff with. You can use a linux server but create your site in Windows with whatever tools you want. Then you ftp or ssh or scp into the server and load the stuff on it. So, the client doesn't required to be a Linux one.
However, for designing I guess it's Kompozer... that's also a WYSIWYG editor (I think). But when you want to do PHP you will need a text editor. There are many very capable ones available.


> **localfiend said:**
> 3.  Would it be best to try and design the website on the actual server (linux), or use a different PC (My x64 Vista Ultimate system is the most likely candidate)
Well, if you want an advanced website with dynamic content then you will use a php/mysql setup. For that you then need to create/alter a theme... it doesn't matter where you do that. In the end you will upload the theme files and select it from the admin interface of that CMS that you use.


> **localfiend said:**
> 4.  I would like to set up streaming video & audio, use flash, and perhaps add email and forum functionality.  Can a beginner figure out this stuff in linux without hours, and hours of hair pulling?  I have already done enough hair pulling with windows operating systems and don't know if I want to go through the process again.
Well, a forum is easy... you may want to combine a CMS and a forum... so you have also a unified look. But I have no clue with regard for streaming video.... I only setup a streaming music server so far. As said, the two howtos I posted above will setup a ISP-like setup. This means you get admin control panels and can manage "clients" who host their website...

But if you want to operate a mail server also, you will need a static IP address.

---

### Post by DrMega on 2008-04-18
1. Ubuntu is really intuitive, but the decision has to be yours. Have a look through the testimonials section of this forum. Most people seem happy (and I am), but some people have had issues. Try the LiveCD (if you haven't already).

2. There are several good ones, and it is a matter of opinion which is best. I like Kompozer, but there are many others in the repositories, and the best thing is they are free so you can just try several, and just uninstall the ones you don't like.

3. If you go for the server version of Ubuntu, there is no GUI by default, so you wouldn't be able to use the browsers that the masses would use. The desktop version of Ubuntu can very easily be configured as a server, so you get the best of both worlds (the only disadvantage of using the desktop version for a server is resource usage - obviously a GUI takes up memory and CPU time that might be better spent on being a server. This decision is taken away from you if you use Windows, as there is always a GUI and tonnes of memory wasted).

4. Can't comment about streaming media. I know it can be done but I've never had need to try so I don't know what's involved there. Same with email. The forum can be done though, when configuring your server just make sure you install PHP and MySQL. There are a number of open source forum apps that you can use to save you having to develop one.

Sorry my answers are a little vague, there's much more specific info floating about on this forum.

---

### Post by OffAxis on 2008-04-18
Regarding streaming video, you won't be able to do a convincing stream over a DSL connection.

Even at mpg4 compression, you're going to need more throughput than your connection can handle. For instance, you can try out skype or yahoo messenger with video chat, but skype recommends 384 for their feed, and it's at 320x240 at 15 frames per second. Okay for a face to face discussion with audio to fill in the gaps, but painful otherwise.

VLC media player has a server aspect built in. For manual setup and streaming of video or audio, it's probably the easiest.

---

### Post by localfiend on 2008-04-18
Thanks for all the replys guys - this gives me a bunch more information to go on.  I'll have to do some looking as it seems ubuntu might not be the best choice for a server as I would like to have the GUI.  Ubuntu was recommended to me by a friend, but it seems I may have better options out there.  Glad I decided to ask before doing anything.

---

### Post by hyper_ch on 2008-04-18
you don't want to operate a server with a gui

---

### Post by Oldsoldier2003 on 2008-04-18
> **localfiend said:**
> Thanks for all the replys guys - this gives me a bunch more information to go on.  I'll have to do some looking as it seems ubuntu might not be the best choice for a server as I would like to have the GUI.  Ubuntu was recommended to me by a friend, but it seems I may have better options out there.  Glad I decided to ask before doing anything.

If you are comfy with Ubuntu I'd go with Debian Etch. Ubuntu is close enough that you wont have too many problems.

---

### Post by HermanAB on 2008-04-18
BTW, as for administering a server with a GUI:
If you use SSH from another machine, then you don't need X11 on the server, since SSH and your local machine provides it.
If you run a 'desktop server' with a screen and keyboard, then switching the GUI on/off is as easy as 'sudo init 5' and 'sudo init 3'.

---

### Post by Danikar on 2008-04-18
If this is your first time putting up a website you should probably look into a shared hosting solution.

If you really want access to the operating system directly (i don't think you need it for what you are trying to do) I would suggest looking into a Virtual Private Server.

These solutions are going to be much faster than hosting your own machine, and the first choice will deal with DNS and a lot of the more technical stuff without you spending hours of hair pulling.

Some basic information:[ http://en.wikipedia.org/wiki/Shared_web_hosting_service]("http://en.wikipedia.org/wiki/Shared_web_hosting_service") 

Streaming video/audio is a tricky thing for a novice. But it is pretty OS independent. I am sure you could figure it out without too much hair pulling.

[http://www.mediacollege.com/video/streaming/overview.html]("http://www.mediacollege.com/video/streaming/overview.html")

Personally I would never host a website off a basic broadband connection unless it was just for fun and a personal site that only I am going to go to.

---

### Post by stchman on 2008-04-18
> **localfiend said:**
> Here's the thing.  I'm looking to build a website for my local church as well as upgrading a business website at work.  I want to do this all myself, to gain experience, and because life has taught me not to trust other humans. ;)

I am going to start completely from scratch - meaning I'll build a server and run everything from my house on a DSL connection.  I am quite competent when it comes to doing such things, however I have almost zero experience running operating systems other than windows, and have done very little HTML.

The current business website I'm running has been cobbled together using XP Pro, IIS 5.1, and an old version of frontpage. (Hey, it was the best I had at the time).

Ok, now that the background info is taken care of here's a few questions:


1.  Is it a good idea for newbie to doing all of this on an unfamiliar operating system?  I would really like to save money and go with this route - but I have limited amounts of time to learn a whole new operating system.  Is a Windows Server OS of some kind perhaps a better choice?
2.  If I go with ubuntu what would be the best program out there to actually design my website with. (I know that hand coding is probably best, but keep in mind that I have very little experience with HTML, PHP, CSS or any of that)
3.  Would it be best to try and design the website on the actual server (linux), or use a different PC (My x64 Vista Ultimate system is the most likely candidate)
4.  I would like to set up streaming video & audio, use flash, and perhaps add email and forum functionality.  Can a beginner figure out this stuff in linux without hours, and hours of hair pulling?  I have already done enough hair pulling with windows operating systems and don't know if I want to go through the process again.

I've got lots more questions of course, but the above seem to be the big ones.  

Thanks

If you want to use Windows as a webserver then you have 2 choices as XP IIS5.1 is 5 concurrent users.

Purchase Server 2003 with IIS6 or
Download Apache for Windows.

You can install Ubuntu and install Apache web server.

I am going to say that since you have little experience with HTML it is going to take a long time for you to get this up and running.

I have a website and I have a web hosting service for $60 a year.  THey give me email, and over 50GB capacity and 120GB/month bandwidth.

You figure you are going to spend more than that on electricity and possible hardware failures.  I recommend a web hosting service.  They will give you a DNS and their hardware won't fail like your as they have redundant systems.

A web hosting service will have far more bandwidth than you do as well.

---

