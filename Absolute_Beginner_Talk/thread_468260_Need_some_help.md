---
title: "Need some help"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by tahmina on 2007-06-08
HI everyone
I am completely new to ubuntu and would like some  help. I have installed ubuntu and now I need to connect it to my existing network and I was wondering how to go about this. Your help will be appreciated.

---

### Post by starcraft.man on 2007-06-08
[I think you want this]("https://help.ubuntu.com/community/SettingUpSamba") for general reference regarding Samba for networking. 

If you have a specific question, you have to be more specific...

---

### Post by ryanVickers on 2007-06-08
I think if it's a wired in one, it's automatic, but lots of people have trouble with this - it's one of the ubuntu hurdles :)

if you have a wireless card, my method is this, but everyone will be different.  If this doesn't work, then please post your network card type and router and that for other people's sake that might know more about this :)

I went into System > Administration > Network and checked on the wireless, then go into properties.  turn off roaming mode and specify your router name (**not** company/make) and your wep key and also pick dynamic IP (probably).

Then close the properties and wait for a small window with a useless progress bar to appear and it should "activate" the network - if this doesn't appear in about 5 seconds, click stuff till it does :)

then go to the terminal and do this:
> sudo iwconfig ra0 channel # (probably 6, but mine is 9 (negates conflict with neighbor :)))
> sudo iwconfig ra0 key restricted ######################### (this is the same key entered eirlier)
> sudo iwonfig ra0 ap ##:##:##:##:##:## (mac adress I think)

and it should spring to life after about between 1 second and 10 minutes :)
also try a comit command (however it's spelled) to speed things up if your card supports it!  You can also lookup iwconfig in System > Help and Support

Hope this helped!

---

### Post by tahmina on 2007-06-08
Well I have a existing server providing internet, printing and file sharing services. And I need to connect to that server to do any of the above mentioned things. Now do I need Samba to connect to this server or can I do without it.
Thank you.

---

### Post by ryanVickers on 2007-06-08
Oh, I didn't really get that :)

I think you can connect *without* any special packages if your not going across different OS's

Try Places > Connect to Server and choose the apropriate connection type and enter the data.  It should work ok and will auto-connect on each login from then on until told not to!

---

