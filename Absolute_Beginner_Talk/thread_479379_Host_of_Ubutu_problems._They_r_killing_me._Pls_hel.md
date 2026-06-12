---
title: "Host of Ubutu problems. They r killing me. Pls help!!!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by applegrew on 2007-06-20
I have Ubuntu Feisty installed. There are some problems that are driving me crazy. Pls help. They r as below.
 
**_[COLOR="SeaGreen"]1)[/COLOR]_** PPPoE connection is erratic.

I used the command **sudo pppoeconf** to configure my PPPoE connection. It then got me connected to net immediately, but after rebooting **pon dsl-provider** didn't work. Infact using **pon** never works. I only get successfully connected when I re-run **pppoeconf**. I also have rp-pppoe-3.8 installed. This is very very frustrating.

You can see the log  **plog** at [http://pastebin.com/932600]("http://pastebin.com/932600").


*Is there any GUI or atleast a reliable method to use PPPoE?*

**[COLOR="SeaGreen"]I have now configured my router to make PPPoE connections for me. This alternative is good, but, alas I couldn't get the wretched pppoe to work in ubuntu.[/COLOR]**

**_[COLOR="Red"]2)[/COLOR]_** KDE dependency error and much more :(
I wanted to install KDE on my Ubuntu Feisty. So I used the command **sudo apt-get install kde** but it generated a list of long error saying dependence error and 
[I]
GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)[/I]

I then tried (after reading somewhere) **sudo apt-get install kubuntu-desktop** and it too generated errors as it did for **apt-get install kde**. What is going wrong.

The error log is at [http://pastebin.com/932595]("http://pastebin.com/932595")

**_[COLOR="SeaGreen"]3)[/COLOR]_** After I enabled Desktop effects (I have disabled it now) in KDE, the Window Decoration seems to be using Metacity and when I change the decorations using KDE's panel then no change occurs. 

Also if I keep desktop effects enabled then when I click the close (cross) button in the title or anywhere on the title bar of the window then many times the click just 'goes through' to the window behind it! So, many times when I click the close button of currently visible widow but instead the one just behind it gets closed! This is very very frustrating.

[COLOR="SeaGreen"]**The Plastik Window Decoration is back after reboot. So this problem is partly resolved.**[/COLOR]

**_[COLOR="SeaGreen"]4)[/COLOR]_** And lastly can I make Ubuntu mount my NTFS partition with Write enabled? (It currently mounts it as Read Only).

**[COLOR="SeaGreen"]I have been suggested in this thread to use *ntfs3g*. I will give it a try after getting rid of problems 1 and 2. In particular 1. I think till then this problem is resolved.[/COLOR]**

I am at my wits end pls help.:(

---

### Post by LaRoza on 2007-06-20
> **applegrew said:**
> 


**_2)_** KDE dependency error and much more :(
I wanted to install KDE on my Ubuntu Feisty. So I used the command **sudo apt-get install kde** but it generated a list of long error saying dependence error and 
[I]
GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)[/I]

I then tried (after reading somewhere) **sudo apt-get install kubuntu-desktop** and it too generated errors as it did for **apt-get install kde**. What is going wrong.


**_4)_** And lastly can I make Ubuntu mount my NTFS partition with Write enabled? (It currently mounts it as Read Only).


For KDE:
```
sudo aptitude install kde-core
```

For NTFS, no. You have to get ntfs3g for Writing.

---

### Post by applegrew on 2007-06-20
> **LaRoza said:**
> For KDE:
```
sudo aptitude install kde-core
```

For NTFS, no. You have to get ntfs3g for Writing.
aptitude is crashing. When I use this command I get Segmentation fault that's all and nothing else.

---

### Post by LaRoza on 2007-06-20
Can you install anything else with aptitude or apt-get?

You can use apt-get instead of aptitude for the command if it works, I just usually use aptitude.

---

### Post by applegrew on 2007-06-20
> **LaRoza said:**
> Can you install anything else with aptitude or apt-get?

You can use apt-get instead of aptitude for the command if it works, I just usually use aptitude.
I have tried using aptitude only twice or thrice (for installing kde) and it crashed all these times.

---

### Post by LaRoza on 2007-06-20
Try it with something else.

---

### Post by applegrew on 2007-06-20
> **LaRoza said:**
> Try it with something else.
ok then I will have to reboot into Linux. Will report in a moment. And is anybody here to address my Linux woes?

---

### Post by sailor2001 on 2007-06-20
if you have all your repositories checked (synaptics) you can check KDE there and it will install with no problems

---

### Post by Happy_Man on 2007-06-20
You can' t use the desktop effects in KDE. You either have to use the KWin (ergo, no wobbly) or install Beryl (like Compiz, only with more options, including wobbly, blur effects, more minimize/maximize effects, etc.). 

Aptitude giving off core dumps, is, quite frankly, scaring the hell out of me. Aptitude is like, *the* most reliable app ever. Times like this make me miss aysiu. Anyway, did you check your CD for errors or get an md5 checksum? That's the only reason I can think of that would cause *aptitude* to crash.... scary. [shudders]

---

### Post by applegrew on 2007-06-20
Hi I tried using apt-get to uninstall and then re-install it, but during both the process apt-get tried to install the failed pacakges again (and it yet another time failed).


**-----------**As for the internet connection when I tired using pppoeconf then it seems I got connected to net (or atleast to my ISP) successfully as the following **plog** log hints

[I]Jun 20 18:39:31 applegrew pppd[7628]: CHAP authentication succeeded: Authentication success,Welcome!
Jun 20 18:39:31 applegrew pppd[7628]: CHAP authentication succeeded
Jun 20 18:39:31 applegrew pppd[7628]: peer from calling number 00:E0:FC:45:2E:77 authorized
Jun 20 18:39:31 applegrew pppd[7628]: not replacing existing default route via 192.168.1.1
Jun 20 18:39:31 applegrew pppd[7628]: Cannot determine ethernet address for proxy ARP
Jun 20 18:39:31 applegrew pppd[7628]: local  IP address 59.94.72.170
Jun 20 18:39:31 applegrew pppd[7628]: remote IP address 59.94.72.1
Jun 20 18:39:31 applegrew pppd[7628]: primary   DNS address 218.248.240.79
Jun 20 18:39:31 applegrew pppd[7628]: secondary DNS address 218.248.240.135[/I]

but none of the programs could access the internet. Pls help!!!

---

### Post by applegrew on 2007-06-20
and yes I have ran **apt-get check** inumerable times. It shows no problem but my problems persists.

---

### Post by meep_meep on 2007-06-20
> **applegrew said:**
> 
**_4)_** And lastly can I make Ubuntu mount my NTFS partition with Write enabled? (It currently mounts it as Read Only)(


Search for 'ntfs-3g' in add/remove programs.

---

### Post by applegrew on 2007-06-20
People pls help me fix problem 1 about the erratic PPPoE connection.

---

### Post by applegrew on 2007-06-20
I have at last resolved by net problem. I am posting now from my Linux Box.:D

Alas the PPPoE couldn't be resolved, but I tried my alternate. I have now configured my router to make the PPPoE connection for me. Now I have no problem connecting. If there are any unfortunate beings like me then I have prepared a small how-to on way to configure Huawei SmartAX MT882 (my router model) at [http://applegrew.blogspot.com/2007/06/configuring-your-huawei-smartax.html]("http://applegrew.blogspot.com/2007/06/configuring-your-huawei-smartax.html").

---

