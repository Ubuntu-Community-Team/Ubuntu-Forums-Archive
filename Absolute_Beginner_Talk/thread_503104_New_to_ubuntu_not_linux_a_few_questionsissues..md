---
title: "New to ubuntu not linux a few questions/issues."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by boomix on 2007-07-17
Hello

I am in love with Ubuntu, its everything I've wanted from Linux based OS. however I am curious about a few things. I've used Linux flavours over the years but never for long. I plan on switching over now because of Ubuntu.

First question. apt-get install apache2 fails with no such package or something similar. I've looked over it last night but haven't had much time to devote to the issue just yet. Quick pointer to similar issues (installing apache search didn't yield anything in particular) would be appreciated.

Second: I am running Ubuntu 7.04 on Dell XPS2 and I have WPA wireless setup at home. What I am wanting to know is this: Is it possible to setup manual configuration from Roaming mode into static WPA and not WEP mode? I mean I can manually connect to my  WPA connection but every once in awhile it asks me for the 64 character key. I would like to have it set and saved so i don't have to 

Other then that I am perfectly happy. :)

---

### Post by AlexenderReez on 2007-07-17
> **boomix said:**
> Hello

I am in love with Ubuntu, its everything I've wanted from Linux based OS. however I am curious about a few things. I've used Linux flavours over the years but never for long. I plan on switching over now because of Ubuntu.

First question. apt-get install apache2 fails with no such package or something similar. I've looked over it last night but haven't had much time to devote to the issue just yet. Quick pointer to similar issues (installing apache search didn't yield anything in particular) would be appreciated.

Second: I am running Ubuntu 7.04 on Dell XPS2 and I have WPA wireless setup at home. What I am wanting to know is this: Is it possible to setup manual configuration from Roaming mode into statis WPA and not WEP mode? I mean I can manually connect to my  WPA connection but every once in awhile it asks me fo the 64 character key. I would like to have it set and saved so i don't have to 

Other then that I am perfectly happy. :)

first question...install using synaptic..it will remove and install requirement for it...make a search in synaptic...maybe misspell the version or whatever....

2.see how to in tutorials and tips.. i found it before but forgot to bookmark it...

---

### Post by davidjmayo on 2007-07-17
Hi

1) also in synaptic check settings==> repositories

2) don't know no wireless

---

### Post by deadlikeoscar on 2007-07-17
Do you have wpasupplicant installed? I think there is a wpagui package in Synaptic (System-->Administration-->Synaptic Package Manager) as well and it may help you to configure your WPA options. I don't use wireless so it is just a guess.

---

### Post by Papi-KB7VGW on 2007-07-17
Hi  Keyring mgr holds my wep key and automatically logs in when I boot up.  I have to give it my admin password to activate it.:)

---

### Post by stchman on 2007-07-17
> **boomix said:**
> Hello

I am in love with Ubuntu, its everything I've wanted from Linux based OS. however I am curious about a few things. I've used Linux flavours over the years but never for long. I plan on switching over now because of Ubuntu.

First question. apt-get install apache2 fails with no such package or something similar. I've looked over it last night but haven't had much time to devote to the issue just yet. Quick pointer to similar issues (installing apache search didn't yield anything in particular) would be appreciated.

Second: I am running Ubuntu 7.04 on Dell XPS2 and I have WPA wireless setup at home. What I am wanting to know is this: Is it possible to setup manual configuration from Roaming mode into static WPA and not WEP mode? I mean I can manually connect to my  WPA connection but every once in awhile it asks me for the 64 character key. I would like to have it set and saved so i don't have to 

Other then that I am perfectly happy. :)

Make sure all the software repositories are enable (universe, multiverse, etc.)

As far as wireless Network Manager does not support static IP with wireless encryption.  I run WPA2 and it never has asked me to enter the passphrase since I initially typed it in.  Supposedly wicd is a far better wireless manager than network manager.

---

### Post by boomix on 2007-07-17
Whoa, thanks guys keep the responses coming. I am sending this URL to myself at home so I can get on fixing it all.

---

