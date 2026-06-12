---
title: "Install stalls"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by azoutback on 2007-05-13
I am trying to install via the LiveCD, after much work I was able to get my system to boot from the CD.  After it boots I get the setup menu.  If I select the first option to run/install Ubuntu it initializes a couple files then I end up with a black screen with a flashing (but non responsive cursor) in the upper left corner.  This also happens if I select the Check CD option.  Could it be bad ISO file, or a bad burn (did burn at 4X)?  Thanks.

---

### Post by taurus on 2007-05-13
What's the spec of your machine?  Could be a problem with your graphic card.  Try using the alternate CD if you want to install it on your machine.

---

### Post by oilchangeguy on 2007-05-13
please advise the version of ubuntu you're using. and your systems specs.

---

### Post by quinnten83 on 2007-05-13
Could also be lack of patience :lolflag: .
when installing ubuntu, i also have to wait like 5 whole minutes before it reacts and starts installing. I should know, I installed the damn thing on 5 (virtual) machines, trying to test it before i was sure enough to install it on my laptop.
Try the patience thing, if that does not work, aks for techie help here.

---

### Post by azoutback on 2007-05-13
@Taurus...Yes, I suppose Specs would be helpful and it is Ubuntu 7.04...
[LIST]
[*]AMD Athlon XP 1800+
[*]768 MB RAM
[*]ATI Radeon 7200 Series w/64 MB RAM
[*]HDDs: 30 GB, 120 GB (will be dedicated to Ubuntu and 160 GB
[/LIST]

I have not tried the alt CD yet, what is the difference?  I also noticed there seems to be problems with these ATI video cards.

@quinnten83, could be.  When it got to that point I assumed the system had froze

---

### Post by taurus on 2007-05-13
Here's more info about alternate CD version, [http://ubuntu-releases.cs.umn.edu/7.04/](http://ubuntu-releases.cs.umn.edu/7.04/).

---

### Post by azoutback on 2007-05-13
Okay, I'll try that later I am getting: Sorry! The server is far too busy to serve your request.  Thanks.

---

### Post by Towerblock on 2007-05-13
I am a complete noob to linux but two days ago I decided I wanted to try loading ubuntu on a cpl of machines. I got 7.04 Feisty Fawn and it installed on one Dell Latitude 600 P4 laptop with no probs at all. Everything works beautifully, wifi etc. 

The other laptop is an old Dell Latitude C400..these are the little ones that you attach an external CD drive to. It would not install at all, black screen etc. I almost gave up and discovered that you can download an alternate install disk. Definately do this! Used that and it installed perfectly..I am amazed that Ubuntu runs so well on a little P3 machine with 256 megs ram, and a 20gig drive. Wifi, everything works beautifully.

As a note though, what someone else said is true...when you put the CD in and things go black, leave it alone...mine went black for what seemed like 8 minutes or so during many periods of the install..so, just give it time even when it looks dead...:) Anyway, good luck, its worth it!

---

### Post by azoutback on 2007-05-18
Okay, I was able to successfully download, burn and install the alternate.  I played with it a little and now appear to have broken it!  When every it tries to boot into Ubuntu it just sits there with a black screen displaying "Starting..."  if I try to do the recovery/rescue option it does a bunch of stuff then stops after "Enabling IO-APIC IRQs".:confused:

Also, is it normal now for the drive that Ubuntu partitioned not to show up in Windows Explorer?  One more thing, when it *was* working, I could get my Windows XP Drive to show up, but I couldn't get into my other drive (it is a NTSF file system).

Thanks

---

### Post by azoutback on 2007-05-19
Okay once I disabled APIC in the BIOS, Ubuntu boots fine.

---

