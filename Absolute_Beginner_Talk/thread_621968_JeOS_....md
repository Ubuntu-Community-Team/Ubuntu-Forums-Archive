---
title: "JeOS ..."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-24
JeOS has been a rather obscure concept for me to understand from what I have read.

Is JeOS intended to be the initial operating system you install on say a new PC?  

Then after JeOS is loaded, you install the VMWARE package using apt-get???

Or, do you download an "appliance" and it just runs?

Does JeOS receive automatic updates?

To summarize is this true:
Take a new PC without OS, install JeOS, then install VMWARE software, then install say Windows Server2003.  You will get a slight performance hit, but if you suffer say a motherboard failure, you can copy your virtualized Server2003 onto an entirely different JeOS'ed computer (different motherboard, different CPU, etc.)  or even to another VMWARE envioronment and it will all work - without the need to go through a Server2003 reinstallation and setup and configuration process?

Another question, how does this VMWARE "snapshot" feature work?

Carl

---

### Post by mark_k on 2007-11-27
Carl -

Keep in mind that I've only started playing with ubuntu JeOS myself, and haven't got it successfully running yet...

From what I've read, I think the 'JeOS' concept is one that's meant for a 'software appliance'. If you go with the theory that you'll have one 'computer' doing a single task (hosting an apache instance, or mysql, or mediawiki), having a couple GB of operating system gives you lots o' stuff sitting on disk that you really don't need. Mind you, the 'computer' can be physical or virtual, but you can make the same case for each.

The theory (as I understand it) is that for these purpose-built instances, you install the teeniest tiniest bit of operating system, and then layer your application stack on top of it.

Ubuntu JeOS looks at first blush like just another ubuntu variant - I assume it'll receive updates and the like, but probably through command-line apt-get mode instead of desktop mode (I assume the desktop gui is not present in these ubuntu flavor). If you look at other JeOS style appliance vendors (rPath comes to mind), they bundle a little management agent gizmo where you can login via a web browser and kick off updates for the jeos instance. Alternatively, I think puppet+JeOS will be a winning combination, at least in my server farm (such as it is).

Re. vmware's snapshot feature - it's pretty nifty. You get your vmware instance where you want it, and then push the 'snapshot' button. It freezes the state of the machine at that point in time. Then on you go messing about with things. At any point, you can revert back to that snapshot, and you're back to that pristine point in time.

- Mark

---

### Post by mark_k on 2007-11-27
First install of JeOS complete. I've got it as a guest operating system on a vmware server.

It weighs in at just under 500 MB disk size, for what that's worth.

About packages... It seems like an extension of the desktop -> server route, just a bit more limited in terms of the number of packages. But the /etc/apt/sources.list sure looks normal.  apt-get update and apt-get upgrade sure worked like normal.

I had some problems on the initial install, but this bug helped

[https://bugs.launchpad.net/ubuntu-jeos/+bug/163227](https://bugs.launchpad.net/ubuntu-jeos/+bug/163227)

1. Don't choose LVM
2. Choose 'buslogic' instead of 'lsilogic'.

Good luck.
- Mark

---

