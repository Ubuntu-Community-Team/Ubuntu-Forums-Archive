---
title: "strange very strange internet issues"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by bluemarble on 2006-04-12
[solved]

Hiya,

So i finally got the internet connected and the wireless working but i can only access some web pages, not all. Mozilla keeps saying the connection has timeout. On top of this i cannot access system/admin/networking, it starts to load but goes not further.

For example i can access;

Ubuntu related pages, bendigobank.com, commbank.com.au, fastmail.fm, monash.edu.au 

but i cannot access 

smh.com.au, theage.com.au, bbc.co.uk, unsw.edu.au, google.com

I looked at [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE) and attempted configuring PPPoe and the results were as follows

bluemarble@:~$ dpkg -s pppoeconf
Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 308
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: all
Version: 1.8ubuntu2
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 Userfriendly tool for initial configuration of a DSL (PPPoE) connection.

bluemarble@:~$ sudo pppoeconf
sudo: unable to lookup  via gethostbyname()
bluemarble@:~$

Need help please!!

Blue

---

### Post by steve.horsley on 2006-04-12
If you can access some sites OK, then I guess your internet connection is working. 

Are you using firefox? If so, I have seen people suggest turning IPv6 off. Enter a URL of "about:config" and then enter "v6" into the search filter. Double-click the line **network.dns.disableIPv6** to set it to True. See if that makes a difference.

---

### Post by bluemarble on 2006-04-12
You rock! I can access all pages now and firefox is running faster... What did "Double-click the line network.dns.disableIPv6 to set it to True" do?

The only problem is i still cannot access system/admin/networking, in the lower desktop panel it states 'starting networking' but just disappears and nothing happens.  Any suggests?

Cheers
Blue

---

### Post by trent dillman on 2006-04-12
That app disappearing is a known bug...

---

### Post by steve.horsley on 2006-04-12
[QUOTE=bluemarble]You rock! I can access all pages now and firefox is running faster... What did "Double-click the line network.dns.disableIPv6 to set it to True" do?
[/QUOTE]
It stopped Firefox from trying to use IP version 6.
> 
The only problem is i still cannot access system/admin/networking, in the lower desktop panel it states 'starting networking' but just disappears and nothing happens.  Any suggests?

Cheers
Blue

You could try it from the command line: **gksudo network-admin** and see if you get any error messages.

---

### Post by bluemarble on 2006-04-13
Hiya

Tried 'gksudo network-admin' and the results were as follows

bluemarble@:~$ gksudo network-admin
sudo: unable to lookup  via gethostbyname()

I have realized that i cannot access package manager either...

Any ideas?

---

### Post by Jason_25 on 2006-04-13
What does 
```

cat /etc/hosts

```
show?

---

### Post by xenmax on 2006-04-13
bluemarble: Just wondering if you performed an expert install ?

---

### Post by bluemarble on 2006-04-13
This is what 'cat /etc/hosts' had to show;

127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And in regards to whether i perform a expert install, welll i would say it was more like a blind install!!!

---

### Post by steve.horsley on 2006-04-13
I can see from your user prompt that you don't have a hostname configured. This may be part of your problem. There should be a file called /etc/hostname that contains the hostname of the computer. This hostname should also be mentioned in /etc/hosts to the right of the address 127.0.0.1. You may be able to fix this from rescue mode on the install CD.

Choose a hostname for the computer, e.g. MyPC.
From the installer rescue mode, try the following:
[B]echo MyPc > /etc/hostname
nano /etc/hosts[/B]
And in the editor, add MyPC to the list of names after 127.0.0.1 like this:
127.0.0.1 localhost.localdomain localhost MyPC

---

### Post by bluemarble on 2006-04-13
I added the hostname of the computer via rescue mode and it now appears but only in 'cat /etc/hosts' as below;

bluemarble@:~$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost Source

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

But i do not seem to have permisson to access '/etc/hosts' or '/etc/hostname' as you can see below;

bluemarble@:~$ /etc/hosts
bash: /etc/hosts: Permission denied

Hmmmm....

I think I need a book of some description to smack my head against ;?

---

### Post by steve.horsley on 2006-04-13
Firstly, by just typing **/etc/hosts** you are asking the computer to execute the file, but it's not an executable file. What are you trying to do with the file?

I see from your prompt that you still don't have a hostname set, or al least it doesn't look as though you do - try: **cat /etc/hostname** to be sure. I guess from your hosts file that you want to use the name **Source**. You may have to use rescue mode of the install CD to be able to edit /etc/hostname and correct it.

---

### Post by Norelec on 2006-05-29
:) :) Well i have to say the infomation given in this thread was what i was looking for and worked wonders. THANX :) :)

---

