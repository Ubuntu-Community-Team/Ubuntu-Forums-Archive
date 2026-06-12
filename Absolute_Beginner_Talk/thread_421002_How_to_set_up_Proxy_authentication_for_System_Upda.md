---
title: "How to set up Proxy authentication for System Updates ?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by lennie2 on 2007-04-24
I am connecting at work to a Squid proxy (I don't know what authentication :-(  ) If I rowse to a website it pops up with a box asking for my username and password . This works fine for browsing and Firefox can rememer that password howeer, how or where so I tell Ubuntu (6.10) to submit my u/name and password for the updates ?

I have set System-> preferences -> Network Proxy.

It gives me a 407 Proxy Authentication error. I have attached the error message.


Many thanks for any help,

---

### Post by dcstar on 2007-04-24
> **lennie2 said:**
> I am connecting at work to a Squid proxy (I don't know what authentication :-(  ) If I rowse to a website it pops up with a box asking for my username and password . This works fine for browsing and Firefox can rememer that password howeer, how or where so I tell Ubuntu (6.10) to submit my u/name and password for the updates ?

I have set System-> preferences -> Network Proxy.

It gives me a 407 Proxy Authentication error. I have attached the error message.


Many thanks for any help,

There is a special place in the Synaptic Preferences for that.

---

### Post by chakkaradeep on 2007-04-24
> **dcstar said:**
> There is a special place in the Synaptic Preferences for that.

Watever you add there, its not going to work as this is a known bug of **gksu** and **synaptic**. From Menu, if you open Synaptic, it will not work and **gksu** strips off the proxy authentication (uname and password). Whereas if you start Synaptic from terminal using **sudo synaptic** , it works.

---

### Post by lennie2 on 2007-04-24
Many thanks for this reply it makes sence I just got it working via sudo apt-get upgrade and will try the GUI now ...
I found this link usefull :[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/1320")

---

### Post by mincho on 2007-05-02
I have tried everything but problems still remains .. so  what can i do now... please help

---

### Post by lennie2 on 2007-05-03
Please provide more information, r you going through a proxy ? What proxy, do ytou know what authentication ? etc. what is the error you get ?

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by motoperpetuo on 2008-04-12
i'm in the same situation as a lot of people. that is, i'm behind a firewall and i can get to the internet through firefox just fine, but i can't get updates or synaptic to work, even when i follow jorno's advice above.

i wonder if the problem might be the port numbers. if i specify this as my http proxy in firefox:

nyc-proxy.ext.acme.com

and my port as 80

does that mean i should specify 80 for LISTEN_PORT in server.conf? or could it be something else? 8080? maybe 5865? is this info that i would have to get from a system administrator?

i'm also assuming that PARENT_PROXY would be nyc-proxy.ext.acme.com and that PARENT_PROXY_PORT would be 80, correct?

---

### Post by arpitubun on 2008-06-19
I had smae problem,you need to go for system->admin->synaptic packager-manager->network setting.
It worked for me ,Hope it will work for you also

---

