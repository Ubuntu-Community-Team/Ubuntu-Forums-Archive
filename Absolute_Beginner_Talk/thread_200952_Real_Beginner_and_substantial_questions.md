---
title: "Real Beginner and substantial questions"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by DanWan on 2006-06-21
I am a real new user of Linux (2 days). After installing succesfully Ubuntu and running it on a VAIO VGN-T2 I am totally unable to understand how to use any software besides what is already packaged in the Live DVD and the internet upgrades.

It might be trivial but what to do when:

After finding a package on the Internet which sounds useful, I search for it again and find it in the different Installing Utility supplied with Unbutu. The process tells me the software is being installed in my machine (example Wine or Qemu) with additional files necessay for the software to run. As I open the terminal I can also see what is written and were. However at the end of this process I cant find the application anywhere. 

I am certainly missing something, but I can't understand what these applications do exactly. For sure there is not a real 'installer' software, similar to the MAC installer, or Window2s SETUP (I am not a Winedows user) which simply makes available to the user what they need to use.  ]

If such software does not exist, how to run the applications once downloaded from the internet?

Example:
I downloaded from the internet a file ending with ".RPM" using Firefox. This because the Unbutu utiloties do nhot find it in the repositories. Firefox asks what I want to do with it suggesting Archiver as the default app. However Archiver tells me it can't recognize and install or unpack this file. The file vanishes. I download it again telling Firefox to save it on disk. Yet although I have found and possibly installed an RPM dearchiver, nothing happens as I don't know how to use this utility.

Also often I read some experienced user suggesting to modify this or that system config. Opening the text editor and doing the required changes is not difficult, however the modified file can't be saved, replaced and so on.
How to modify and then save in its proper location config and other system files.

Although I am new to Linux I managed Unix websites often and succesfully, with little or no problems. I understand Permission and this kind of things and I can even play a bit with PHP still I wonder where to find an effgicient guide to explain people how to do such simple things.

Something else I would like to know is how to get rid of the password routine. I am the only person using this system, and I don't need to allow myself to do things. Is there a way to achieve this. I reqalize this is true to avoid malicious internet navigators fgrom entering my system, but still I accept this risk rather than typing and cliking more often than not.

I have tried to google, wiki away and search forums, probably there is an answer, yet googling, wiking and searching cannot be a job. I wish someone would simly create a basic

One remark is the following. Linus is a very powerful and interesting System, of course it is mostly a niche and people doing it always know what they are talking about. Yet communication also means to be able to realize the meaning of a question, and what is the most appropriate langue to deliver an answer.

Thanks

---

### Post by aysiu on 2006-06-21
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) and [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) should answer all your questions about installing software.

Read this for password stuff: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
It explains Ubuntu's security philosophy, but it also tells you how to enable a traditional root account. It sounds as if (against your better judgment) you want to log in as root, and you'll be able to do that.

---

### Post by DanWan on 2006-06-21
I am a real new user of Linux (2 days). After installing successfully Ubuntu and running it on a VAIO VGN-T2 I am totally unable to understand how to use any software besides what is already packaged in the Live DVD and the internet upgrades.

It might be trivial but what to do when:

After finding a package on the Internet which sounds useful, I search for it again and find it in the different Installing Utility supplied with Unbutu. The process tells me the software is being installed in my machine (example Wine or Qemu) with additional files necessary for the software to run. As I open the terminal I can also see what is written and were. However at the end of this process I cant find the application anywhere. 

I am certainly missing something, but I can't understand what these applications do exactly. For sure there is not a real 'installer' software, similar to the MAC installer, or Windows SETUP (I am not a Windows user) which simply makes available to the user what they need to use.  ]

If such software does not exist, how to run the applications once downloaded from the internet?

Example:
I downloaded from the internet a file ending with ".RPM" with Firefox. This because the Unbutu utilities do not find it in the repositories. Firefox asks what I want to do with it suggesting Archiver as the default app. However Archiver tells me it can't recognize and install or unpack this file. The file vanishes. I download it again telling Firefox to save it on disk. Yet although I have found and possibly installed an RPM un-archiver, nothing happens as I don't know how to use this utility.

Also often I read some experienced user suggesting to modify this or that system config. Opening the text editor and doing the required changes is not difficult, however the modified file can't be saved, replaced and so on.
How to modify and then save in its proper location config and other system files.

Although I am new to Linux I managed Unix websites often and successfully, with little or no problems. I understand Permission and this kind of things and I can even play a bit with PHP still I wonder where to find an efficient guide to explain people how to do such simple things.

Something else I would like to know is how to get rid of the password routine. I am the only person using this system, and I don't need to allow myself to do things. Is there a way to achieve this. I realize this is true to avoid malicious internet navigators from entering my system, but still I accept this risk rather than typing and clicking more often than not.

I have tried to google, wiki away and search forums, probably there is an answer, yet googling, wiking and searching cannot be a job. I wish someone would simply create a basic

One remark is the following. Linux is a very powerful and interesting System, of course it is mostly a niche and people doing it always know what they are talking about. Yet communication also means to be able to realize the meaning of a question, and what is the most appropriate language to deliver an answer.

Thanks

---

### Post by aysiu on 2006-06-21
[Looks as if you already posted this thread](http://www.ubuntuforums.org/showthread.php?t=200951)

---

### Post by bukwirm on 2006-06-21
Some applications, such as WINE, do not have shortcuts in the 'Applications' menu. To run these programs, you usually need to go to the command line (Applications > Accessories > Terminal) and type in the name of the application, for example, to run WINE, type 'wine'.

Files ending in rpm are packages for other *nix distribution, such as Red Hat. Ubuntu uses Debian packages, which end in .deb. If you need to use a .rpm, you will need to install a package called 'alien' to convert it.

When modifing system file, you usually must be the superuser, type 'sudo nano filename' to edit system files.

Requiring a password when you try to do stuff that affects your computer more directly has two purposes: 1) to protect your computer from malicious hackers, and 2) to help prevent you from doing anything harm ful to your system. For example, you could remove your computer's entire filesystem with just the command 'rm -rf /'.

---

### Post by bukwirm on 2006-06-21
Sorry, I need to delete this.

---

### Post by icheyne on 2006-06-21
[quote=DanWan]
After finding a package on the Internet which sounds useful, I search for it again and find it in the different Installing Utility supplied with Unbutu. The process tells me the software is being installed in my machine (example Wine or Qemu) with additional files necessay for the software to run. As I open the terminal I can also see what is written and were. However at the end of this process I cant find the application anywhere. [/quote]

1. If it's a GUI application, it should find its way into the menus.
2. If it's a command line application, you need to run it from the command line.

> If such software does not exist, how to run the applications once downloaded from the internet?

The simple answer is not to bother using apps downloaded from the internet until you are more familiar with Linux. I find that sticking to Synaptic is most reliable and easy.

> Although I am new to Linux I managed Unix websites often and succesfully, with little or no problems. I understand Permission and this kind of things and I can even play a bit with PHP still I wonder where to find an effgicient guide to explain people how to do such simple things.

This is the root of your problem. I read this and it helped massively:

[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)

> Something else I would like to know is how to get rid of the password routine

[http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29](http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29)

---

### Post by DanWan on 2006-06-21
[QUOTE=aysiu][Looks as if you already posted this thread](http://www.ubuntuforums.org/showthread.php?t=200951)[/QUOTE]
I know I am sorry for this, however I received different replies and they appear valuable for me to solve my problems

---

