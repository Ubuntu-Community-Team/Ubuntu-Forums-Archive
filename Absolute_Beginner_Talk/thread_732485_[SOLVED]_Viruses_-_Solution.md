---
title: "[SOLVED] Viruses - Solution?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-03-22
I know I know the old adage, ubuntu doesn't have any viruses. But I recently came across this:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

and it details numerous ways to make ubuntu more secure...

2 things:

1. I don't want to do anything that could "harm" my system, so I'd rather get expert opinion before doing any of this.

2. I don't want to waste a lot of time downloading and compiling all 50 of these programs only to find that they don't really help.

Right now I'm on Gutsy and using Lokkit and AVG.

Thanks!

---

### Post by Oldsoldier2003 on 2008-03-23
> **abhiroopb said:**
> I know I know the old adage, ubuntu doesn't have any viruses. But I recently came across this:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

and it details numerous ways to make ubuntu more secure...

2 things:

1. I don't want to do anything that could "harm" my system, so I'd rather get expert opinion before doing any of this.

2. I don't want to waste a lot of time downloading and compiling all 50 of these programs only to find that they don't really help.

Right now I'm on Gutsy and using Lokkit and AVG.

Thanks!

As far as viruses practice safe computing practices and drive on :)
As far as general security is concerned a lot of it depends on how valuable your data is to you. Obviously if it is mission critical or sensitive data, the more security the better. The main thing to remember is the more ports you open, the more vulnerable you become. If you are running servers its best to separate the services, one web one mail one samba etc... so that any breaches of your security don;t affect the entire enterprise immediately. Its also a lot easier to secure a single use machine.

---

### Post by oedha on 2008-03-23
recently......just keep your system update......you're safe....CMIIW :)

---

### Post by ubuntu-freak on 2008-03-23
All seems a bit overkill to me. I guess installing StartUp Manager and setting it to prompt for the root password at GRUB is a good idea though. As for antivirus, it's up to Windows users to make sure they have at least AVG Free Edition installed. Also, doesn't Ubuntu have a built-in firewall? I'm sure it does.
 
Nathan

---

### Post by Oldsoldier2003 on 2008-03-23
> **reassuringlyoffensive said:**
> All seems a bit overkill to me. I guess installing StartUp Manager and setting it to prompt for the root password at GRUB is a good idea though. As for antivirus, it's up to Windows users to make sure they have at least AVG Free Edition installed. Also, doesn't Ubuntu have a built-in firewall? I'm sure it does.
 
Nathan

yeah its pretty overkill and complicates matters immensely. a Ubuntu install is more secure out of the box than a fully tweaked windows install anyhow. When you start running servers is when you need to tighten down the security screws.

As Far as a grub password. If you need to go that far i think you have problems that wont be solved by that "security measure" phyical access to a machine = total ownage, passwording grub will only delay said ownage for a couple minutes :)

---

### Post by herbster on 2008-03-23
I advise you to read the security structure of linux with regards to users, permissions, etc. Here's a good one split by topics: [http://www.linuxtopia.org/online_books/linux_administrators_security_guide/](http://www.linuxtopia.org/online_books/linux_administrators_security_guide/)

If you don't want to do anything to harm your system, as you stated, then you're fine, case closed.

---

### Post by asmoore82 on 2008-03-23
Um, about that article you linked to; I won't bother to read the whole thing because
I can already go ahead and point out that their first three points are utter nonsense:

> Reconfiguring shared memory
Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:

tmpfs /dev/shm tmpfs defaults,ro 0 0
shared memory is just that: ***shared***; making it **read-only** defeats the purpose.
this location is already protected by being "sticky" meaning users can't trample each other's files:
```
~$ ls -dl /dev/shm
**drwxrwxrwt** 2 root root 60 2008-03-22 01:07 /dev/shm
```
^the 't' there means sticky.

> Disabling SSH root login
Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:

PermitRootLogin yes
to
PermitRootLogin no
this is a moot point for 2 reasons:
1. sshd is _NOT_ installed by default; so its settings have no effect on anything *out-of-the-box*
2. the root account is locked with no passwd *out-of-the-box*
Why does it matter that in theory the non-existent service could allow the invalid user to log in??

> Limiting access to the "su" program
Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:

sudo chown root:admin /bin/su sudo
chmod 04750 /bin/su
First of all the first command has an error in it: the sudo on the end is superfluous and will cause this error:
```
chown: cannot access `sudo': No such file or directory
```
These people can't even get a simple command right and they are giving us security advice?
Did they not even run down the checklist *and take their own advice* before publishing the article??

Secondly, the effect of `su` is almost nil because the root account is locked and disabled *out-of-the-box*.
Theoretically, `su` also allows any user to masquerade as any other user with the correct password;
But they do have to know the password and if they do, they can simply log in as that other user directly.

And finally, if you cross reference my rebuttals, you can see that the answer to #2 applies to 1 and 3:
what major difference can shared memory and `su` make in network security if ssh is not enabled??

---

### Post by herbster on 2008-03-23
Poop, I got confused for a sec and thought you were referencing my link.

---

### Post by dcstar on 2008-03-23
> **asmoore82 said:**
> Um, about that article you linked to; I won't bother to read the whole thing because I can already go ahead and point out that their first three points are utter nonsense:
......

The article is dated May 2007, so it doesn't event take 7.10 into account (presumably it used 7.04 as its base).

A lot of it seems totally unnecessary for the "normal" Ubuntu home user who would not be concerned by some malicious person having actual access to the hardware (which a lot of the "solutions" seem to be aimed at).

Even the part about changing read permissions on the home directories assumes that you will have additional logins on your system and you are worried about one user seeing another's files - not a big concern for most people.

Since a lot of people also run their systems behind a NAT device, the "protection" from external network attacks is also redundant.

If someone can prove that Linux can have scumware installed by normal use/web browsing (like Windows), then I'd be prepared to give these articles some credence, until then I just use my anti-virus to scan my incoming e-mails and let me know about spoofed links and other Windows scumware that won't affect me anyway.

If I wanted to remain panicked about the big, nasty world attacking my PC then I would have remained a Windows user and lived with a system crippled by various always to be out of date "protection", since I actually use Linux I don't need to be too concerned by the 0.001% of possibilities for attack in comparison.

---

### Post by abhiroopb on 2008-03-23
Thanks a lot for the help, was just worried that there was apparrently SO much I hadn't done. I just installed chkrootkit or something, and did a scan. I think my machine is secure so I'm happy with it. I guess its never 100% secure so its a good idea to give all this a try out, but I'm happy with my current set up.

Thanks again for the advice

---

