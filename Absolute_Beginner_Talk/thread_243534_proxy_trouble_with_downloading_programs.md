---
title: "proxy trouble with downloading programs"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by xarinatan on 2006-08-25
i`ve got 2 pc`s and i use a windows program named analogX proxy to route the internet from the windows pc to the kubuntu pc.
http is ok and i can use google and download some things on the internet,
but when i go to a ftp-site or when i try to download programs like "make" and "automake" in adapt or in apt-get i can`t find it.
i have no acces to the servers of kubuntu, i can`t download updates and i can`t get online with kopete IM. so i also can`t install ndiswrapper to use my own wlan-stick under kubuntu.

does anyone know howto..?:confused:

---

### Post by benfindlay on 2006-08-25
I reckon it's probably your windows pc thats at fault. I'd recommend you get rid of the 3rd party prog for proxying and just use the built-in windows connection sharing. Setting this up on the device that connects to your modem in windows should automatically assign an ip to your ethernet/firewire (or whatever else you're using to link to your ubuntu pc).

Up until about 3 weeks ago I had 3 pcs all running over 1 usb wifi card in my house, because toe router was downstairs at another pc. The 3 pcs were networked using a switch, and the pc with the usb wireless had internet connection sharing enabled. This will simply make your windows pc function as a "DHCP within a DHCP" server. The linux box will be assigned an ip by your windows pc, and will just use the windows pas as its default gateway, and everything should work peachily!

Hope this helps!

---

### Post by xarinatan on 2006-08-25
i already tried this. when i say share connection the windows pc AND the kubuntu pc both can`t get on the internet.](*,):evil:

---

### Post by benfindlay on 2006-08-25
Are you bridging your internet connection? If you use Incernet Connection Sharing and you setup a bridge then it won't work. The whole point of ICS is that it does it all for you.

Why can't both machines get on the internet together? I take it the modem is plugged inot your windows pc, and then there is a connection between your windows pc and your ubuntu pc? If this is so, then its the exact same setup I had and ICS worked rather peachily! ;)

---

### Post by xarinatan on 2006-08-25
how do i setup this?
i go to (i have to guess how it`s called because my version is dutch) network connections and i click left on the wireless network connection and then i go to the tab advanced and enable "share internet connection"

is this how it work?:-k 

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
"no keyboard found, press any key to continue" :twisted:

---

### Post by benfindlay on 2006-08-25
Yes, then it should deal with everything for you. It assigns an ip to the 2nd network card which in turn assigns an ip to the network card in the ubuntu box, and both will access the internet simultaneously

---

### Post by Woei on 2006-08-25
> **xarinatan said:**
> i`ve got 2 pc`s and i use a windows program named analogX proxy to route the internet from the windows pc to the kubuntu pc.
http is ok and i can use google and download some things on the internet,
but when i go to a ftp-site or when i try to download programs like "make" and "automake" in adapt or in apt-get i can`t find it.
i have no acces to the servers of kubuntu, i can`t download updates and i can`t get online with kopete IM. so i also can`t install ndiswrapper to use my own wlan-stick under kubuntu.

does anyone know howto..?:confused:

Well, by default, all repositories enabled by the Ubuntu installer use the HTTP protocol, so you're good there with the proxy server. However, when you're talking about apt-get, you're probably running in a terminal, which will probably not pick up the proxy settings of Firefox, KDE or Gnome. The solution to make programs like apt-get and generally any program that accesses the net from the commandline aware of your proxy, is through the http_proxy environment variable. So, before running apt-get, you'd run something like ```

export http_proxy='http://192.168.1.1:8080'
apt-get install blah
```

There's also the ftp_proxy environment variable you can export analogously if your proxy server running on Windows can do FTP proxying too. Some programs only react to the HTTP_PROXY variable, so if it doesn't work immediately, try exporting the same proxy server through the same variables, but now in all uppercase.

---

### Post by xarinatan on 2006-08-25
well when i used adept to install\download new packages i could not found any... uses adept the standard proxy? or do i have to  setup another proxy?

---

### Post by benfindlay on 2006-08-25
you don't need ANY proxy set up. Internet Connection Sharing in Windows deals with it for you. It's one of the few things windows does really well ;)

---

### Post by xarinatan on 2006-08-25
that`s just the point... windows management on the way like i said DOESN`T WORK:evil: :cry:  i only could post this with analogX proxy!...
and when i use adept or try to download ftp-sites i can`t succeed...

---

### Post by xarinatan on 2006-08-28
i think it is a setting somewhere in connetions, but i don`t know how to set it likewise i can use adept packetmanager to download the neccesary programs to install ndiswrapper so i can connect the w-lan stick directly. i use analogX proxy to route the internet from windows directly to my linux pc, but i can ONLY acces the internet in the webbrowser which is http (i use google and this forum). does anyone know how to set the settings in connections like i can download with adept and Ktorrent (etc.) ??:confused:](*,)

---

### Post by bplus on 2006-08-28
I had a porblem with my proxy until someone suggested this:
make a file /etc/apt/apt.conf and add the following lines:


Acquire::http::Proxy "http://user:password@xxx.xxx.xxx.xxx:portnumber/";
Acquire::ftp::Proxy "http://user:password@xxx.xxx.xxx.xxx:portnumber/";

---

### Post by bplus on 2006-08-28
and those smily faces are supposed to be colons :  btw.

---

### Post by benfindlay on 2006-08-28
Colon followed by a P, as in password I believe, so its user[colon]password, where user and password are youre personal username and password

---

### Post by xarinatan on 2006-08-28
yes but there`s one little problem. i can`t download "make" , so i can`t make a file in there....

---

### Post by benfindlay on 2006-08-28
make is just a command. It's already built into linux, along with the ./configure and the make install command

---

### Post by xarinatan on 2006-08-29
i already tried to use make in the terminal. 
it just isn`t there.... maybe i do something wrong but.. i don`t know what. if i try to use "make" he says: command not found.....
did i something wrong?

---

