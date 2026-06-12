---
title: "Clam Virus Scanner"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jcouillard on 2007-11-14
I am new obviously and I have no idea what 'you must be root to install updates' means...lol How do I become root. I am assuming it means admin but I mean aren't you an admin by default on your personal computer like in Windows/ I guess not. Can I run as and admin by the way?? Help...lol

---

### Post by Paul820 on 2007-11-14
Maybe this can explain it for you [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by mdpalow on 2007-11-14
+1 on the above reply.

You have administration ability, but you have to switch to this in order to do many key things. This is the nature of the built in security... read up on it some more.

However, and quickly... it just means you should open a terminal windows and type:

sudo 'some_command_could_go_here' and then enter your password. Then you would be
a super user and able to do what you need.

So, for example. If you wanted to delete a file in the /etc directory, you would need to have the authority/permission to do that. So, you would simply enter this in a terminal:

cd /etc
sudo rm test_file.txt

the system would ask for your password and then would do it... If you hadn't used sudo in about 15 minutes, you would be asked for your password again. Otherwise, you could keep going without having to re-enter your password each time...

that's it....

---

### Post by Giradman on 2007-11-14
You really have not explained the 'purpose' of your request as it relates to the title of your posting, i.e. 'Clam Virus Scanner' - if you're trying to update your ClamAV definition files, then a simple way is to go into the terminal mode, and type in 'sudo freshclam' - you will need to enter your password, then the definitions are updated - just did it a few days ago.  If there is another issue, then please explain - good luck - :)

---

### Post by jcouillard on 2007-11-16
> **Giradman said:**
> You really have not explained the 'purpose' of your request as it relates to the title of your posting, i.e. 'Clam Virus Scanner' - if you're trying to update your ClamAV definition files, then a simple way is to go into the terminal mode, and type in 'sudo freshclam' - you will need to enter your password, then the definitions are updated - just did it a few days ago.  If there is another issue, then please explain - good luck - :)

The reason why I typed that was b/c I was unsure if it was just for that program or not. I am new to Linux and no other program but that one needed me to do that as of yet, thus the subject. Thanks for the help guys.

---

### Post by Giradman on 2007-11-16
> **jcouillard said:**
> The reason why I typed that was b/c I was unsure if it was just for that program or not. I am new to Linux and no other program but that one needed me to do that as of yet, thus the subject. Thanks for the help guys.

OK, so was your question addressed?  Are you interested in just updating your ClamAV files, and if so, did the suggestion work?  I'm just trying to determine if this is your issue, and if the  suggestion worked?  Just to help others w/ the same concern - thanks for any response - :)

---

### Post by ramjet_1953 on 2007-11-16
The question begging to be asked here, is why do you even feel the need to have an anti-virus scanner anyway?

There are no active Unix-like viruses out there in the wild and even the ones that have been floated are ineffective, unless you allow them into your system through root permissions.

Unless you are using Wine, downloading a virus scanner is a waste of space.

Even with email attachment forwarding to Windows users these days doesn't really require you to scan for Windows viruses, as email providers scan attachments anyway.

Regards,
Roger :cool:

---

### Post by Giradman on 2007-11-16
> **ramjet_1953 said:**
> The question begging to be asked here, is why do you even feel the need to have an anti-virus scanner anyway?

There are no active Unix-like viruses out there in the wild and even the ones that have been floated are ineffective, unless you allow them into your system through root permissions.

Unless you are using Wine, downloading a virus scanner is a waste of space.

Even with email attachment forwarding to Windows users these days doesn't really require you to scan for Windows viruses, as email providers scan attachments anyway.

Regards,
Roger :cool:

**Roger** - thanks for that response - I'm paranoid as a long time Windows user (and still so!) - but even after a month or so w/ Ubuntu I feel the same way now - I initially downloaded ClamAV but now understand after much reading, web searching, and multiple comments on this forum (including yours) that viruses just are not much (if @ all) a concern w/ this OS - :)

---

### Post by jcouillard on 2007-11-21
Yeah i guess it's a habit...lol I may take it off too.

---

### Post by pbmax on 2007-11-28
> **ramjet_1953 said:**
> The question begging to be asked here, is why do you even feel the need to have an anti-virus scanner anyway?

There are no active Unix-like viruses out there in the wild and even the ones that have been floated are ineffective, unless you allow them into your system through root permissions.

Unless you are using Wine, downloading a virus scanner is a waste of space.

Even with email attachment forwarding to Windows users these days doesn't really require you to scan for Windows viruses, as email providers scan attachments anyway.

Regards,
Roger :cool:

I thought that too, but irc.efnet banned me because my DSL's IP address was blacklisted due to a "Srorm Worm" infection.

I looked it up and it's windows only, but I decided to run ClamAV just to check what's up.

Now for the stupid question: in 7.10, I installed ClamAV with synaptic but can't find it in the menu. Anyone know how to run it?
thanks
pb

---

### Post by Giradman on 2007-11-28
> **pbmax said:**
> ..........but I decided to run ClamAV just to check what's up.

Now for the stupid question: in 7.10, I installed ClamAV with synaptic but can't find it in the menu. Anyone know how to run it?..........

**PB** - I installed *ClamAV* in the same way - the program showed up in my Applications -> Accessories menu; a right-click on the entry allowed me to set up a 'Launcher' on the desktop; to update the virus definitions (a number of options), I just go into a 'terminal mode', then type in 'sudo freshclam' - enter your password, then the updates occur.  Please let us know if this helps - thanks.

---

### Post by Giradman on 2007-12-21
> **pbmax said:**
> I thought that too, but irc.efnet banned me because my DSL's IP address was blacklisted due to a "Srorm Worm" infection.

I looked it up and it's windows only, but I decided to run ClamAV just to check what's up.

Now for the stupid question: in 7.10, I installed ClamAV with synaptic but can't find it in the menu. Anyone know how to run it?  thanks pb

Well, the Clam AV definitions include the 'tens of thousands' that affect the Windows OSs, so one of the main reasons that one might use the program on a Linux system is in exchanging e-mails, files, etc. w/ Windows users, i.e. to prevent the Linux user from passing virus-infected content or to notify a Windows user that the files/e-mails sent had a virus!  Of course, you can 'gloat' that the virus will have no effect on your Linux system! :)

When I installed Clam AV on my 7.10 system, the 'Virus Scanner' was added to the 'Accessories' menu under 'Applications' - I right-click and made a launcher to the desktop.

My current problem is that ClamAV has been updated (see screenshot below) and despite some Clam updates done today, the 'newest' version apparently was not installed - the terminal message below after I tried to 'sudo freshclam' to update the definitions - assume that this will be resolved w/ further updates?  But in checking my definitions, the date is 12/22 - probably as a result of today's updates? Oh well - :confused:

---

### Post by Schrodinger on 2007-12-22
Just to throw in my thought on the virus issue,
just because there are very few Linux/Unix virii out there does not mean that they do not exist, it also does not mean that they will not exist. Linux is still prone to Virii, keyloggers, etc... just like any other OS, where do you think hacking began? On Windows boxes? Nope, hackers started out on Unix/VAX, etc... systems- before windows even existed!!! They are out there and having good security in place is not something to be questioned but rather respected.

---

### Post by Schrodinger on 2007-12-22
Oh yeah, one more thought, have you also looked at Firestarter? Its a firewall that is availible in Synaptic, its very easy to use. Once again Linux has very strong security built in, but having these things is place is not a bad idea.

---

### Post by jken146 on 2007-12-22
> **Schrodinger said:**
> Oh yeah, one more thought, have you also looked at Firestarter? Its a firewall that is availible in Synaptic, its very easy to use. Once again Linux has very strong security built in, but having these things is place is not a bad idea.

Firestarter is NOT a firewall!  Iptables is the firewall that is already installed (all ports blocked) and firestarter is a GUI tool for adding rules to iptables.

---

### Post by Giradman on 2007-12-22
> **jken146 said:**
> Firestarter is NOT a firewall!  Iptables is the firewall that is already installed (all ports blocked) and firestarter is a GUI tool for adding rules to iptables.

Thanks - and I'll second the post above; *iptables* is built into the Ubuntu kernel in my understanding, but apparently is a pain to manipulate @ the terminal level (don't know personally, but I'm sure other 'experienced' users can respond); *Firestarter* permits changes to be made easily - I have the program installed, but have not used any of its features for my 'personal' single computer needs; important when you must regulate inbound & outbound traffic, e.g. needing others to have access to your computer files.

---

### Post by Ahunt on 2007-12-26
Hi everyone:

I just wanted to drop my two cents worth in here in support of Schrodinger. Every time the subject of virus scanners comes up on the forum someone has to say "forget about it - there are no Linux viruses".

There are two very good reasons to install and run a virus scanner on Ubuntu or any other Linux system:

1. You can pass Windows viruses along to Windows users.

2. There _**are**_ viruses written for Linux and they are out there "in the wild" now. Have a look at:

[http://www.cbc.ca/technology/story/2007/06/11/badbunny-worm.html](http://www.cbc.ca/technology/story/2007/06/11/badbunny-worm.html)
[http://www.symantec.com/enterprise/security_response/weblog/2007/06/bad_bunny.html](http://www.symantec.com/enterprise/security_response/weblog/2007/06/bad_bunny.html)
[http://www.symantec.com/security_response/writeup.jsp?docid=2007-052400-3656-99](http://www.symantec.com/security_response/writeup.jsp?docid=2007-052400-3656-99)

Why would anyone bother to write viruses when there are so few desktops running Linux systems? Because there are lots of servers, palms and cellphones running Linux. Makes it a worthwhile target.

Protect yourself and those you e-mail to - get a virus scanner. Both ClamTk and AVG are available for Ubuntu (there may be others too).

---

