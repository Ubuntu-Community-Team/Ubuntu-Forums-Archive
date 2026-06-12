---
title: "Ubuntu 14.04 On Macbook 4,1 can see WiFi but won't connect"
date: 2014-09-27
forum: Apple Hardware Users
---

### Post by Kale_Freemon on 2014-09-27
Hello!

So, I have a Macbook 4,1 that I would like to run Ubuntu 14.04 on. I already have it installed (accidentally killing OS X in the process). Everything seems to work, except that I cannot connect to the wifi successfully.

The Macbook can see the WiFi connections I have in my house, but it won't connect to either one of them, even with the correct passkeys (I checked them numerous times). The WiFi card is a Broadcom BCM4321. The driver is already installed via bcmwl-kernel-source.

I have searched google for the past two or three hours with no success. The closest I got was getting it to connect to the WiFi by setting the connection up with a static IP address. I know I set it all perfectly as I checked it with my other Ubuntu install that also uses a static IP adress. But I still couldn't get the Mac too connect to the internet.

Anyone have any solutions, because I'm getting tired of shooting in the dark.

Thanks!

EDIT: Strangely enough, shortly after posting this, the darned thing actually connected and seemed to work. I am rebooting it now to see if it will still work.
EDIT 2: After reboot, it did connect after a second attempt, but won't actually go out to the internet.
EDIT 3: Currently installing latest updates to the system via an ethernet cable. Hopefully this will remedy the issue. If anyone else has a potential solution, I am open to trying it. Thanks again!
EDIT 4: Updates did not fix the issue.
EDIT 5: So, I looked further and further into the problem, and also continued to research it as much as possible. During my search, I finally came upon a thread, which I'll link here, that had a post with instructions that solved my problem. The link is: [http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784](http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784) - Hopefully this will help other users of this particular WiFi card.

---

### Post by este.el.paz on 2014-09-27
@K_F:

Just stopping by to say howdy.  Glad you figured it out . . . looked like Bucky Ball had a link to the wiki . . . it's interesting how from machine to machine the "additional drivers" app will work perfectly . . . and other times not.  

e.e.p.

---

### Post by Kale_Freemon on 2014-09-30
> **este.el.paz said:**
> @K_F:

Just stopping by to say howdy.  Glad you figured it out . . . looked like Bucky Ball had a link to the wiki . . . [I][B]it's interesting how from machine to machine the "additional drivers" app will work perfectly . . . and other times not.  
[/B][/I]
e.e.p.

Ya. I've never needed to use the app before installing on my Macbook. Everything just worked out of the box. But, with the Macbook, it didn't impress me. Luckily I was able to find instructions after nearly giving up. I don't as much time to look for solutions to problems as I used to. Gotta work now and spend time with my wife.

But, I appreciate the howdy. :) Howdy back! Everything else on the install is working great.

---

### Post by este.el.paz on 2014-09-30
> **Kale_Freemon said:**
> Ya. I've never needed to use the app before installing on my Macbook. Everything just worked out of the box. But, with the Macbook, it didn't impress me. Luckily I was able to find instructions after nearly giving up. I don't as much time to look for solutions to problems as I used to. Gotta work now and spend time with my wife.

But, I appreciate the howdy. :) Howdy back! Everything else on the install is working great.

@K_F:

As the machines get "older" it seems to take more effort to get the newer OSs running . . . never needed an xorg.conf file for my PPC iBook, but with the 14.04 upgrade I had to add one . . . not a major deal, but, does take time . . . and agreed, there are other things in life that need our attention . . . .  : - )  Looks like the iBook is now taking a dive . . . unfortunately, which would take time or money to maintain . . . .  : - 0

e.e.p.

---

### Post by Kale_Freemon on 2014-09-30
> **este.el.paz said:**
> @K_F:

As the machines get "older" it seems to take more effort to get the newer OSs running . . . never needed an xorg.conf file for my PPC iBook, but with the 14.04 upgrade I had to add one . . . not a major deal, but, does take time . . . and agreed, there are other things in life that need our attention . . . .  : - )  Looks like the iBook is now taking a dive . . . unfortunately, which would take time or money to maintain . . . .  : - 0

e.e.p.

The problem with iBooks these days is that they are running on technology that has been considered dead for a while now. Canonical pretty much dropped all support for it, leaving it up to the community to manage a PPC port of Ubuntu.

My Macbook, on the other hand, isn't very old at all. It's an early 2008. Everything else worked perfectly, except the WiFi. I'd say that is pretty darn good still, even though my other laptop works 100% out of the box. Then again, my other laptop also uses an Atheros while the Macbook uses a Broadcom. And I've seen Broadcom cards be a slight pain in other distributions as well on even newer machines.

---

### Post by este.el.paz on 2014-09-30
> **Kale_Freemon said:**
> The problem with iBooks these days is that they are running on technology that has been considered dead for a while now. Canonical pretty much dropped all support for it, leaving it up to the community to manage a PPC port of Ubuntu.

My Macbook, on the other hand, isn't very old at all. It's an early 2008. Everything else worked perfectly, except the WiFi. I'd say that is pretty darn good still, even though my other laptop works 100% out of the box. Then again, my other laptop also uses an Atheros while the Macbook uses a Broadcom. And I've seen Broadcom cards be a slight pain in other distributions as well on even newer machines.

@K_L:

Indeed, PPC is dropping off the radar screen for many distros, kind of a shame, my '02 era iMac is running fine for the most part . . . but getting linux to run on it was a bit challenging and the newer upgrades are likely not viable for it . . . in the time/cost/benefit ratio of time management . . . .  Even my '10 MBPro is starting to take some "attention" on the upgrade front . . . might be staying with the 14.04 LTS for the extended ride . . . .

e.e.p.

---

