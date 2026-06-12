---
title: "Live CD boot,can't surf internet."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by jerry2 on 2006-10-18
Boot from ubuntu desktop 6.06 CD with [COLOR="Red"]no[/COLOR] HD install.

adsl modem already set to auto-dial,and DHCP server.

ubuntu can get correct IP,and ping any website is OK.

**[COLOR="Red"]question:[/COLOR]**
   Can't open any website with firefox,even telnet is fail.

any advise? Is that HD installation necessary?

---

### Post by Laptop1 on 2006-10-18
Get slax ubuntu is noob.

---

### Post by jerry2 on 2006-10-18
website? pls

---

### Post by ReaderRat on 2006-10-18
> **Laptop1 said:**
> Get slax ubuntu is noob.
Slax (Slackware is not near as easy and forgiving as Ubuntu. If you would like to check your hardware to see if it runs, please post what your computer is composed of....RAM laptop or desktop, etc.

---

### Post by ReaderRat on 2006-10-18
> any advise? Is that HD installation necessary?
A full installation is not required unless you want full functionality of Ubuntu. Running from a Live CD limits what you can do with Ubuntu.

---

### Post by jordanmthomas on 2006-10-18
> **Laptop1 said:**
> Get slax ubuntu is noob.
> **also from same poster:**
is it hard to save to hardrive and not screw up my other OS?

If that ain't the pot callin' the kettle black.

For OP, in firefox go to about:config
In the filter bar start typing ipv6
When it comes up, turn off ipv6 and see if that helps

---

### Post by clouduser on 2006-10-19
my situation is totally different..

my Live CD boot, can surf internet..
everything is fine..
DHCP is turned on, and i get my ip.

but after i install ubuntu into my hdd,and boot with hdd,
i can't surf internet.
i don't even have an ip address when i check my ip in terminal..
DHCP is turned on, but just i din't get my ip.

does anyone know what's my problem?
by the way, my computer is on lan..(in a office)
my colleague computer is using ubuntu too,
but he has no problem..
i install the same way as he did..

---

### Post by odiseo77 on 2006-10-19
> **clouduser said:**
> my situation is totally different..

my Live CD boot, can surf internet..
everything is fine..
DHCP is turned on, and i get my ip.

but after i install ubuntu into my hdd,and boot with hdd,
i can't surf internet.
i don't even have an ip address when i check my ip in terminal..
DHCP is turned on, but just i din't get my ip.

does anyone know what's my problem?
by the way, my computer is on lan..(in a office)
my colleague computer is using ubuntu too,
but he has no problem..
i install the same way as he did..

Hi, a friend of mine had exactly the same problem you're reporting. If  you're using a Davicom ethernet adapter, that could be the problem. '/sbin/lspci' should tell you wich network adapter you're using. If it's Davicom, then follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=186430&highlight=davicom") and it should work.

---

### Post by clouduser on 2006-10-19
maybe it's your proxy setting problem??
try this 
Edit > Preferences > Connection Settings > Auto Detect Proxy Settings for this network.

---

### Post by jordanmthomas on 2006-10-19
What kind of ethernet card do you have clouduser?  There are several that work on the LiveCD but need configuring after installation.

---

### Post by clouduser on 2006-10-19
thanks for trying to help..
it's company computer, i also don't know what kind of ethernet card in this computer. can i check it in ubuntu?
'/sbin/lspci' <-- i found sbin folder in the file system folder, but i didn't see lspci??
thanks again for you all

---

### Post by jordanmthomas on 2006-10-19
just type lspci in a terminal, it will run
(it's actually in /usr/bin)

---

### Post by clouduser on 2006-10-19
thanks to odiseo77 and jordanmthomas, thank you very much..
i solved my problem already, i check my ethernet, and it is Davicom semiconductor ethernet..
i follow the method in the link given by odiseo77, and now i am able to online here..
thanks to both of you very much. i really appreciate it..

---

### Post by jerry2 on 2006-10-19
> **jordanmthomas said:**
> If that ain't the pot callin' the kettle black.

For OP, in firefox go to about:config
In the filter bar start typing ipv6
When it comes up, turn off ipv6 and see if that helps

I turn off IPv6 in firefox,but nothing change.
the firefox statusbar show something like this: "Connecting to [www.google.com](www.google.com) ..." and return an error later.

> **clouduser said:**
> maybe it's your proxy setting problem??
try this 
Edit > Preferences > Connection Settings > Auto Detect Proxy Settings for this network.

I don't think it's a proxy problem, I'm home, no use any proxy.
repeat: [COLOR="Red"]can[/COLOR] ping any website but can't show any page in firefox.

---

### Post by Bartender on 2006-10-19
Does Synaptic Package Mgr work?

---

### Post by jerry2 on 2006-10-19
> **Bartender said:**
> Does Synaptic Package Mgr work?

it can run,but can't download anything.

---

### Post by jerry2 on 2006-10-21
On my old PC, Unbuntu runs well, and everything is ok include internet.

I'll try to figure out the internet problem on new PC.

---

