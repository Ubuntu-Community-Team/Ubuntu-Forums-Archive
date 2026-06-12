---
title: "Proactive Security"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by kahrytan on 2007-03-31
I wish to take a more proactive approach to Ubuntu [linux]  security. I am aware of the fact that the security is already the best. I know ports are closed by default and privileged based security of Linux. But I want more. I want to harden the security of my Ubuntu.  When I talk about security, I mean by preventing unauthorized intrusions, key logging of any kind, and prevent binaries accessing the internet unless authorized to do so on any port.

Please keep the Terminal usage to a minimal. Stick to GUI based tools to harden security. This post is not just for me but for other newbies. The goal of this post is basically a Howto guide to security.

The reason I created this post is because Ubuntu Wiki [_'Proactive Security'_]("https://help.ubuntu.com/community/ProactiveSecurity") has not been written. This an attempt to fulfill the need for that Wiki.

---

### Post by nixclusive on 2007-03-31
Ports are not closed by definition but by virtue of not being open!! Since there are no applications installed in the default package that might require an open port, ports are *not open* by default. Thanks.

---

### Post by GSF1200S on 2007-03-31
> **kahrytan said:**
> I wish to take a more proactive approach to Ubuntu [linux]  security. I am aware of the fact that the security is already the best. I know ports are closed by default and privileged based security of Linux. But I want more. I want to harden the security of my Ubuntu.  When I talk about security, I mean by preventing unauthorized intrusions, key logging of any kind, and prevent binaries accessing the internet unless authorized to do so on any port.

Please keep the Terminal usage to a minimal. Stick to GUI based tools to harden security. This post is not just for me but for other newbies. The goal of this post is basically a Howto guide to security.

The reason I created this post is because Ubuntu Wiki [_'Proactive Security'_]("https://help.ubuntu.com/community/ProactiveSecurity") has not been written. This an attempt to fulfill the need for that Wiki.

Open firefox and do a search for "snort." Its an open source internet security suite thats free of charge. It doesnt have an antivirus, but most linux users dont seem to think that linux needs AV protection.

If you are concerned with AV protection, the most highly regaurded for Linux is ClamAV. This is also open source program. I believe Kaspersky AV has a client for Linux, but im not sure how good it is.. Hope some of this info helps...

---

### Post by kahrytan on 2007-03-31
The reason for this post is not for myself but build a howto post and perhaps add some data for the wiki.

So come on people. Let's fill this thread with tips, hints, and software from the repositories to help harden security for ubuntu. When you suggest a software, make sure it is in the repository with description and provide some useful tips on how to use it.

---

### Post by nixclusive on 2007-03-31
Ok lets start with educating the users about security in general. Then we can move over to specific security contexts and their possible solutions. I hope this just doesn't come off as some To-Do list for new users to make sure their system is *secure*. The very first and perhaps the weakest component of any Proactive Security System is its users. Educating the users about their own security should be of primary concern in your wiki article. Let more people join in and allow it mature continually.

Remember.. Security is not a product (or a package!!), its a process.

---

### Post by alien21010 on 2007-03-31
Unfortunately, the only real way to actually utilize a lot of the great security measures that Linux has built into it, is to use the Terminal.  For example, you could use Firestarter to interface with NetFilters (IpTables), but in the past I have seen that most of the rules Firestarter uses are absolutely unnecessary, and in some cases more dangerous than no rule at all.  

A firewall is a good place to start.  IPTables is your solution.  Plenty of pages out there explain how to set it up already.

---

### Post by kahrytan on 2007-04-01
> **alien21010 said:**
> Unfortunately, the only real way to actually utilize a lot of the great security measures that Linux has built into it, is to use the Terminal.  For example, you could use Firestarter to interface with NetFilters (IpTables), but in the past I have seen that most of the rules Firestarter uses are absolutely unnecessary, and in some cases more dangerous than no rule at all.  

A firewall is a good place to start.  IPTables is your solution.  Plenty of pages out there explain how to set it up already.

What is the best  GUI tool to configure IPTables?
What ports are needed ? Besides the HTTPS, HTTP, FTP SMTP, POP*,  and DNS.
What ports can one close and reject safely?

Here's some tools I know about;

 Guarddog, in Repository.
 Firewall Builder
 KmyFirewall

EDIT: One last question. How much protection does Router's provide?

---

### Post by nixclusive on 2007-04-01
Two of these tools are for KDE and fwbuilder seems too much of a configuration beast for new users. How about bastille? Simply answer a series of questions and the system is hardened in lot more ways than just firewalling:

```
sudo apt-get install bastille
```

---

### Post by nixclusive on 2007-04-01
After downloading and installing bastille, enter ```
sudo bastille -c
``` to access the curses bases GUI.

---

### Post by Obor on 2007-04-01
This isn't exactly an answer to your question but you might find the following article useful. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by bodhi.zazen on 2007-04-01
A little off topic as well, but this is the best reference I know :

Link: [http://www.puschitz.com/SecuringLinux.shtml](http://www.puschitz.com/SecuringLinux.shtml)

Book ~ Hardening Linux : [http://www.apress.com/book/bookDisplay.html?bID=395](http://www.apress.com/book/bookDisplay.html?bID=395)

---

### Post by jvc26 on 2007-04-01
Best Ubuntu GUI iptables editor is Firestarter in my opinion. I would recommend you install that straight away on getting your system installed and then you add the settings - put the standard stuff on, and if you want turn things like ICMP filtering on (though it can block stuff like pings and so forth which you may want to use) so you can add that at your own discretion.

Using things like bastille is another way to make your computer much harder to break into. The book Hardening Linux as Bodhi has mentioned is really good for this - you may well get a lot of information out of it which you can add (and learn one hell of a lot whilst you're there) I have enjoyed the book (the parts of it I've read)

My personal opinion is to configure Firestarter straight away - I may be wrong but I have seen this mentioned multiple times is that Iptables IS NOT CONFIGURED BY DEFAULT I have checked this myself with:
```

sudo iptables -L

```
Which you may well finds outputs no rules at all and a very permissive setup. Therefore get Firestarter, run through the normal straightforward configure steps, and that will get you at least some stuff. Once you've got iptables basically on, then you can go into firestarter's preferences and choose more specifically services you want to allow/ban, and you can set up particular rules for particular domains.

I hope some of the stuff in this brief note will give you more things to add to your discussion on the wiki. ClamAV I havent got installed, though I have in the past, more as a thing to virus scan stuff I'm sending to the windows boxes I have. (After all you can be a carrier, even if you cant be infected)

Il

---

### Post by nixclusive on 2007-04-01
ClamAV yeah.. the newer version sure got a new feature called 'clamuko'. It works with the Dazuko kernel module to provide on-access virus scanning in linux too!!

And yeah, *linux cannot be infected with virus/malware/spyware etc.* is an absolute myth. Period.

Anyone up for SELinux, Mandatory Access Control.. sandboxing, etc.??

---

### Post by kahrytan on 2007-04-01
> **Illuvator said:**
> Best Ubuntu GUI iptables editor is Firestarter in my opinion. I would recommend you install that straight away on getting your system installed and then you add the settings - put the standard stuff on, and if you want turn things like ICMP filtering on (though it can block stuff like pings and so forth which you may want to use) so you can add that at your own discretion.

Using things like bastille is another way to make your computer much harder to break into. The book Hardening Linux as Bodhi has mentioned is really good for this - you may well get a lot of information out of it which you can add (and learn one hell of a lot whilst you're there) I have enjoyed the book (the parts of it I've read)

My personal opinion is to configure Firestarter straight away - I may be wrong but I have seen this mentioned multiple times is that Iptables IS NOT CONFIGURED BY DEFAULT I have checked this myself with:
```

sudo iptables -L

```
Which you may well finds outputs no rules at all and a very permissive setup. Therefore get Firestarter, run through the normal straightforward configure steps, and that will get you at least some stuff. Once you've got iptables basically on, then you can go into firestarter's preferences and choose more specifically services you want to allow/ban, and you can set up particular rules for particular domains.

I hope some of the stuff in this brief note will give you more things to add to your discussion on the wiki. ClamAV I havent got installed, though I have in the past, more as a thing to virus scan stuff I'm sending to the windows boxes I have. (After all you can be a carrier, even if you cant be infected)

Il

How would you set up Firestarter on your computer? With details please.  I believe in restrictive setups.  

How do you keep binaries from acting as services and sending out data on allowed ports?

And more questions that are unrelated. Is there an application can monitor or scan system logs and watch for unusual activity?

---

### Post by nixclusive on 2007-04-02
Is there an application can monitor or scan system logs and watch for unusual activity?

Probably tripwire. ```
sudo apt-get install tripwire
```

---

### Post by nixclusive on 2007-04-02
How do you keep binaries from acting as services and sending out data on allowed ports?

You can probably use the iptables 'owner' match target to control certain level of process filtering:

> 
owner

This module attempts to match various characteristics of the packet creator, for locally-generated packets. It is only valid in the OUTPUT chain, and even this some packets (such as ICMP ping responses) may have no owner, and hence never match.

--uid-owner userid
    Matches if the packet was created by a process with the given effective user id. 
--gid-owner groupid
    Matches if the packet was created by a process with the given effective group id. 
--pid-owner processid
    Matches if the packet was created by a process with the given process id. 
--sid-owner sessionid
    Matches if the packet was created by a process in the given session group. 

Each binary that may require internet access can be placed in a certain group and the relative ruleset can be applied. Very much similar to ZoneAlarm's program control module.

---

### Post by kahrytan on 2007-04-03
How would I go about using this  easily? GUI if possible or step by step tutorial.

---

### Post by STREETURCHINE on 2007-04-03
```
Sure, there are Linux viruses. But let's compare the numbers. According to Dr. Nic Peeling and Dr Julian Satchell's Analysis of the Impact of Open Source Software 

"There are about 60,000 viruses known for Windows, 40 or so for the Macintosh, about 5 for commercial Unix versions, and perhaps 40 for Linux. Most of the Windows viruses are not important, but many hundreds have caused widespread damage. Two or three of the Macintosh viruses were widespread enough to be of importance. None of the Unix or Linux viruses became widespread - most were confined to the laboratory."

Why are Linux and Mac OS X safer?

First, look at the two factors that cause email viruses and worms to propagate: social engineering, and poorly designed software. Social engineering is the art of conning someone into doing something they shouldn't do, or revealing something that should be kept secret. Virus writers use social engineering to convince people to do stupid things, like open attachments that carry viruses and worms. Poorly designed software makes it easier for social engineering to take place, but such software can also subvert the efforts of a knowledgable, security-minded individual or organization. Together, the two factors can turn a single virus incident into a widespread disaster.

Let's look further at social engineering. Windows software is either executable or not, depending on the file extension. So if a file ends with ".exe" or ".scr", it can be run as a program (yes, of course, if you change a text file's extension from ".txt" to ".exe", nothing will happen, because it's not magically an executable; I'm talking about real executable programs). It's easy to run executables in the Windows world, and users who get an email with a subject line like "Check out this wicked screensaver!" and an attachment, too often click on it without thinking first, and bang! we're off to the races and a new worm has taken over their systems.

Even worse, Microsoft's email software is able to infect a user's computer when they do something as innocuous as read:  Don't believe me http://www.microsoft.com/technet/treeview/default.asp?url=/technet/security/bulletin/MS03-023.asp

This sort of social engineering, so easy to accomplish in Windows, requires far more steps and far greater effort on the part of the Linux user. Instead of just reading an email (... just reading an email?!?), a Linux user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. Even as less sophisticated users begin to migrate to Linux, they may not understand exactly why they can't just execute attachments, but they will still have to go through the steps. As Martha Stewart would say, this is a good thing. Further, due to the strong community around Linux, new users will receive education and encouragement in areas such as email security that are currently lacking in the Windows world, which should help to alleviate any concerns on the part of newbies.


Further, due to the strong separation between normal users and the privileged root user, our Linux user would have to be running as root to really do any damage to the system. He could damage his /home directory, but that's about it. So the above steps now become the following: read, save, become root, give executable permissions, run. The more steps, the less likely a virus infection becomes, and certainly the less likely a catastrophically spreading virus becomes. And since Linux users are taught from the get-go to never run as root, and since Mac OS X doesn't even allow users to use the root account unless they first enable the option, it's obvious the likelihood of email-driven viruses and worms lessens on those platforms.

Security is, as we all know, a process, not a product. So when you use Linux, you're not using a perfectly safe OS. There is no such thing. But Linux and Mac OS X establish a more secure footing than Microsoft Windows, one that makes it far harder for viruses to take hold in the first place, but if one does take hold, harder to damage the system, but if one succeeds in damaging the system, harder to spread to other machines and repeat the process. When it comes to email-borne viruses and worms, Linux may not be completely immune - after all, nothing is immune to human gullibility and stupidity - but it is much more resistant. To mess up a Linux box, you need to work at it; to mess up your Windows box, you just need to work on it. I know which one I'll trust. How about you?


```

---

### Post by aysiu on 2007-04-03
> This sort of social engineering, so easy to accomplish in Windows, requires far more steps and far greater effort on the part of the Linux user. Instead of just reading an email (... just reading an email?!?), a Linux user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. > Further, due to the strong separation between normal users and the privileged root user, our Linux user would have to be running as root to really do any damage to the system. Not true any more. All one would need to do is have a .deb as an attachment. Double-click the .deb file, offer your password when GDebi asks for it, and the .deb sender can do whatever she wants to your computer. You've been compromised, and it's just as easy as in Windows. Just no one writes those .deb files right now. Social engineering is not OS-specific. It can happen to any user who is not aware of what she's doing. Users need to be "street smart" on the web, and it doesn't matter what operating system they use, all other social factors being equal. As Ubuntu becomes a bigger target, you're far more likely to get social engineering-based malware based around .deb files and such. > He could damage his /home directory, but that's about it. And who cares about all those irreplaceable family photos, documents, and such when you can protect all the system files that are easily replicated by a reinstall of the OS? Sure, every user backs up all her stuff regularly, though. All users do that, right? So the /home directory can be damaged, and that's okay. Right. > So the above steps now become the following: read, save, become root, give executable permissions, run. The more steps, the less likely a virus infection becomes, and certainly the less likely a catastrophically spreading virus becomes. No, really, as I outlined before, the steps are to become a target, have the malware-writer create a .deb attachment, have the user double-click the attachment, enter her password, and the virus is off and running. No different from Windows.

---

### Post by kahrytan on 2007-04-03
> **Obor said:**
> This isn't exactly an answer to your question but you might find the following article useful. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)



With respect, We're moved beyond the howto article in Ubuntu security  to building secure iptables firewall.

---

### Post by kahrytan on 2007-04-03
> **aysiu said:**
> Not true any more. All one would need to do is have a .deb as an attachment. Double-click the .deb file, offer your password when GDebi asks for it, and the .deb sender can do whatever she wants to your computer. You've been compromised, and it's just as easy as in Windows. Just no one writes those .deb files right now. Social engineering is not OS-specific. It can happen to any user who is not aware of what she's doing. Users need to be "street smart" on the web, and it doesn't matter what operating system they use, all other social factors being equal. As Ubuntu becomes a bigger target, you're far more likely to get social engineering-based malware based around .deb files and such. 

All the more reason to focus on the possible ways of attack. Why wait? A preemptive fix to ensure that Debian based distributions remain secure.

---

### Post by aysiu on 2007-04-03
But social engineering is social. It bypasses any software security that is set up and depends solely on the user.

As long as the user is in the *admin* group, will click on anything, and is dumb enough to enter her password for anything... it doesn't matter how "securely" the OS is "built."

---

### Post by eentonig on 2007-04-03
correct. And the more you annoy your user with security related pop-ups, questions, passwords and so on... the more likely he wont be reading any of them and just start clicking <ok> or entering his password.

In my opinion, a default install is more than secure enough for desktop usage. It's the default user that isn't. so any security related efforts should go into making your users aware of the threats. Not by forcing them to bear with stupid messages and actions over and over again. Because those are just making your users bored with security.

Actually, the only systems I agree on supporting for friends and family, is those where they don't have root priviliges. That is, the actual users are NOT in the admin group. That way, i'm sure they'll ask me if they want something installed. And for the rest, it's up to me to make sure they keep up to date by administering them remotely and making sure they have the required updates. And that's done via a script.

---

### Post by bodhi.zazen on 2007-04-03
> **kahrytan said:**
> All the more reason to focus on the possible ways of attack. Why wait? A preemptive fix to ensure that Debian based distributions remain secure.

Security is a relative term. It is an ongoing process and, generally, increasing security = decreasing ease of use. For example, in Vista one must allow all processes ... (or something like that, I actually have not seen Vista).

Linux is quite secure out of the box. There are a number of things you can do to further harden your OS, but generally, unless you are running a server, you do not need to. If you are going to install and run a server, part of the installation responsibility is on you to learn how to configure the server to be secure.

> **aysiu said:**
> But social engineering is social. It bypasses any software security that is set up and depends solely on the user.

As long as the user is in the *admin* group, will click on anything, and is dumb enough to enter her password for anything... it doesn't matter how "securely" the OS is "built."

I agree with aysiu.

Best to make a second user for daily use not in the admin group.

You can then obtain root access, in a terminal, without logging out -> in

```
su <user_name_with_admin_access>
Password : <enter_password>
sudo -i
```

Second, as with ALL OS, DO NOT DOWNLOAD OR INSTALL PROGRAMS FROM UNKNOWN SOURCES. If you stay with the repos's you will be good to go.

If, as a user with admin access, you download and install programs from unknown sources, well there is really nothing to protect you from yourself. Knowing your OS, how to keep it secure, and what not to download/install is your responsibility (as an administrator).

---

### Post by nixclusive on 2007-04-03
So it all comes down to education the user about his or her own security in general. Hey you can create a wiki that works with the concepts and uses the various tools and utilities in their implementation.. duh.. do you have any outline prepared?

Yo aysiu.. good to see you here :-)

---

### Post by bodhi.zazen on 2007-04-03
> **nixclusive said:**
> So it all comes down to education the user about his or her own security in general. Hey you can create a wiki that works with the concepts and uses the various tools and utilities in their implementation.. duh.. do you have any outline prepared?

Yo aysiu.. good to see you here :-)

In terms of a wiki, start by identifying the existing projects. Contribute to and improve them. Bring them to the awareness of the community.

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Security&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=Security&titlesearch=Titles)

[https://help.ubuntu.com/community/CategorySecurity](https://help.ubuntu.com/community/CategorySecurity)

---

### Post by kahrytan on 2007-04-03
What's the difference between Admin user and Non-Admin user? What kind of restrictions is placed on the non-admin users?

---

### Post by aysiu on 2007-04-03
Non-admin users cannot modify anything outside their /home/username directories

Admin users can modify anything as long as they preface the modifying command with *sudo* **and** then give their passwords as authentication.

---

### Post by FLPCGuy on 2007-04-03
FYI,
Another significant threat to all versions of Windows has been demonstrated on 3/28/07. This includes the supposedly improved Windows Vista. It is an exploit of the animated cursor feature of Windows and Internet Explorer.  While such files typically end with .ANI, they can also be executed with many other file extensions. For a technical explanation see: 
[http://www.determina.com]("http://www.determina.com/security.research/vulnerabilities/ani-header.html")[/security.research/vulnerabilit]("http://www.determina.com/security.research/vulnerabilities/ani-header.html")[ies/ani-header.html]("http://www.determina.com/security.research/vulnerabilities/ani-header.html")

This threat can be launched from an email or a web page allowing hidden code to be executed with your user rights (usually Administrator rights).  So, Windows users cannot safely open email (except text only email) or visit websites other than trusted ones until a fix is provided.  Malware run from this exploit could compromise personal security info, delete files and even wipe or disable your computer. 

It may be possible to avoid the most likely source of the threat by using the Firefox web browser available for Windows but this is not certain.  Apparently, it is not possible to turn off support for animated cursors in Windows since they use a key system file USER32.DLL, so there is no way to disable this insecure, non-essential feature of Windows.

Just by knowing enough to use Linux you are already so much more secure than using Windows, the few threats that remain are rather insignificant by comparison.  Not running with root privileges keeps the basic OS pretty secure.

It also helps to have a hundred flavors of Linux with new kernels comping out every month and new distros every six.  How would you write and spread a virus for that kind of environment and why?

---

### Post by nixclusive on 2007-04-09
This looks dead enough but hey.. here's a starting point for ya to stand on. Maybe build something out of this. The wiki page is still empty enough... :o

[http://tldp.org/guides.html#securing_linux](http://tldp.org/guides.html#securing_linux)

---

