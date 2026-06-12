---
title: "Internet help"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by jbomber on 2006-07-30
Hello, I have a WRT54G router (same as the pic)

[http://en.wikipedia.org/wiki/WRT54G](http://en.wikipedia.org/wiki/WRT54G)

I am able to connect wirelessly for a short time, it drops signal a few times before losing all connection. I am unable to connect with my ethernet cable. I am on optimum online cable internet. Can anyone show me a step by step guide on how to connect? I tried giving myself a static ip, but that didn't work. I have no idea how to start. 

So these are my two problems: 

1. keeping wireless internet without dropping
2. connecting with wires with my router


thanks!

---

### Post by x64Jimbo on 2006-07-30
Need more info.
Card model? Driver? Security level on router?

---

### Post by califdon on 2006-07-30
> **jbomber said:**
> 
So these are my two problems: 

1. keeping wireless internet without dropping
2. connecting with wires with my router

thanks!


1. sounds like possibly weak signal...what does your client computer show for signal strength?

2. have you followed the step-by-step instructions that came with your router? they are usually quite detailed and successful.

---

### Post by x64Jimbo on 2006-07-30
[QUOTE=califdon]have you followed the step-by-step instructions that came with your router? they are usually quite detailed and successful.[/QUOTE]
And usually quite tailored to Windows users. ;)

---

### Post by jbomber on 2006-07-30
My router is right next to me, I am able to connect with cables and wirelessly with the other computers in my house. It has WEP security, I put the hex code in and it works for a short while. I dont have a card, it is internal. I think it is this one "Intel (R) PRO/Wireless 2915ABG Network Connection" I have a Dell XPS M140.

---

### Post by x64Jimbo on 2006-07-30
Ok. Does it stay connected at short range?

---

### Post by jbomber on 2006-07-30
No, it dose not. Like I said before, Wireless works for a bit then drops completely reguarless of distance. I never left my seat, lol.

---

### Post by x64Jimbo on 2006-07-30
Ok so it sounds like some kind of configuration issue. Is the WEP shared or open?

---

### Post by Touch.Code on 2006-07-30
I am new to this, but can you download any drivers for it?

---

### Post by x64Jimbo on 2006-07-30
> **Touch.Code said:**
> I am new to this, but can you download any drivers for it?
IPW drivers are included in Ubuntu, which is why it works for a short while.

---

### Post by Touch.Code on 2006-07-30
You learn something new everyday! LOL

---

### Post by jbomber on 2006-07-30
I don't know if it is shared or open. When I made the passwords up, I did not see the words shared or open.

---

### Post by x64Jimbo on 2006-07-30
It's a configuration setting in your router. Check your wireless security page.

---

### Post by jbomber on 2006-07-30
Authentication Type: Auto? Is that right the other option for that is shared key.

---

### Post by x64Jimbo on 2006-07-30
Yeah that should be right. How are you setting up your interface?

---

### Post by Rich3077 on 2006-07-30
I recently had a problem with a different router and how I managed to fix it was change the security key to "shared" it was set to open by default.
Also it seems that WEP is easier to setup than WPA

---

### Post by Rich3077 on 2006-07-30
Almost forgot, after changing these settings you may need to reboot your modem and restart the PC

---

### Post by x64Jimbo on 2006-07-30
If you're going to use shared WEP, you need to add the option to your iwconfig...
iwconfig <interface> essid <SSID> key <key>** restricted**

---

