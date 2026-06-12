---
title: "Ebook Pro"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Linuxgenius on 2007-08-19
im trying to open a couple of my ebooks i get this message any suggestions 

Cannot open /home/linuxgenius/Desktop/vpmadden08n1.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by Dr Small on 2007-08-19
```
sudo apt-get install wine
```
```
wine /home/linuxgenius/Desktop/vpmadden08n1.exe
```

Dr Small

---

### Post by Linuxgenius on 2007-08-19
> **Dr Small said:**
> ```
sudo apt-get install wine
```
```
wine /home/linuxgenius/Desktop/vpmadden08n1.exe
```

Dr Small




err:bitmap:StretchDIBits Invalid bitmap
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:shdocvw:PersistStreamInit_InitNew (0x185c40)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:shdocvw:navigate_url Unsupported arguments
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionW Option 7 STUB

---

### Post by Linuxgenius on 2007-08-19
any help?

---

### Post by Linuxgenius on 2007-08-20
bump

---

### Post by Dr Small on 2007-08-20
Apparently, that exe will not run with wine. Some don't.

Dr Small

---

### Post by Tautoa on 2007-09-16
Erm... just so you know, an .exe file isnt an ebook?

---

### Post by Charybdisz on 2008-03-19
Hello!

Someone could please test me an .exe, whether it works with the latest Wine, or not? It is an ebook compiled with Ebook Pro 6.

I don't have Linux, but I have to know whether a specific application runs on Wine or not. Thanks very much in advance!

[Here is the EXE file]("http://downloads.marketingtips.com/lead-ebooks/FoolproofSuccessStrategies.exe")

It is virus-free (if it matters), and the provider website is a trusted website, it has Alexa rank 9200 by the way.

Please someone download and test it with the latest Wine. BTW you don't have to install this program, because it runs automatically.

Thanks again!

---

### Post by handydan918 on 2008-03-19
Alexa isn't exactly a trusted site itself. Just because they are big doesn't mean they (or their clients) are scrupulous.
But, knock yourself out. Some exploits have been run in Wine before...

edit: Tell me, does it concern you that > INTERNET_OPTION_SEND/RECEIVE_TIMEOUT seems to be trying to make an internet connection?
JUST from installing the program?

---

### Post by Charybdisz on 2008-03-19
Go to the main domain, and you will see that hundreds of people install this file every day. Really.

I installed this file here in XP, I have the 2 best anti-virus and anti-spyware software here (Nod32 and CounterSpy), and they did not detect any virus.

Yes, internet connection required, it wil connect to a central Ebook server to validate your copy. And at the same time it will collect and send all your password and computer details, then it will delete all your hard drive. No just kidding, it won't happen :)

But if wine can cause this security risk, then you'd better uninstall it. What if you download a Linux program, which will launch wine with a very dangerous Windows virus and spyware?

---

### Post by handydan918 on 2008-03-19
OK, as long as you're happy!

:popcorn:

---

### Post by zvacet on 2008-03-19
@ **Linuxgenius**

After installing Wine run in terminal 

```
winecfg
```

---

### Post by Charybdisz on 2008-03-19
Thanks for support, you Linux gurus are afraid to install a program, lol.

---

### Post by Frumious Boojum on 2008-03-19
> **Charybdisz said:**
> Go to the main domain, and you will see that hundreds of people install this file every day. Really.

I installed this file here in XP, I have the 2 best anti-virus and anti-spyware software here (Nod32 and CounterSpy), and they did not detect any virus.

Well, if this is how you determine safe files, you could be in for a surprise someday.

First, just because hundreds of people have downloaded a file, that doesn't mean that it's safe.  Second, not even the best anti-virus software can detect absolutely everything -- many have trouble detecting rootkits, for example.

In short, relying only on the number of downloads so far and the antivirus could get you into trouble when working in windows.

---

### Post by chilinski on 2008-03-19
In addition, a virus shows up "in the wild" before the anti-virus people can learn about it and write the stuff to block it. So it's highly likely you can get a new virus way before the anti-virus people find out about it.

---

### Post by Charybdisz on 2008-03-20
I want to reply to the original question.

Ebook Pro viewer requires Internet Explorer 4 or later. So I think you should install IE6 first. Then try again running the viewer.

---

### Post by Charybdisz on 2008-03-20
Hello,

I have just got an official Ubuntu live CD, with nice Ubuntu logo :)

I would like to launch [this EXE file]("http://downloads.marketingtips.com/lead-ebooks/FoolproofSuccessStrategies.exe"), but I got the same errors as the topic owner.

This application needs Internet Explorer 4 or higher. So should I install Internet Explorer with Wine first? Does it make any difference?

So question is, that if you want to run an application with Wine which requires Internet Explorer APIs, do you have to install INternet Explorer first? What is the easiest way to do this?

(The provided program is virus free, tested both on Windows and Linux with Wine).

---

### Post by handydan918 on 2008-03-20
> **Charybdisz said:**
> Thanks for support, you Linux gurus are afraid to install a program, lol.

Yes. 
And a more humble, less scornful man might ask himself "why?".

---

