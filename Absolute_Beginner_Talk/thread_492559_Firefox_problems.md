---
title: "Firefox problems"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by shyamsg on 2007-07-04
Hi,

I have the HP laptop dv6345us, intel dual core with 1 gig ram and intel 945 graphics card -- with Feisty. Now whenever i open the site msn.co.in with firefox, firefox hangs, I dont know what the problem is.I tried removing all the plugins and it still gives me the error. Any help is appreciated. This happens with some other sites as well, but this site consistently gives me trouble.

TIA
Shyam

---

### Post by freebird54 on 2007-07-04
No idea what you're running into - site works fine here.  What version of FF are you running? Are you accessing from dial-up?  For that matter - FROM where are you attempting access?  Sounds like a strange one - but not directly FF's fault is my guess....

---

### Post by jimrz on 2007-07-04
> **shyamsg said:**
> Hi,

I have the HP laptop dv6345us, intel dual core with 1 gig ram and intel 945 graphics card -- with Feisty. Now whenever i open the site msn.co.in with firefox, firefox hangs, I dont know what the problem is.I tried removing all the plugins and it still gives me the error. Any help is appreciated. This happens with some other sites as well, but this site consistently gives me trouble.

TIA
Shyam

just a guess, but have you istalled flash and the ff plugin fo it?

---

### Post by shyamsg on 2007-07-04
> **freebird54 said:**
> No idea what you're running into - site works fine here.  What version of FF are you running? Are you accessing from dial-up?  For that matter - FROM where are you attempting access?  Sounds like a strange one - but not directly FF's fault is my guess....

I think you are right about that. I tried opening the site in OPERA and that had the same trouble. To answer your questions, I am using ff 2.0.0.4. I am accessing it from Michigan using cable internet.

shyam

---

### Post by shyamsg on 2007-07-04
> **jimrz said:**
> just a guess, but have you istalled flash and the ff plugin fo it?

You might be onto something... I have the flash player and the plugin installed but whenever I access any page with active flash content on it, FF seems to hang. I will check into it and let y'all know.

TY
shyam

---

### Post by freebird54 on 2007-07-04
This thought is from way out in left field (and I keep getting told that I think it's the solution to everything:) ) but I wonder if you have ipv6 disabled on your system?  I did run into some oddities with MS sites till I killed it on my system..  

A quick test for that is to type  **about:config** into the address line of FF, then search for (enter in the filter line) ***network.dns***.  This will bring up the option
***network.dns.disableIPv6*** for you to ensure that is set to TRUE.  Let's hope... :)

---

### Post by atria on 2007-07-04
If it still doesn't work after disabling IPv6, try doing a full uninstallation of firefox and install the flash plugin directly from [www.adobe.com](www.adobe.com) instead of using the one from the ubuntu repositories.

```
sudo aptitude purge firefox
```
then to reinstall:
```
sudo aptitude install firefox
```

---

### Post by shyamsg on 2007-07-04
ipv6 is disabled.. i am going to reinstall firefox and see what that gives me.. wish me luck

---

### Post by freebird54 on 2007-07-04
***_[SIZE="5"]luck![/SIZE]_***

---

### Post by kerry_s on 2007-07-04
install adblock plus with the easy list subscription, that will block all those ad's.
i have no problems and all the ad's are blocked.

---

### Post by Wiebelhaus on 2007-07-04
I'm seeing allot of Firefox issues as of late , try [swiftfox]("http://getswiftfox.com/") it is firefox , just tweaked.

---

### Post by shyamsg on 2007-07-05
I had flash plugin installed in my local directory. I removed the plugin from the local .mozilla/plugin directory and this site and others that were giving me trouble started working fine, but obviously without the flash content being displayed. I am going to install the flash plugin directly from adobe and see what happens. Thanks all... will update

---

### Post by shyamsg on 2007-07-05
i reinstalled the firefox plugin... but the problem persists... for the time being, I just installed adblock.. so that site works fine, but I have trouble whenever I want to view flash content. Will try some other stuff...

---

