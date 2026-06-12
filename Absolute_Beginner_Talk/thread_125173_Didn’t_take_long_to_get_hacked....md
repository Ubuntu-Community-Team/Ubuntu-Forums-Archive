---
title: "Didn’t take long to get hacked..."
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by inkpassion on 2006-02-03
I decided to explore the Linux option again and I have been very impressed with ubuntu and this community. Ive now have a dedicated computer to running ubuntu and with luck move away from Windows. Anyways after about 2 days of having my box online it was owned via SSH (that’s what I guess from looking at the router logs) and being impatient I cleared the box and started over, this time installing ubuntu and not ubuntu-server . 

I was looking at some possible ways why could have gotten in and how I can prevent this from happening again. I was excited and went a little package happy so I know that didn’t help but this is what I had setup security wise: box behind router, firestarter was enabled with ports open for VNC(5900), www (81), SSH(22) on both. I also used a 7 character password that was random numbers/letters so I doubt they brute forced my password. I know I was stupid and followed an online doc and made my primary user admin.  

If there is any tips you all could give to help me secure my box so I can run it 24x7 with a clear conscious I would greatly appreciate it.

---

### Post by krusbjorn on 2006-02-03
Check this one out, works great for me: [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

Also, change your ssh port to something else. Since i changed mine from 22 to 9921 i hardly get any incoming connections from bots or script kiddies at all ;)

---

### Post by Mustard on 2006-02-03
Did you have a root password setup, or was it disabled?

Is it possible that this was an 'inside job'? I guess thats a tricky question to answer, but you never know. :)

---

### Post by inkpassion on 2006-02-03
[QUOTE=krusbjorn]Check this one out, works great for me: [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/)

Also, change your ssh port to something else. Since i changed mine from 22 to 9921 i hardly get any incoming connections from bots or script kiddies at all ;)[/QUOTE]

Wow that is awesome! I will install this when I get home before installing SSH again. Changing the SSH port... DUH...I will mark this mistake off as being excited ;)

I see there is a debian package, can I just install that or so I need to set this up manually?

---

### Post by inkpassion on 2006-02-03
[QUOTE=Mustard]Did you have a root password setup, or was it disabled?

Is it possible that this was an 'inside job'? I guess thats a tricky question to answer, but you never know. :)[/QUOTE]

I believe the root password was setup since every time I sudo it prompted me (I could be wrong). The chance of this being an inside job is slim to none since it’s a small home network. Wifi was enabled and I did scan the network real quick and didn’t see anybody who normally isn’t on.

---

### Post by krusbjorn on 2006-02-03
[quote=inkpassion]Wow that is awesome! I will install this when I get home before installing SSH again. Changing the SSH port... DUH...I will mark this mistake off as being excited ;)

I see there is a debian package, can I just install that or so I need to set this up manually?[/quote] 
I think I had to convert one of the rpm's to get it working. Anyways, i still have the deb i used, if you want to you can grab it here: [http://embla.krokodil.se/misc/denyhosts_1.1.4-1_all.deb]("http://embla.krokodil.se/misc/denyhosts_1.1.4-1_all.deb")

I'll leave it there until you reply.

Edit: Btw, the password you enter when you use "sudo" is your user's password, not the root's. By default there is no root password in Ubuntu.

---

### Post by inkpassion on 2006-02-03
well cripes. I will make sure to set a root password now...

I downloaded it and e-mailed it to myself. Thanks!

---

### Post by Mustard on 2006-02-03
[QUOTE=inkpassion]well cripes. I will make sure to set a root password now...

I downloaded it and e-mailed it to myself. Thanks![/QUOTE]

Setting a root password is what you want to avoid actually, as every linux install has a known user account called 'root'.  By disabling the password for root, its not possible to log in via root, as no password will match.

---

### Post by inkpassion on 2006-02-03
[QUOTE=Mustard]Setting a root password is what you want to avoid actually, as every linux install has a known user account called 'root'.  By disabling the password for root, its not possible to log in via root, as no password will match.[/QUOTE]

Oh boy this is going to be a fun transition... :p

---

### Post by steve.horsley on 2006-02-03
[QUOTE=Mustard]Setting a root password is what you want to avoid actually, as every linux install has a known user account called 'root'.  By disabling the password for root, its not possible to log in via root, as no password will match.[/QUOTE]

Well, it's not hard to configure sshd to disallow root login. To my horror, the default setting in Breezy is to allow it. 
/etc/ssh/sshd_config : PermitRootLogin yes/no

---

### Post by az on 2006-02-03
[QUOTE=steve.horsley]Well, it's not hard to configure sshd to disallow root login. To my horror, the default setting in Breezy is to allow it. 
/etc/ssh/sshd_config : PermitRootLogin yes/no[/QUOTE]
It is assumed that if you install the ssh package, you know what you are doing.

---

### Post by Iowan on 2006-02-03
There's that ***-u-me word...

---

### Post by bscbrit on 2006-02-03
You mentioned that your wifi network was active.  Is it secured?  (WEP? WPA?) If not, then it is possible that someone got your password that way. You might be transmitting your password for all to see/hear. What kind of environment is it where you are?  Residential neighbourhood, block of flats, student dorm?  Basically, are you surrounded by the sort of people that might have enough knownledge to break in to your network using a local wifi connection?  SSH itself is usually quite robust but the weak link is the password.  How many people 'are normally on' your network - and how well do you trust them?

---

### Post by inkpassion on 2006-02-03
[QUOTE=bscbrit]You mentioned that your wifi network was active.  Is it secured?  (WEP? WPA?) If not, then it is possible that someone got your password that way. You might be transmitting your password for all to see/hear. What kind of environment is it where you are?  Residential neighbourhood, block of flats, student dorm?  Basically, are you surrounded by the sort of people that might have enough knownledge to break in to your network using a local wifi connection?  SSH itself is usually quite robust but the weak link is the password.  How many people 'are normally on' your network - and how well do you trust them?[/QUOTE]

My computers are all hardwired and there is 3 laptops that are wifi. Its secure with wep in a residential/country area and I doubt somebody has the knowledge where I live, the cows might though. On my router I check my incoming connections and I had 2 coming into port 22. I closed the port and started packet sniffing and all was calm so I am almost positive (never can be 100%) the attack was not local.

---

### Post by erick_p on 2006-02-03
This is bothersome. I do want to use Ubuntu to set up a WAN network, with my Ubuntu being the server -- FTP, SSH, Apache, MySQL and Postgresql. 

After installing the above, is there a list of "Best Practices" for security that I can follow?

Thanks

---

### Post by bscbrit on 2006-02-03
Inkpassion.  I agree it looks like they came down the wires at you - I haven't yet met cows with the necessary skills to do this sort of thing but you never can tell.....

I can see some value in changing the SSH port number but, to be honest, any decent scan will show which ports are open so it will not prevent a serious attempt to get into your network.  I suppose it will prevent most, if not all, of the bots that are not clever enough to look at other ports.  And if they came down the wires then they probably cracked your password - 7 random letters and numbers doesn't appear to have worked in this instance.  You could always use, say, a 32 character password.  Twenty four characters could be written on a post-it and stuck to the screen - nobody cracking from outside can see it!  The last 8 can be your favourite random string so that nobody local can get access even if they have the post-it to work from! (In fact, most people who gain physical access will simply try various combinations of the post-it and spend years trying to achieve the impossible.  And if they are that smart, they will simply reboot the computer in recovery mode and defeat all of your passwords in a matter of seconds. :-D )

Do you need to allow SSH from outside your network?  If not, then simply close access at your firewall.  It will not prevent network SSH access from inside but will give the opposition another barrier to deter them.  Similarly, are you actually serving http, ftp or whatever to all and sundry or is it really for internal network use?  After all, you have only got to make it more attractive for the cracker to look elsewhere rather than provide an inpenetrable barrier that would hold back GCHQ, NSA and the FSB!

---

### Post by bscbrit on 2006-02-03
erick_p.  Don't be put off - go for it!  If you set up a good firewall and limit the world's access to the essential ports only, then you have a good chance of never being cracked.  But you must never assume that you CANNOT be cracked.  So have a robust backup system in place, use it, test it and then sleep well at night.

---

