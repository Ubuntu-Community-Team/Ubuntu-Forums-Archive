---
title: "No virus?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Frydek on 2008-02-01
Hi,
I'm totally new to linux.
The person who convinced me to install it told me there was no virus problems.
Sorry if it's a silly question but... is it true? If so, why?
Thanks

---

### Post by LostMagix on 2008-02-01
There are, but the likelihood you will get one is very very low.

---

### Post by jan quark on 2008-02-01
viruses are written to affect windows systems, the windows-like architecture of applications
the windows way of dealing with processes 

linux is different

99 % of all viruses are "windows" viruses
and the 1 % is too slow comparing to the update process of linux to effectively affect the system

---

### Post by emarkd on 2008-02-01
Yes it's true. There have been about 40 Linux viruses ever, and they don't last long.  There are no known Linux viruses in the wild now.  The why is a little more complicated.

Here's a good article that goes more in-depth on this:  [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by hyper_ch on 2008-02-01
multiple reasons

(1) Linux is not defective by design

(2) see reason (1)

(3) you don't use warez/p2p sites to get programs... you get (most of it) from repos which are clean

(4) It's more fun to hack M$ than Linux

(5) If you hack M$ you normally get full control to that machine (and create zombie networks which you can sell them for spamming or DDoSing)... if you hack a Linux machine, you may only control just 1 program and/or get access to the user's home....

(6) there are about 40 known linux viruses... none of them in the wild... compared to about 60'000 known malware for windoze....

---

### Post by reyhan on 2008-02-01
there is no virus on linux because the linux is totally different then windows

---

### Post by jrharvey on 2008-02-01
Another reason is that Unlike windows, linux and unix (like osx) do not automatically let applications mess with the system files. You must have root acess to be able to change anything in the system. I believe windows may have gotten better about this with vista but im not completley sure. TRUST ME, you are ALOT safer with linux and OSX than you ever were on windows with the best virus scanners and firewalls. I dual boot windows and have completely removed it from the internet. I deleted all internet browsers also, just incase.

---

### Post by hyper_ch on 2008-02-01
another reason:

Whether a file can be executed does not depend on the filename extension but on the actual permissions. Normally you couldn't execute a file without altering that first.

---

### Post by az on 2008-02-01
> **Frydek said:**
> If so, why?


Gnu/Linux is not owned or written by one person or organization.  Windows is under complete control of microsoft.  

Why do you think you have to scan and remove vulnerabilities from Windows but the same kinds of vulnerabilities are just fixed in Gnu/Linux?

Because if windows did that, a whole lot of applications that are supposed to "just work" would "just break".  Linux is source-compatible, not binary-compatible.  You can fix something, recompile it and it "just works".  You can't recompile most things in windows.

---

### Post by aysiu on 2008-02-01
> **hyper_ch said:**
> another reason:

Whether a file can be executed does not depend on the filename extension but on the actual permissions. Normally you couldn't execute a file without altering that first.
I don't think people should get complacent about this idea.

If people wanted to target Ubuntu users with malware, all they'd have to do is create a crafty .deb file and trick people into downloading it and double-clicking it. gDebi will take care of the rest.

---

### Post by Whiffle on 2008-02-01
> **aysiu said:**
> I don't think people should get complacent about this idea.

If people wanted to target Ubuntu users with malware, all they'd have to do is create a crafty .deb file and trick people into downloading it and double-clicking it. gDebi will take care of the rest.


Which points out another thing, that the user is probably the biggest security risk on linux.

---

### Post by hyper_ch on 2008-02-01
yeah, social working ;)

Let's ban users from using computers ;)

---

### Post by aysiu on 2008-02-01
> **Whiffle said:**
> Which points out another thing, that the user is probably the biggest security risk on linux.
Exactly. I wrote more about that idea here: [Without education, it doesn&#8217;t matter which OS is &#8220;more secure&#8221;](http://ubuntucat.wordpress.com/2008/01/22/without-education-it-doesnt-matter-which-os-is-more-secure/)

---

### Post by insane_alien on 2008-02-01
> **Whiffle said:**
> Which points out another thing, that the user is probably the biggest security risk on linux.

The user is the biggest security risk on anything. even windows can be completely secure if the user is smart. if the user is not scurity wise then no matter how many levels of security you have, short of unplugging the network, there will be no way of completely secring any box with any OS

---

### Post by jan quark on 2008-02-01
How very true aysiu

we are talking about viruses and trojans and internet worms and phishing sites,,,

but behind all this are real people and real people are the attacked ones

so security can be increased by increasing the awareness not of the death applications but of the users

---

### Post by bodhi.zazen on 2008-02-01
> **Frydek said:**
> Hi,
I'm totally new to linux.
The person who convinced me to install it told me there was no virus problems.
Sorry if it's a silly question but... is it true? If so, why?
Thanks

Viruses take advantage of holes or flaws in the code. There have been Linux Viruses, but their damage has always been limited to a users home directory and, being open source, the holes have been rapidly patched.

Microsoft, on the other hand, had made little or no attempt to patch the various flaws and security issues, either preferring "ease of use" over security or leaving known holes unpatched for years. So much so that there is a whole industry of spy ware, virus detection, and firewalls around such holes.

In Linux security is different. The threats are different.

See this link : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

As has been pointed out, on any OS security is an active process and involved user education and awareness of social engineering.

EDIT: Nowadays you need to secure your browser as well. 

This will get you started : [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by IamJohnHayes on 2008-02-01
> **Whiffle said:**
> Which points out another thing, that the user is probably the biggest security risk on linux.

Sudo does help with this isssue a little better,  anyone wanting acess would not be able to just try under the default of root user.  also stops the user from screwing things ups as easily while logged in as root.

just my .02

---

### Post by agim on 2008-02-01
Thanks for the post about dangerous .deb files and gdebi. I am a new linux user and I am learning more everyday, but I had not considered this. Great piece of info.

---

### Post by aysiu on 2008-02-02
> **agim said:**
> Thanks for the post about dangerous .deb files and gdebi. I am a new linux user and I am learning more everyday, but I had not considered this. Great piece of info.
Well, at the moment, I have never heard of a malicious .deb file, but it could be something developed in the future.

---

### Post by Perfect Storm on 2008-02-02
As long you keep to the official repo. Don't use a .deb or repo from a total stranger with no reputation.

---

### Post by misfitpierce on 2008-02-02
To put it simply

NO - There are no viruses... By stating this im not saying there are 0 viruses ever made for linux but you got a better chance of a train coming through your house and then a airplane crashing into the same spot followed by santa coming down the chimney all at once! Amazing huh?

There is always a chance for someone to make some sort of malware to destroy something on any OS. But linux is very secure unlike windows which is Admin at all times and allows you to do whatever, whenever. So no you'll be fine without antivirus or anything for linux... To answer antoher question if curious... Antivirus is made for linux as well by AVG and Avast but it is to pick up windows viruses so you dont spread windows viruses to a windows machine if you get and network with windows computers on your network. Enjoy.

---

