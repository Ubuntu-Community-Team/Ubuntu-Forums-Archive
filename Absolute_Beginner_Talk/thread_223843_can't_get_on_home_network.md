---
title: "can't get on home network"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-07-27
my home computer runs windows. I just installed a wireless router on my desktop. My laptop uses ubuntu. I was unable to get on the network. Is there any procedure I'm supposed to go through?

---

### Post by friedokra on 2006-07-27
is ubuntu supposed to detect my wireless connection?

---

### Post by friedokra on 2006-07-27
bump

---

### Post by easyease on 2006-07-27
not an area i know much about but the word samba springs to mind..... worth typing in the searchbar at least....

---

### Post by richardward101 on 2006-07-27
can you elaborate?

What exactly doesn't work (internet, samba, any network acess at all)?

What have you tried, what happened?

What is the setup of your router? are you trying to connect by wires or wireless, if wireless, are you using WEP or WPA (it'll say in your router configuration pages)

---

### Post by friedokra on 2006-07-27
the internet doesn't work. I'm not really sure what I have to do in windows (if anything) to enable other computers to get on the web using my router. My router is a D-Link 524. I should be able to get on the internet if everything was working properly. Maybe I have to do something in Windows? My internet works fine on ubuntu if I'm hooked up to a modem. I am not getting any error messages.

---

### Post by friedokra on 2006-07-27
I don't even know what samba is. I use mozilla firefox. And I've never used ubuntu to get on wireless internet before. Is ubuntu just supposed to detect wireless internet and connect?

---

### Post by NT4usB on 2006-07-27
the search engine on the forum is weak but a useful workaround is use google with the format:
site:ubuntuforums.org <searchword> <searchword> ...

this search returned lots of tips:
[site:ubuntuforums.org windows wireless samba network]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+windows+wireless+samba+network&btnG=Google+Search")

ed: now I see you're having an internet connection problem, **not** a network problem. try the same search with appropriate keywords.

---

### Post by friedokra on 2006-07-27
no. I don't want to share files between the computers. I just want to use the internet on my laptop by using the router.

---

### Post by richardward101 on 2006-07-27
ok, how do you connect with your windows pc, is it also wireless? if so you'll need the same details (a network name and a password) to get ubuntu on the wireless network as you do for windows. If windows is wired, and you don't know the password and network name, then on windows go to [192.168.0.1]("http://192.168.0.1/"). this ought to be the web interface for your router (if not, check the router manual). now you need to use this interface to set up wireless. If you have the choice i'd recommend selecting WEP rather than WPA (less secure, but easier to set up). The next question is whether or not ubuntu is actually detecting your wireless card. use the System -> Administration -> Networking  option in ubuntu's menu, and see if there is a wireless card there. If there is, go into its properties and fill in the details you know (you'll probably want 'passphrase' in key-type, and select DHCP rather than static ip). at this point I would hope that the internet works, once you've clicked ok.
If anything goes wrong, let us know what.

---

### Post by friedokra on 2006-07-27
well, I'm here at my university now. We have campus-wide wireless internet and I'm not connecting to it. How will I know if my wireless card is being recognized by ubuntu. I know I have one because when I had windows installed on the same laptop, wireless internet in hotels,etc. was working. I activated the wireless card (eth1 ?) and still no internet. Also, I have to activate the wireless "connection" (eth1) each time I click on 'networking. (it is "not active" unless I activate it and when I close the window and open the [networking] window,  I have to activate it again)

---

### Post by richardward101 on 2006-07-28
```
iwconfig
```
will tell you which card is the wireless one, the others should say something like "wireless extensions not found."

I assume that your uni network is unecrypted and you have to log on properly in a browser.

lets assume you've confirmed its eth1 using iwconfig:
```
sudo ifup eth1
sudo iwconfig eth1 essid "network_name_goes_here"
dhclient eth1

```
If all that works you may want to put it in a bootscript, or make an icon for it on the desktop. Plenty of tutorials on how to do that on google, or just ask here.

if it doesn't, report back with any error messages.

---

### Post by richardward101 on 2006-07-28
PS if you don't know the name of the network, use:
```
iwlist eth1 scanning
```
or perhaps its 
```
sudo iwlist eth1 scanning
```
I forget, been a while since I used my wireless.

Assuming again that the wireless is actually eth1

---

### Post by friedokra on 2006-07-28
hey thanks for coming back to help. I started a newer thread about this same problem:

[HTML]
http://www.ubuntuforums.org/showthread.php?t=224260[/HTML]

If you have time to read through it and see what I attempted to do , you may be able to help me.

---

