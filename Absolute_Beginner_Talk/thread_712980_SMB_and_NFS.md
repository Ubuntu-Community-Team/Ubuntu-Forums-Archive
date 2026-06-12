---
title: "SMB and NFS"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2008-03-02
Hi I just installed a fresh copy of ubuntu and I need to copy things from a Windows computer.

When I click on shared folders the following pops up:

Sharing Services are not installed, there is two tickboxes.

Ok so I select both and click on "Install services", but then the same window (Sharing servic.. not installed) pops up again everytime you click on "Install Services".

Is their any other way of installing this NFS and SMB ?

---

### Post by Happy_Man on 2008-03-02
> **ThRixXx said:**
> Hi I just installed a fresh copy of ubuntu and I need to copy things from a Windows computer.

When I click on shared folders the following pops up:

Sharing Services are not installed, there is two tickboxes.

Ok so I select both and click on "Install services", but then the same window (Sharing servic.. not installed) pops up again everytime you click on "Install Services".

Is their any other way of installing this NFS and SMB ?

Just open a terminal (Applications --> Accessories --> Terminal) and run the code ```
sudo apt-get install samba
```

---

### Post by northern lights on 2008-03-02
[http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm]("http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm")
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

### Post by Mud.Knee.Havoc on 2008-03-02
I hate to toss another link for you onto the pile, but it's one that will help you install or configure a ton of useful things: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy").  This is the "Ubuntu Guide" for Gutsy (7.10), but different version guides are there, too.

---

