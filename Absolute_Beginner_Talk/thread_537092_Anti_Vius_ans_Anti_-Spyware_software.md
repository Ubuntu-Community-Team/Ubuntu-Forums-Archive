---
title: "Anti Vius ans Anti -Spyware software"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Dennis_Shepherd on 2007-08-28
Hi,

As an absolute newbie to Ubuntu I would welcome some advice on the best anti virus and anti spyware software to use.

Many Thanks,
Dennis

---

### Post by newlinux on 2007-08-28
some ideas and thoughts about  antivirus:

[http://ubuntuforums.org/showthread.php?t=530621](http://ubuntuforums.org/showthread.php?t=530621)

---

### Post by saj0577 on 2007-08-28
Hiya,

I dont think you need any to be honest with you, when i use to run windows i use to have so much protection yet i would still be getting virus and spyware etc. But on ubuntu i have not had one piece on any of my machines because many malicious people dont spend the time developing them for linux/unix. So unless you are storing really sensitive information on your computer then i would not install any to be honest just another thing to go wrong that you dont need.

Saj
Hope it helps

---

### Post by M$LOL on 2007-08-28
Short answer is that you don't need it unless you're on a network with Windows computers.

Long answer is that malware is written for Windows, and doesn't work on Linux. Some malware does run in Wine though, so be careful of that.

---

### Post by s26c.sayan on 2007-08-28
Don't bother to get an antivirus software.
A firewall config utility (like firestarter) is recommended though!

---

### Post by r4ik on 2007-08-28
> **M$LOL said:**
> Short answer is that you don't need it unless you're on a network with Windows computers.

Long answer is that malware is written for Windows, and doesn't work on Linux. Some malware does run in Wine though, so be careful of that.

Nice link about trolling and flaming bookmarked it.
Thanks.

---

### Post by hyper_ch on 2007-08-28
You don't need one... the AVs for linux just delete windows viruses... mainly they are used at servers (email / files / ....) so windows users don't catch them

However I think if you don't have an AV on windows why should others do the job for you?

---

### Post by por100pre1 on 2007-08-28
If you want to get busy, lets scan for rootkits with chkrootkit and rkhunter. 

To install them in Terminal:

```
sudo aptitude install chkrootkit rkhunter
```

To use them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

Have some computing fun. :)

---

### Post by neodorian on 2007-08-28
> **saj0577 said:**
> I dont think you need any to be honest with you, when i use to run windows i use to have so much protection yet i would still be getting virus and spyware etc.

That sucks about your Windows installs.  Once I found the winning team of AVG and Firefox 3 or 4 years ago, I haven't seen a virus on my Windows boxes at all.  Still, I agree with your main sentiment.  I've not installed any AV on my Linux systems at all and so far the only thing to screw them up has been me ;)

---

### Post by bumanie on 2007-08-28
Linux doesn't really have problems with virus' or malware etc. However if you wish to pursue an AV there is clam AV which in an open source application. I believe AVG has a debian version of their free for home use AV. I assume spyware terminator can be installed on ubuntu as it and clam AV are related programs. (I cannot check this as I am at work on a windoze machine). Go to either add/remove or synaptic and do a search for these, they should be part of the install cd programs or in a repository somewhere.

---

### Post by perspectoff on 2007-08-28
Although you will see lots of claims that there are no spyware or viruses for Linux, this does not mean that there aren't substantial security risks when using Linux (Ubuntu or any other distro).

If you download and install a package from a third-party source, you are at risk for a Trojan being installed on your computer. 

Be very careful about third-party packages and repositories. Make sure you trust them.

Many servers have security holes that you must be diligent about closing. Don't just set up an FTP, Apache, VNC, SSH, or other server without making sure you know how to tighten down access. 

Linux is susceptible to attack from the Internet; don't let claims of "no viruses or spyware" lull you into a false sense of security.

Furthermore, many Linux users trust in each other to find and expose security risks in open-source software. 

Remember that brand-new packages may not have circulated widely to be tested by a substantial number of users. Again; be wary of third-party packages and repositories.

Proprietary binary packages can contain anything, including a Trojan. If you install a binary package, make sure it is from a vendor you trust.

Lastly, I strongly recommend that as you learn Ubuntu, that you isolate any Ubuntu-based server from your LAN network while you learn to use it. Hackers can find a weak spot in your internet server and then access your LAN, which may have Windows boxes on it that are more susceptible to viruses, spyware, etc.

---

### Post by Dennis_Shepherd on 2007-08-29
Hi everyone,

Thanks for all of your advice.

The speed and helpfullness of the responses must make this one of the best forums that I have ever seen.

Regards,

Dennis

---

