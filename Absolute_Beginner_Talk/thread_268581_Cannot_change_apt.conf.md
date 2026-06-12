---
title: "Cannot change apt.conf"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by ON6TS on 2006-09-30
Hi all,

Installed Ubuntu 6.06.1 desktop yesterday and having troubles with update and repositories.
Tried to remove -Acquire::http::Proxy "false"- from apt.conf as was suggested in some posts but cannot save changes.
BTW: this is the only line in apt.conf .

Have direct internet connection via router and can browse.

Temporarily going to archive with browser and then can download but very cumbersome due to different addresses.

Thanks in advance for your help !
ON6TS

---

### Post by tagra123 on 2006-09-30
From a terminal

sudo gedit /etc/apt.conf

Also try


ping [www.google.com](www.google.com)

If you get a response from the ping then synaptic should work. You can press ctrl-c to stop ping.


also check your settings in synaptic and make sure you have allowed access to the internet.

One other thing: I had to manually enter my dns addresses under system - administration -networking (DNS Tab) because of using a static IP address and by entering this apt and synaptic began working correctly for me.

---

### Post by bulldog on 2006-09-30
The file you're talking about is in /etc/apt/apt.conf 

If you can discribe your probs a little more to the point,it's possible you get the proper help.

If you having troubles with the repositories you better take a look at your
/etc/apt/sources.list where the repo's are listed.

It's possible you have the wrong country code.

---

### Post by ON6TS on 2006-09-30
Thanks a lot for your reply.
My apt.conf is now empty and saved but Synaptic still does not work.
Ping to [www.google.com](www.google.com) is OK !
Tnx
ON6TS

---

### Post by Ziox on 2006-09-30
> **ON6TS said:**
> Thanks a lot for your reply.
My apt.conf is now empty and saved but Synaptic still does not work.
Ping to [www.google.com](www.google.com) is OK !
Tnx
ON6TS

what's the output when you do this command:

[PHP]sudo aptitude update[/PHP]

---

### Post by tagra123 on 2006-09-30
On my system apt.conf didnt exist at all until I installed apt-proxy on a server and get my updates from my server but you shouldnt need that file.

If you can ping to google then you have internet access that apt should be able to use

Try looking in your /etc/apt/sources.list and copying the base url minus the deb part into a browser and see if it connects. I'm guessing that you already did this by your post.

Copy the contents of your sources.list and post here so we can have a look.

No start synaptic

Panel Menu System - Administration - Synaptic Package Manageer

When it opens

Uset the menu: Settings - Preferences and then click on the Network tab. Is it marked "Direct Connection to the Internet"?

Do you happen to have more than 1 network card on your computer?

---

