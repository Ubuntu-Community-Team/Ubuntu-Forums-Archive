---
title: "network-manager...location?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-03-04
Hi...

Had a quick question:

I have been reading the threads on network manager. They seem to say that it is located at Systems>Preferences

I checked via Synaptic and found that the network-manager packages are indeed installed. The Add/ Remove also shows that network-manager is installed. But I can't seem to find it anywhere!

I downloaded Wifi-Radar and it shows up under Apps>Internet. Also under Apps>Internet, something called VPN Connection manager (generic) shows up but when I click on it nothing happens.

From the network-manager site, l saw the images and it should show something like what the Wifi Radar displays when the latter is clicked.

So, my question is if network-manager is indeed installed, then where is it?

Thanks

BTW, my wireless works fine (well, I am keeping my fingers crossed)

My wireless card is the Intel 3945 A/B/G  and I somehow did not have to mess around with ndiswrapper even though while initially setting up, I was advised on some of the posts here to do so. As I mentioned in those earlier posts, the wireless somehow resolved itself - at least when I am at home. It does not work on my campus - but then I had no way of picking up the signals. I am on campus tomorrow and will be trying Wifi-Radar then.

Can you folks set me straight on this?

Again, thanks

---

### Post by igknighted on 2007-03-04
Network manager is not a default app... you need to install it via synaptic

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> Network manager is not a default app... you need to install it via synaptic

Hi...

But it's already installed!

---

### Post by igknighted on 2007-03-04
What happens then if you type 'network-manager' in the terminal?  Or if that doesn't work, 'gksudo network-manager'

Scratch that... try "gksudo nm-applet"

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> What happens then if you type 'network-manager' in the terminal?  Or if that doesn't work, 'gksudo network-manager'

In the first instance (typing network-manager) it says command not found and in the latter instance (gksudo network-manager) it return me to my user prompt x@y-laptop...!

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> What happens then if you type 'network-manager' in the terminal?  Or if that doesn't work, 'gksudo network-manager'

Scratch that... try "gksudo nm-applet"

Oh oh!

Here is what I get:

(nm-applet:6632): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by igknighted on 2007-03-04
> **kristalsoldier said:**
> Oh oh!

Here is what I get:

(nm-applet:6632): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Yeah, that should just be debug info in the terminal, then the app should start up. 

EDIT: It probably opened to the taskbar, see if there is a new icon in the upper right corner.

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> Yeah, that should just be debug info in the terminal, then the app should start up. 

EDIT: It probably opened to the taskbar, see if there is a new icon in the upper right corner.

Nope! Nothing here. However, there are 2 network connection icons. One is the one that is active, the other one is not and has an exclamation mark against it.

But the interface of the active network connection only shows my current home network, while when I activate wifi-radar, it shows my neighbour's wifi connection (secured!) too!

---

### Post by igknighted on 2007-03-04
Thats what mine shows up as (a network connection icon).  Right click and choose "about" and it will tell you it is network manager.  How to do wireless with it?  Lord only knows (well, im sure many others here do to, I am not one of them).  I always use wifi-radar on my laptop and love it, and my desktop which I just installed network-manager on has no wireless.

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> Thats what mine shows up as (a network connection icon).  Right click and choose "about" and it will tell you it is network manager.  How to do wireless with it?  Lord only knows (well, im sure many others here do to, I am not one of them).  I always use wifi-radar on my laptop and love it, and my desktop which I just installed network-manager on has no wireless.

Well, when I right-click on the icons, it says it is 'Network Monitor'.
 Yup...will try out the wifi radar tomorrow...and thanks for your attention.

---

### Post by igknighted on 2007-03-04
Interesting, this is what mine says:

---

### Post by kristalsoldier on 2007-03-04
> **igknighted said:**
> Interesting, this is what mine says:

Now this is getting really wierd...

I mentioned earlier i have 2 icons. One is active and the other is not - it is the one with the 'exclamation mark'. When I right click the first one it say 'network monitor', but when I right click the second, it says 'network applet' like the image you sent.

Let me see if I can post an image here. Never done it before.

---

### Post by kristalsoldier on 2007-03-04
You see what I mean?

---

### Post by kristalsoldier on 2007-03-04
I'd better get to bed! Else no classes tomorrow!:) 
Thanks for working with me...I'll pick it up tomorrow...err...later today, I mean!

---

### Post by igknighted on 2007-03-04
Yeah, I see the two.  Does it tell you what the "!" is for?

---

### Post by kristalsoldier on 2007-03-05
> **igknighted said:**
> Yeah, I see the two.  Does it tell you what the "!" is for?

If I hover the cursor over the one with the exclamation mark it says 'No Network connection'!

---

### Post by bngn on 2007-03-05
I don't have network-manager...I think, but i need it, how do I get it?

---

### Post by kristalsoldier on 2007-03-05
> **bngn said:**
> I don't have network-manager...I think, but i need it, how do I get it?

AFAIK....Go to Systems>Admin>Synaptic and download it from there.

---

### Post by kristalsoldier on 2007-03-05
OK. Here is an update. I am on campus. Still don't know where network-manager is or what it is doing....but hey...using Wifi-Radar, I am connected and am posting to this forum!

So, there! Thanks folks for all your help!

---

