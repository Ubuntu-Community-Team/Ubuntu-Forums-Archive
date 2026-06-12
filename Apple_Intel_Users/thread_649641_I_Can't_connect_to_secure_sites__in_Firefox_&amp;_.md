---
title: "I Can't connect to secure sites ? in Firefox &amp; Opera"
date: 2007-12-25
forum: Apple Intel Users
---

### Post by Sonah on 2007-12-25
Hi 
 
i download new Ubuntu 7.10 from [www.ubuntu.com](www.ubuntu.com)
 
and i install and run it using [VirtualBox ]("http://www.virtualbox.org")under XP
 
in firefox i can visit http sites BUT not the Http**S** sites
 
I Can't go in hotmail Gmail Yahoo mail :(
 
So I Download OPERA web browser but i have the same problem in fireFox the Http works Fine But I Can't connect to secure sites ? :(
 
Please Help ..

---

### Post by Rog-Mahal on 2007-12-25
Do you get any errors? If so, what kind?  have you tried playing around with your settings under Edit>Preferences? Let's try and narrow this down. I assume you don't have this problem using other OSes.

---

### Post by Sonah on 2007-12-26
[SIZE="2"]also i have the same problem in Opera 

here is a snapshots  for the Firefox

Http sites works  OK
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54266&stc=1&d=1198684495[/IMG]


can't connect to Gmail :( its** HTTP[COLOR="Red"]S[/COLOR]** site
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54267&stc=1&d=1198684495[/IMG]


Firefox  settings  
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54268&stc=1&d=1198684495[/IMG]


can't login to my hotmail account :(
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54269&stc=1&d=1198684769[/IMG][/SIZE]

[SIZE="4"]**[COLOR="Red"]PS:[/COLOR]** I run Ubuntu in  "Virtual Box"  under XP  and the firewall in XP is **Disable**[/SIZE]

---

### Post by Samhain13 on 2007-12-26
Have you tried "Select one automatically" in Preferences>Advanced>Encryption?
Or is that a bad idea?

---

### Post by Sonah on 2007-12-26
Yes  i made  "Select one automatically"  nothing change :(

---

### Post by Rog-Mahal on 2007-12-26
Hmmm...do you use a proxy server? If so, you may want to go to Preferences->Advanced->Network and check that you have it enabled for all protocols.

You also may want to google this problem, it doesn't seem to be uncommon.

---

### Post by Sonah on 2007-12-27
no i did't  add  any proxy server  
i know that if i add proxy  the secure sites will now work i know this ..


here is a some one have same my problem but i don't  know How  he solved it ?
he Updated NSS ?  what is the NSS  :confused:

[http://www.linuxquestions.org/questions/linux-software-2/cannot-connect-to-secure-sites-after-update-to-firefox-1.5.0.7-484079/](http://www.linuxquestions.org/questions/linux-software-2/cannot-connect-to-secure-sites-after-update-to-firefox-1.5.0.7-484079/)

---

### Post by Lord DarkPat on 2007-12-27
Have you set-up WINS with samba? Because the same thing used to happen to me only diff is that even http was gone. Now it healed after I uninstalled samba. I never got to the root of the prblm, though

---

### Post by Sonah on 2007-12-27
[B]Hey! Lord DarkPat

you are from Kuwait me to from Kuwait!!  :)

I did't install samba or wins .. 

I think the proplem is in [_VirtualBox _]("http://www.virtualbox.org/")

I will try [_Virtual PC 2007 _]("http://www.microsoft.com/windows/products/winfamily/virtualpc/overview.mspx")to run Ubuntu on it  or [_VMware Player_]("http://www.vmware.com/products/player/")    :confused:[/B]

---

### Post by jeffspen on 2008-01-01
Did anyone fix this? i am having big problems here with teh exact same issue. I'm running a purely Ubuntu 7.10 system no XP anywhere near it. Direct connection to my router (no proxy stuff)

I have also disabled IPv6 systemwide and in Firefox itself.

Any clues????

---

### Post by jeffspen on 2008-01-02
My situation is solved -  i have discovered the factory settings on my new router were wrong and the cause of my problem. Ubuntu is as blameless as I wanted it to be! Thanks anyway,

---

### Post by IwarV on 2008-05-07
It's good to hear that I am not the only one having problems with secure connections in Ubuntu, but it very disheartening that everyone bar me seems to find the solution to their problem.

I need to power cycle my router (Netgear RP614v3) at least twice a day when either Firefox or Thunderbird fail to make a secure connection.

The blame definitely rests with Ubuntu, because the other PC connected to said router is an XP box and that can make secure connections even when my Ubuntu box fails.

I have tried disabling IPv6 but to no avail.
This is driving me nuts.

But what is worse; I am sure the wife will not put up with it much longer and will demand we switch back to using XP on both boxes. I like Ubuntu, but I cannot defend this behaviour really.

I desperately need this sorting out.
Anyone here got any other things to try out?

---

### Post by JoeDesertrat on 2008-05-12
I had the same issue which really irritated/perplexed me until just a few minutes ago. My solution, which may not work for everyone, was to uninstall Firestarter which I never got working right anyway. I restarted and the secure sites worked. 
I should have figured this out sooner as I'm fortunate enough to be "beta testing" Ubuntu at work and that was really the only significant difference between the two setups and the secure sites work fine there.
I have seen another forum where someone got it working by disabling another "security" program but as I did not have it installed I disregarded the post. So if you don't have Firestarter installed think about what other programs you installed that might affect browsing.
Hope this helps!

---

### Post by IwarV on 2008-05-13
Things seem to have improved for me. I had only disabled IPv6 an hour or so before I submitted my last post and at first things seemed just as they were before. But in the following days things got a lot better.
Now I am going for days sometimes before I need to power cycle the router.

Weird eh?

---

