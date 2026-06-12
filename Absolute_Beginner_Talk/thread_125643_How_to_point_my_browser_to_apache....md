---
title: "How to point my browser to apache...?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by procogo on 2006-02-04
Hi:

(Total Linux newbie....)

I have have a small network running Windows Small Business Server 2003.  I have set up a linux box and installed Apache, and plugged it into the network router.

Now I want to be able to access Apache from one of my windows workstations for testing.

**My Question:**  How do I view my test web-sites on apache from my Windows workstation?  Do I have to do something with Samba?


Note:  The apache server is ONLY for internal testing, it will never be live to the internet.

Many Thanks,

Dale

---

### Post by Breaks on 2006-02-04
Have you tried just typing the IP of the machine with the website + apache on it within your browser on the windows machines? All i had to do when having apache run on one of my machines was just to type the computers network IP into my browser on another to view the website it was hosting.

---

### Post by procogo on 2006-02-04
Hi,

Yes, (I think) I tried that.  What's the best way to find the ip of the linix machine?  (Remember, totaly newbie here!)

Thanks

Dale

---

### Post by moephan on 2006-02-04
If I understand you correctly, you would like to serve web pages from your Ubuntu machine to browsers running on Win XP machines, and all the computers are all in the same local area network. If that's correct, then

1. install samba ([http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)) 
2. edit the smb.conf file so that it is in the same workgroup as the Win XP  ([http://ubuntuguide.org/#changecomputerdomainworkgroup](http://ubuntuguide.org/#changecomputerdomainworkgroup))
3. that's it! now you can just type: http;//yourubunutucomputername in a web browser in any computer in the same workgroup, and apache will work.

Cheers, Rick

---

### Post by moephan on 2006-02-04
Typing in the IP address should also work fine. Open a terminal on your ubuntu machine and type in "ifconfig". That will tell you the ip address.

Cheers, Rick

---

### Post by procogo on 2006-02-04
Thanks Rick:

That sounds like it should do the trick.  btw, my network is using a domain instead of a workgroup, will it still work? (haven't had a chance to read samba docs yet)

Dale

---

### Post by Breaks on 2006-02-04
If your behind a router (which im guessing you are because you have a network), then surely your router automatically assigns IP addresses to connected machines. But yeah just run that command in the terminal and it should tell you the IP of the machine :).

**:: Edit ::**

If you have apache running and configured correctly on the Linux machine then all you should be required to do on the windows rigs is basically just type the IP address of the linux machine in the windows machines browser to display it. Thats all i had to do with my network of linux & windows machines. If its just for your network internally and not anything else then that samba things a bit long winded isnt it?.

---

### Post by moephan on 2006-02-04
Dale,

Yes, Samba will let you Ubuntu machine join the domain. However, as Breaks points out, if all you really want to do is look at the web pages on the Ubuntu machine and you don't mind that your users have to type in the ip address instead of the computer name, then samba is overkill. 

If you do set up and configure samba to be in the same domain you will be able to see the Ubuntu machine in the Network Places, and essentially have your Ubuntu machine be a fill fledged member of your domain. However, it does take some configuration and work, so if you don't need those features, I agree with Breaks that it's probably not worth the hassle.

Cheers, Rick

---

### Post by procogo on 2006-02-04
Thanks for all the help.  I've got a pretty good idea of what to do now.

Dale

---

### Post by Breaks on 2006-02-04
So did you manage to get this working to how you wanted it to? :)

---

### Post by procogo on 2006-02-04
Thanks for following up!

Unfortunately, my wife pulled me off my computer to strip wallpaper.  I hope to get back to it later tonight.  My main goal is to simply learn php, and test php utilities before using them on my clients live web-site.....  I know I could set up a test server in Windows, but I thought this would be a good time to get my feet wet with Linux (and loving it so far!)

Dale

---

### Post by Terry of Astoria on 2006-02-04
I did that! I set up PHP and MYSQL and made a ubuntu server on my home net. I installed textpattern and got it working. Wow! took like two days but I did it! So fun to learn and do! I wish you luck!! 
   I ended up installing textpattern over at my shared server on textdrive and am using it for my web site [astoria.doesntexist.com]("http://astoria.doesntexist.com") - My homemade server is going to be an intranet server at my business in town. I installed webcalendar on it and plan to use the forum and the calendar for keeping track of stuff like employee schedules and stuff.
   As you probably know, the first secret to how to do this stuff is "don't give up!"
Aloha

---

### Post by Breaks on 2006-02-04
[QUOTE=procogo]Thanks for following up!

Unfortunately, my wife pulled me off my computer to strip wallpaper.  I hope to get back to it later tonight.  My main goal is to simply learn php, and test php utilities before using them on my clients live web-site.....  I know I could set up a test server in Windows, but I thought this would be a good time to get my feet wet with Linux (and loving it so far!)

Dale[/QUOTE]

Im guessing you do know that php has to be installed seperately to apache? Just double checking :). And i hope all goes well with the install!

---

