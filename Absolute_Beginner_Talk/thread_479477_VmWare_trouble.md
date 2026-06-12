---
title: "VmWare trouble"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ghost_ryder35 on 2007-06-20
Ok, heres the deal.  Got my Fedora7, Fedora6, Ubuntu7,Windows XP,Windows Vista all in VM's.  My Ubuntu7 (Vmware tools installed), Windows XP(VmWare tools installed) can get to the internet no problem.  However Fedora regardless of which version is a little bit of trouble.  They both have VMware tools installed but can not access web pages.  Both are set to NAT, and both can ping any web address ([www.yahoo.com](www.yahoo.com), [www.google.com](www.google.com)) so I am getting DNS and I am getting results from my pings but when I go to go to a website they time out and dont display.  I have been working on this for days now.  Port forwarding is set up on the router correctly, holes in the firewall are correctly set for VmWare ports (902,904,8222,8333 both UDP,TCP) on both the host and the guest and nothing is working.  I even tried completly turning the firewall off on the guest and the host and the router and still nothing.  Any thoughts would be great!  Here is a screen shot of the pings working and the website timing out.

[[IMG]http://img488.imageshack.us/img488/1087/testfa0.th.jpg[/IMG]](http://img488.imageshack.us/my.php?image=testfa0.jpg)

---

### Post by ghost_ryder35 on 2007-06-22
bump, nobody knows?

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

### Post by diggity on 2007-06-24
ghost_ryder35: Just a guess, but it might be an SELinux issue. If I were you, I'd visit the Fedora forums (if you haven't already) or disable SELinux in Fedora altogether.

---

### Post by dannymichel on 2007-06-24
> **diggity said:**
> ghost_ryder35: Just a guess, but it might be an SELinux issue. If I were you, I'd visit the Fedora forums (if you haven't already) or disable SELinux in Fedora altogether.
No ideas about my issue?

---

### Post by ghost_ryder35 on 2007-06-24
I totally overlooked SElinux.  I will try disabling it!  Thanks for the input!!!

---

### Post by Dedoimedo on 2007-06-24
What driver do you use for network - vlance?
Dedoimedo

---

### Post by ghost_ryder35 on 2007-06-24
i think its vlance, let me power it up and double check... is vlance bad?

---

### Post by ghost_ryder35 on 2007-06-24
ok i was smoking a lot of crack.  disabling selinux does not help at all (selinux is a file rights stuff kinda like the new ntfs) it seems it was just dumb luck that when i disabled it the internet worked in fedora.  the internet works everyonce in a while, however I can always ping.  I wish I knew what the f was going on.  It's probally cause of my cheap router that I have.  not forwarding the ports correctly all of the time :)

---

### Post by cool_mast on 2007-07-02
I have installed vmware,but dont know how to add operating system to it....I runned vmware and created virtual machine on my disk.Now when I run this machine by selecting option then blank screen comes and after some time it goes...what should I do???

---

### Post by Dedoimedo on 2007-07-02
Hello,
Your virtual machine is empty. The fact you created an X machine does not mean there's the X operating system on it. You'll have to install an operating system into it. Just like you would a normal OS. Pop a CD/DVD into the tray and then install (or boot to a live session and then install).
Dedoimedo

---

