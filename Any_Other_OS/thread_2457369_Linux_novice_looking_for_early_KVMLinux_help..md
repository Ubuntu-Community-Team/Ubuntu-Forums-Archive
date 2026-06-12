---
title: "Linux novice looking for early KVM/Linux help."
date: 2021-01-31
forum: Any Other OS
---

### Post by jmgmr2 on 2021-01-31
Hi, I'm a novice to Linux trying to tackle a KVM server that I'll use for school and home projects.  I hope no one minds if I ask some questions (I don't mind if anyone just gives me the location of the answers, rather than the answers themselves...but I'm a bit out of my depth).

The server is the best I could afford:  
3700x, 32 GB RAM, 2 TB HD, Radeon 570, USB Wireless adapter.  I've enabled svm in the BIOS and confirmed hardware acceleration and CPU compatibility.

I couldn't wrap my newbie head around a Userver CLI install so I opted for a stripped base-desktop install. 

Question 1:  Will using a stripped down Udesktop install lead to security or performance issues for me?  

I installed KVM and it's running a Kali instance on top.  It runs without issues but it does show a tiny bit of response lag in Virt Manager.  I assigned 1 CPU and 2 GB of RAM.

Question 2:  For Kali, SIFT, Ubuntu, GhostOS, and Windows 10, what kind of recommended hardware CPU/RAM assignments do you all recommend.  I know the recommended total for Kali is 1/2048 but it seems a bit sluggish.  I was wondering if it was a GPU rendering issue I had misconfigured or if maybe it was undernourished with resources.

To secure my baby Udesktop server, I installed the following/made the following changes:

    A.  Installed openSSH. (and denied root logon)
    B.  Installed CPU-X and PSensor for hardware information.  (the box CPU seems to be running a bit hot at 35-52 C on idle to regular tasks).
    C.  Installed GUFw.  Graphical Uncomplicated Firewall.
    D.  Autoremoved junk.
    E.  Installed Rootkit Hunter and tied it to ClamAV.
    F.   Installed LMD and updated it.
    E.  Changed the root pwd.
    F.  Locked the GRUB loader with a pwd.  Updated the GRUB.

Question 3:  Apart from locking down ports, what else am I missing on the security end of the hypervisor?  I have long passwords for root and superuser (over 16 characters each).  Will installing all these things kill my performance?  Any other advice to lock down my hypervisor?  (free options and links to the resources please if you have them).

Question 4:  I started this process because I wanted to run VMs faster and 24/7 vs using VBox which is running slowly on an older desktop I had.  Can I expect this to be the case through Virt Manager?  Could I install Virt Manager on Windows (I've heard it's scary) or Mac (also scary) and have it be competitive with VBox?

I know I've asked for a bit but there's a lot of talent and knowledge on here and as a Mac aficionado, I'm hoping that someone will help a cousin OS user. :)

---

### Post by oldfred on 2021-01-31
To get you started until those who know the topic.

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

### Post by Tadaen_Sylvermane on 2021-02-01
> [COLOR=#000000]Question 1: Will using a stripped down Udesktop install lead to security or performance issues for me?

Not really. Just more stuff running that can theoretically break and destabilize the system. Is on reason why servers typically don't have a DE installed.

> [/COLOR][COLOR=#000000]Question 2: For Kali, SIFT, Ubuntu, GhostOS, and Windows 10, what kind of recommended hardware CPU/RAM assignments do you all recommend. I know the recommended total for Kali is 1/2048 but it seems a bit sluggish. I was wondering if it was a GPU rendering issue I had misconfigured or if maybe it was undernourished with resources.

[/COLOR][COLOR=#000000]Based on the rest of your post you are doing everything with Virt-Manager? In that case it's going to be sluggish no matter what. Virt-manager is not much different than vnc for gui, and will only run as fast as a basic network connection. Even over gigabit it will run like crap. I had a gaming vm running on my desktop at one point with Windows 10 installed and I could play world of warcraft through it. I used Steam in home streaming to run it on the same machine to another monitor. I also could plug a monitor directly into the video card and it ran perfect. But Virt-manager was about useless other than seeing if it would actually load.

[/COLOR]

---

