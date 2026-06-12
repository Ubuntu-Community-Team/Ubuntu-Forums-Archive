---
title: "Slow Web Connection"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ngreene on 2007-03-21
I've been searching on this one and it seems to be a common problem.  I think I may be seeing some different results.  I have loaded both 6.06 and 6.10.  I have also disabled ipv6.  Also have tried two different NIC cards.  None of this has seemed to resolve the problem.  It appears that Ubuntu has a problem with network speed.  The interesting part is that some pages display very quickly.  If I go to Google the connection is instant.  If I go to Ubuntu.com the page will never load.  I even logged onto my exchange web access.  I did this using the IP address and the URL.  Both times the page failed to load completely.

When i go Add Remove I'm told that the list is outdated.  I tell the computer to update and half of the downloads fail.  

I even try to load easybuntu and after entering the commands in terminal I get to the point where the computer appears to be downloading the file and it seems to go into a stall.  I'm stuck at 1% on the download.

There are obvious problems but I don't even know where to start.  Any ideas.

I have checked DNS and the settings are the same as the other XP desktops in my office that work fine.  

I have a T1 coming into the network with a netscreen firewall feeding a 3Com and Dell switch.

Ubuntu is installed on a Dell Diminesion 8100

Thanks in advance for any help!!

---

### Post by oilchangeguy on 2007-03-21
ubuntu seems to have issues with it's own web pages. i've seen problems mainly in this forum. check your connection speed at [www.speakeasy.net](www.speakeasy.net).

---

### Post by ngreene on 2007-03-21
Trying that now.  One of the problems is that I don't have Macromedia loaded and it takes forever to load from the other pages.  

I did run the speed test from the XP machine I'm on now.  The pipe is delivering

1419 down
1439 up

If I can get macromedia on the Ubuntu machine I'll provide those results.

Ubuntu is runing off the same settings that the Xp machine is

THanks

---

### Post by halitech on 2007-03-21
go into the about:config and check for 

network.http.pipelining.maxrequests

and set it to 32 then restart firefox. I'm guessing that you are using firefox, if not, let us know what browser for usre.

---

### Post by ngreene on 2007-03-21
Yes using firefox.  Just tried your suggestion.  It loads the Speakeasy page quickly but when I go to adobe to download flash it appears to hit a brick wall.  Then I get a quick view of the begining of the page.  The Firefox quickly resets the connection!

Thanks again for everyone's help!!

---

### Post by ngreene on 2007-03-22
I don't know if this helps anyone but I moved the Ubuntu box into the DMZ on my network and everything took off working fine.  Does anyone know what ports could be blocked that are needed by Linux that Windows doesn't need??

---

### Post by cowlip on 2007-03-22
Have you tried this? [http://www.digg.com/linux_unix/Performance_tip_for_Ubuntu_Edgy_and_Feisty_users](http://www.digg.com/linux_unix/Performance_tip_for_Ubuntu_Edgy_and_Feisty_users)
[http://beuno.com.ar/?p=4](http://beuno.com.ar/?p=4)
> 
Performance tip for Edgy and Feisty users

I&#8217;ve been following a thread in the forums that refers to a very simple change in Ubuntu that actually is improving the responsiveness of many Edgy and Feisty users (including me).
I have no idea why this is, or if it has any side effects, to be careful.

Edit your &#8220;/etc/hosts&#8221; file:
$ sudo gedit /etc/hosts

You should see something like this:

127.0.0.1 localhost
127.0.1.1 martin-laptop
(and if your in Feisty, some lines about IPV6

Now, add the following:

127.0.0.1 localhost martin-laptop
127.0.1.1 martin-laptop
(Replace &#8220;martin-laptop&#8221; with your hostname)

Save. Should work instantly, or sometimes on reboot.

The forum thread is: [http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765).

---

