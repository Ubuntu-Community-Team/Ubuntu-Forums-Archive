---
title: "Installing all repositories"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by doctapeppa on 2007-01-21
Hello, first post. 

Is there a reason why all available repositories are not installed/enabled by default? Is there a drawback to having all of then enabled? Does doing this take up system memory or hard drive space somewhere; or maybe just make searching through them slower?

I have a fresh install of Dapper Drake and all went well. The first thing I did though, was install all of the "updates" that popped up on the upper right corner (windows habit) and I also clicked checkmarks enabling all of the repositories. 

My problem is, Firefox runs really slow now. It's really the only thing I've tried using, so not sure if it's a system wide slow down or what. I don't know if it is caused by having enabled all of the repositories or if the prob was caused by one or more of the updates. that's all I have changed from the fresh install. Right after install (and before the changes I described above) I surfed around a bit with firefox and it was working fast. 


P4 2.6
2 Gig Ram
ATI X800

Thanks.

---

### Post by zerhacke on 2007-01-21
There are third party repositories that can cause conflicts with the regular repository if enabled.  They'll cause problems.  Or so the story goes... I've never encountered any problem with any of the repositories I use.

The Firefox issue, though, I know what's causing that.  IPv6 is enabled in K/E/X/Ubuntu by default and nobody uses IPv6 yet.  To disable it and speed Firefox up, follow the steps below.

Open a terminal and type 

```
sudo gedit /etc/modprobe.d/aliases
```

Find the line: alias net-pf-10 ipv6

Edit this to: alias net-pf-10 off

Save the file and reboot

---

### Post by doctapeppa on 2007-01-21
Great! I'll try that out, thanks.

---

### Post by Shatrat on 2007-01-21
I think the reason multiverse and universe repositories are commented out in the sources.list by default is that there are many packages that have legal or ethical conflicts with the debian project and they dont want to be considered part of the Default Ubuntu installation.

As for 3rd party repositories, keep in mind that these are very much a security issue.  You should only add ones you trust.  Anyone who runs a repository that you use or anyone who manages to get access to it could put a trojan in the repository masquerading as a newer version of a common program and it would infect every machine that uses that repo.
I haven't heard of this ever actually happening but it's been demonstrated before by changing peoples wallpaper to a big warning symbol through apt.

---

### Post by wpshooter on 2007-01-21
> **zerhacke said:**
> There are third party repositories that can cause conflicts with the regular repository if enabled.  They'll cause problems.  Or so the story goes... I've never encountered any problem with any of the repositories I use.

The Firefox issue, though, I know what's causing that.  IPv6 is enabled in K/E/X/Ubuntu by default and nobody uses IPv6 yet.  To disable it and speed Firefox up, follow the steps below.

Open a terminal and type 

```
sudo gedit /etc/modprobe.d/aliases
```

Find the line: alias net-pf-10 ipv6

Edit this to: alias net-pf-10 off

Save the file and reboot



Is this really necessary or desirable ??  

I have never done this and to my knowledge I have no problems with Firefox ?  Are you saying that if I change this that Firefox is going to be running even faster than it is now ?

Thanks.

---

### Post by zerhacke on 2007-01-21
> **wpshooter said:**
> I have never done this and to my knowledge I have no problems with Firefox ?  Are you saying that if I change this that Firefox is going to be running even faster than it is now ?

Are you on dialup or broadband?  If you're on dialup it will make no difference.  You're going to be slow no matter what. Also, dialup doesn't bind to IPv6 for some reason.

If you're on broadband, have not disabled Ipv6, and are getting speedy service... well, it's possible your ISP, modem, and router support IPv6.  This is probably not likely though.

---

### Post by wpshooter on 2007-01-21
It is DSL, Verizon flavored.

The modem/router is a Westell Model 6100.  Do you think a search on this modem or a call to Verizon would tell me if it supports/uses Ipv6 ?

Thanks.

---

### Post by wpshooter on 2007-01-21
I turned Ipv6 to off and I really can not tell any difference !!!

---

