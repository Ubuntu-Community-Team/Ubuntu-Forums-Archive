---
title: "email notifiaction in Pidgin Tray Icon"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Chris11 on 2007-11-13
is that possible? I only get new message notification in the tray icon.... email notifiaction only in the buddy window...

Chris

---

### Post by zabien1970 on 2007-11-13
STOP read top sticky first

---

### Post by p_quarles on 2007-11-13
Don't run that command. It's a spammer.

---

### Post by carlosjuero on 2007-11-13
> **Chris11 said:**
> is that possible? I only get new message notification in the tray icon.... email notifiaction only in the buddy window...

Chris
To answer your question - have you tried looking at the plugins that are installed? I think there is one for mail notification; I know that if you get the Plugin Pack (link is on Pidgin website) and install it then you can add a little pop up window (like Yahoo! IM & MSN have on Windows) that will tell you when new messages arrive in the account.

---

### Post by mcduck on 2007-11-13
> **Chris11 said:**
> is that possible? I only get new message notification in the tray icon.... email notifiaction only in the buddy window...

Chris

I don't know if Pidgin can do that, but i you get the program called Mail Notification, it will monitor your mail accounts and show icon in notification area when you got new mail. It can also be configured to run commands when you have new mail, so you can set it to play a sound, or whatever you want (I have configured it to light the mail led on my laptop..).

Mail Notification supports multiple mail accounts, and many different mail protocols, including gmail.

Just install the mail-notification package from Synaptic, Add/Remove or run 'sudo apt-get install mail-notification' to install it. After that you can configure it in System/Preferences/Mail Notification.

---

### Post by Chris11 on 2007-11-13
zabien1970 and p_quarles:

I subscribed to my thread and the first answer was the rm carp.. thx for you advice!...

carlosjuero:

I looked at the plug ins and there is no such thing as email notification... If i remember right Gaim notified new mail changing  the tray icon. As pidgin notifies new mail by adding a message in the buddy windows, I thought maybe there is some plugin for a tray icon message.  I don't have always the buddy window on top.

mcduck:

I installed the suggested program also its no a additional program running in the background...once I find a notifier plug in for Pidgin I'll uninstall it

thx to all , Chris

---

### Post by p_quarles on 2007-11-13
Glad to hear you didn't run that. Several people weren't so lucky. 

Anyway, I use Kopete, so I can't test this out, but there are a couple packages in the repos that might solve this issue:
```
sudo apt-get install pidgin-extprefs pidgin-plugin-pack pidgin-libnotify
```
Hope that helps.

---

### Post by Chris11 on 2007-11-13
> pidgin-extprefs pidgin-plugin-pack pidgin-libnotify 

unfortunately they don't do the job.. thx anyway, Chris

---

### Post by carlosjuero on 2007-11-13
> **Chris11 said:**
> unfortunately they don't do the job.. thx anyway, Chris
This is the plugin pack I am talking about: [http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)

It has to be built from a downloaded source, one of the plugins offered has little pop window thingies that let you know when new mail is available (per IM account). I use gmailnotify for GMail though so I dont know if it works with GTalk accounts in Pidgin, it should though.

---

### Post by Chris11 on 2007-11-14
Thanks carlos

I saw that list and the plug in I'm looking for is not listed.. anyway I think it does no exist, as i found down on the page a link to a ticket asking precisely for that plug in.. it's open since 6 month, last modified 5 month ago..

[http://plugins.guifications.org/trac/ticket/344]("http://plugins.guifications.org/trac/ticket/344")

Chris

---

### Post by carlosjuero on 2007-11-14
> **Chris11 said:**
> Thanks carlos

I saw that list and the plug in I'm looking for is not listed.. anyway I think it does no exist, as i found down on the page a link to a ticket asking precisely for that plug in.. it's open since 6 month, last modified 5 month ago..

[http://plugins.guifications.org/trac/ticket/344]("http://plugins.guifications.org/trac/ticket/344")

Chris
Ah ok, wish I could help more. The only other email I have a notifier for is GMail and I use the GMailNotifier applet, maybe they will get on the other plugin soon - who knows :)

---

