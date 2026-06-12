---
title: "an idea I had"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-12
I was daydreaming about getting my linux and winxp pc to play together today and of course, Samba came to mind. Having used SWAT in the past, this didn't really bring a smile to my face.  However, I would like to try my hand at PHP and Apache. If I set up an Apache web server on a linux machine on my LAN, I should be able to assign that machine a static IP through my router and set up a place where I can transfer files from my winxp to my linux and vice versa, right? Is this harder than it sounds? Either way, Apache seems like a useful skill to learn.

---

### Post by UnknownVariable on 2006-10-12
Apache is a webserver, not a skill. :lol: Apache basically puts your files "on the internet" while keeping them on your computer. It serves them. Of course, only other computers that can connect to the computer with apache will be able to see them, and they'll have to connect to your IP address.

Try doing a crossover cat5 connection without Samba or any other programs first. My two computers are able to communicate perfectly between each other, transfer files, see each other's apache install, etc.

As a matter of fact, try it with a normal cat5 wire before a crossover. For some reason, mine works perfectly, and here I was under the impression a crossover was always needed for direct PC connections.

---

### Post by saintj0n on 2006-10-12
I don't see how a normal cat5 cable would work. Each end of the cable would have exactly the same pinout, therefore the in would connect to the in and the out would connect to the out. However, I do have a router. I should be able to see each pc but windows uses smb and linux uses something else... However, tcp/ip is universal so, the web server idea should work somehow. I can't serve files over the internet because I don't have a static IP but it should work locally.

---

### Post by saintj0n on 2006-10-19
Actually, I think setting up a web server and maintaining it could be a skill. At the very least, it is an experience worth trying. I only wish I had a static IP or some way to put one up on the web. I can't even figure out how to get my 2 xubuntu pc's to see each other on my home network. I'm thinking NFS, it will just take some research for me to learn how it works. Hmmm...wonder of there is a complete idiot's guide to NFS.....8)

---

### Post by Foudre on 2006-10-19
easily it will work, i can tell you how, on your windows setup a folder with filesharing on. Now from linux on the other computer on the same network (crap i can't rember where, but something that says networking i think) lets you broswe your network for computers, connect to your computer with xp and file sharing on, and ta da, to get files from either computer to the other one just dump them in the folder that has sharing on, when you are done you can just turn sharing off. Not as easy to use as an ftp, but easier to set up. 


_________
I'm a lazy man, i find the easy solutions, if something takes more then 30 minutes to do, you've done something wrong...

---

### Post by Foudre on 2006-10-19
oh and to put it up on the web you would have to allow your router to let it out, then if you wnat to access it by other then ip address still you'll have to register a dns for it (not sure if there is a better way i hope there is) to access the router type [http://168.192.0.0](http://168.192.0.0)   crap i think thats the right addrsss why can't i remeber it. anyways  it may be 198.162 or i may be wrong. lol i know that the main router on a network always has the same ip so ya, then assumeing you router or maybe a modem is designed to allow http access it'll bring up a web pag, ask for a pass word then have some setting you can change, if you have a router behind like a cable modem you may have to allow the samething twice once in both of them

---

### Post by saintj0n on 2006-10-19
My router is set up with the standard default settings 192.168.0.1, subnet mask 255.255.255.0.... It would be cool if I could find a cheapo webserver site where I could plug directly in. I could have a site with godaddy.com but I wouldn't be able to run an apache web server on that. Really all I want for now is to see my 2 linux pc's playing nice on the network. The apache stuff will come later, when I get some bux...:rolleyes:

---

### Post by thornomad on 2006-10-19
you can go to dyndns.org and register a free domain name that points to your external ip address (check: whatismyip.com).  I have [setup a linux server]("http://www.damontimm.com/blog/how-to-install-a-lamp-server-linux-apache-mysql-php-on-older-laptop-with-ubuntu/") this way.

---

### Post by saintj0n on 2006-10-19
This works even after DHCP renews the lease? How does that work..?:confused:

---

### Post by thornomad on 2006-10-19
I am not sure what is available for Linux (that is, I don't know the link -- I know it is out there) but you can get software (or maybe in your router) that will automatically "ping" the dyndns.org service when your DHCP renews ... so, you don't have any disconnects.  Renewed DHCP, automatically changes in the registry.  Wa la!

---

### Post by yellowband on 2006-10-19
what gave you problems with SAMBA?  At first i felt the same way, but once i learned some more about file permissions (setting them recursively) and the samba.conf file, i have gotten my server working nicely with windows.  I think samba would suit your needs better if you got it working, but learning how to use apache may be a good lesson as well.

---

### Post by saintj0n on 2006-10-19
smbd isn't starting up...[http://localhost:901](http://localhost:901) just returns an error page...I don't even know if it is set up. I always thought there was a way to launch SWAT from the command line..?:confused:

---

