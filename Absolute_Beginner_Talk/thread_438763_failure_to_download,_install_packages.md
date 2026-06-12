---
title: "failure to download, install packages"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by oui_buenafe on 2007-05-10
Recently got a brand-new PC to tweak for the lab/office I work.  Installed Ubuntu Feisty as its only OS.

The OS runs smoothly and I'm able to see the Windows-based workstations in the office network (aside from being able to go online via Mozilla) BUT I have some minor but irritating problems:

(1) I can't download nor install additional packages: I've enabled all the repositories (main, universe, restricted, multiverse) in Synaptic, but whenever I reload it, Synaptic fails to download the packages and gives me this message:

[INDENT]*The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.*
[/INDENT]
(2) If the trouble in (1) is annoying enough...the trouble I got by using Add/Remove Applications is more annoying.

The first message it displays is: 
[INDENT][I]The list of available applications is out of date
To reload the list you need a working internet connection.[/I]
[/INDENT]
I ignore it and try to download an package (for this case, GStreamer extra plugins).  First it displays this message:
[INDENT][I]**Install community maintained software?**
GStreamer extra plugins is maintained by the Ubuntu community.
You need a working internet connection to continue.
[/I][/INDENT]

Which I find (personally) idiotic because the PC is connected to the network (and I can actually access the Net).  I proceed with the "Install" command and it begins to "download" the packages...and then BOOM, this message (again):

[INDENT]*The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.*[/INDENT]

BTW, it gives me the list of repository URLs which can't be accessed (God knows why?!)--here's a snippet:

[INDENT][I][http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (92 Protocol not available) [IP: 91.189.89.6 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_PH.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_PH.bz2:) Could not connect to archive.ubuntu.com:80 (91.189.89.6). - connect (92 Protocol not available) [IP: 91.189.89.6 80][/I][/INDENT]

I'm at the end of my wits here, being new to Ubuntu (or Linux, in general).  Is it because of the network I'm in (it has its own main and firewall/DHCP servers) or how I configured the PC? :confused:

---

### Post by shadowboxer_k on 2007-05-10
maybe the site where you usually download these packages from is down for maintenance. you can change the location very easily by doing this:

system -> administration -> software sources
there should be a drop down menu, so just pick another country. that should do. and of course, you can always change it back. 

just a guess.

---

### Post by oui_buenafe on 2007-05-10
Hi!

Did that...and the same thing happened. :sad: The oddest thing here is that I checked my network connection: I can ping my office server, but I can't ping ANY other servers...

---

### Post by shadowboxer_k on 2007-05-10
hey,

i'm sorry i couldn't help. i hope someone else can.

good luck!

---

### Post by Sef on 2007-05-10
Could you post your sources list here?

From the Terminal:

> cat /etc/apt/sources.list

---

### Post by apienk01 on 2007-05-10
I suspect your Windows network administrator have set up a very resticted web proxy that allows only traffic to basic ports, eg. http (80) and https (443), and only from a few legitimate browsers and email clients. It is made by checking the 'user agent' string provided by many applications, eg. Internet Explorer presents himself as 'Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)'.

If that is the case, you won't be able to connect anywhere beyond your server with any apps using simple network protocols like ping. Synaptic and apt provide "Debian APT-HTTP/1.3" user agent, so if the server filter allows only IE, Firefox and Opera, apt won't work. Ask your administrator to add this user agent to his server 'allowed' filter. This is your only option.

BTW, on Fedora, apt-rpm already has been patched to allow custom user agent strings (in order to mask apt or Synaptic as IE, for example), but unfortunately for Ubuntu this patch is still on the wishlist.

---

### Post by apienk01 on 2007-05-10
Ah, forgot. If your admin turns to be totally windows-blinded, you can download and install packages manually. Browse to [http://packages.ubuntulinux.org]("http://packages.ubuntulinux.org") with Firefox, find and download a package for your Ubuntu distribution and architecture, and then just double-click on it.

Good luck!

---

### Post by oui_buenafe on 2007-05-10
Thanks for the suggestions!

I was able to find my way around the problem...**apienk01**, the idea about the proxy settings hit me a few hours ago (the ping failures clued me to the solution).  True enough, I had to configure the server proxies for the PC (**System > Preferences > Network Proxies**).  Now Synaptic and the usual terminal apt-get work nicely.

(Of course the firewall and proxies are stringent, being one of the university server and all...)

---

### Post by costis on 2007-05-26
Hello, I am having the similar problem, I am logging in to an ssh server with
```
$sudo ssh  username@ip.address -L 80:localhost:800
```

Then I go to to System > Preferences > Network Proxy
I choose from the "Proxy Configuration" tab
Manual proxy configuration 
I check the Use the same proxy for all protocols and then in
Http proxy:  localhost   Port: 80  (no authentication is required)

Finally, in the "Advanced Configuration" tab, the "Ignore Host List" includes only
127.0.0.0/8
*.local
localhost 


However I cannot neither ping nor use apt-get... any ideas?

---

### Post by costis on 2007-05-29
Solution found!!!
```
$export http_proxy=http://127.0.0.1:80
```
for my case...

---

