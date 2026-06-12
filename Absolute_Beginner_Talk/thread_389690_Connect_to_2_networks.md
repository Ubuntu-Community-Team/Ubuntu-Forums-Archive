---
title: "Connect to 2 networks"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by xboxSlayer on 2007-03-21
I have just installed Ubuntu Ultimate 1.3. I like it and I want to try it as my primary OS. I have 2 questions. First I am connected directly to the internet from this computer using a cable modem. I would like to connect to my xboxes that are connected to a wireless router. In windows it would automatically connect to both but in Ubuntu I can only connect to one or the other. I guess I want to setup internet connection sharing.

Secondly, I want to share a folder on the network so that my xbox1 can connect to it. Again Windows did this automatically but I have shared the folder I want but the xbox can't connect. It is a folder in my windows partition that I have mounted so that Ubuntu can read and write to it and I have shared it with SMB.  Like I said my xbox is connected to a wireless router and when I switch Ubuntu to connect to the wireless router the xbox doesn't see the shared folder. 

Any help would be appreciated. Thanks.

---

### Post by cowlip on 2007-03-21
[http://kde-apps.org/content/show.php?content=53675](http://kde-apps.org/content/show.php?content=53675) There's an internet connection sharing wizard here.

BTW are you using XBMC on your xboxes?

Try this for sharing your folders from Ubuntu: [https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

---

### Post by xboxSlayer on 2007-03-21
Thanks, I'll give those a try. I'm not a total linux noob but I'm still a bit of a noob. I'll see if these help and I'll post questions later.

---

### Post by cowlip on 2007-03-21
Hi,
I just found out from another thread that the package "firestarter" which you can apt-get apparently allows you to share the internet too.  Just more info for you

---

### Post by xboxSlayer on 2007-03-23
OK so I switched to the 64 bit version of Ubuntu. I have successfully installed Beryl, setup flash and java in Firefox and got utorrent to work under wine. This linux thing is getting easier all the time. But I still have the same problem.

If I go to System - Administration - Networking and try to setup my wireless card, my internet stops working altogether. My wired nic is setup for DHCP. I'm trying to connect my wireless card to a wireless router so I can hookup the my xboxes to the router and connect to the internet. This is the way is was setup under windows and it worked great.

My wireless router is also a dlink dsl modem, I switched to cable. The routers IP address is 192.168.0.1 and the xboxes would get thier IP address from the router. What are the settings I need to change to get this to work, it works either with the wired or the wireless but not both.

By the way cowlip, I am trying to use xbmc. Once I can connect to the router I'll work on setting up the shares. Actually I did try firestarted but it kept saying my wireless card wasn't responding.

---

### Post by xboxSlayer on 2007-03-23
OK wow, I got it working. When I tried to set it up in Ubuntu Ultimate, I couldn't connect to both networks. Now that I set everything up myself, I can. Then I selected the the folder I wanted to share, installed SMB and everything works. Awsome. I think that Ultimate had so many different programs installed that something was conflicted with my setup. Oh well, everything works great now.

---

