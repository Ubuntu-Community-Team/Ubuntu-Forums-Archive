---
title: "virus question"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-02-07
HI all,
    I was hoping to get some very specific information about how different types of viruses work/don't work in a linux environment. 
    Most people say that linux/mac/unix systems are so much safer (more virus free) than windows systems. Unfortunately, there is no real explanation that comes with these statements. The one thing that I do sort of understand is that most viruses will not work on anything other than windows because they have been designed for the windows architecture. Other than that are there any other reasons why they are not able to infect other systems (linux,unix or macs)? 
   The other thing that has been said is that surfing the net is so much safer because you avoid spyware and the likes. For example if I was to visit a porn site using a windows (i.e. IE or any other windows browser), I would get rouge cookies and malicious javascript that would load onto my system. As a result, various things could happen; viruses being loaded, spyware being loaded etc. Does this mean that malicious scripts are rendered useless on *nix systems? And if so why? I mean if I have malicious javascript in my cache how would I know that I am safe?

Sorry for the long question. Its just that I would like a substantial answer rather than the whole linux is safer and better..without any reasons. 
    

thanks

---

### Post by paulmilliken on 2006-02-07
My understanding is that the reasons are:
1.  most viruses are designed to exploit windows systems
2.  because there are more windows systems on the internet, the viruses spread more quickly
3.  Linux and other Unix systems have file ownership and file permissions so that a non-root user cannot perform certain operations
4.  There are fewer vulnerabilities in Linux and the vulnerabilities that do exist get fixed more quickly due to the fact that the source-code is available for all to see.

---

### Post by blair on 2006-02-07
Generally, the attack must specifically target a vulnerability that is environment (i.e. OS) specific. So an attack against one OS does not automatically work against another OS due to differences in the OS. 

The following is an excellent article I saw referenced in an earlier post in these forums:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

---

### Post by Bone Down on 2006-02-07
These might help you out..

[one article]("http://www.channelregister.co.uk/2005/04/07/linux_windows_quocirca/")

[I found this interesting read.]("http://www.theregister.co.uk/security/security_report_windows_vs_linux/")

[this one covers some virus some security.]("http://www.theregister.co.uk/2005/02/16/linux_security/")

---

### Post by Theely on 2006-02-08
I have never worried about viruses since I installed a Linux OS, it makes me happy. On the other hand though! I'm always worried about remote hackers. No one has ever gotting into my system before but in Linux I can actually see them try!! Its nutty. At times I wish there wasn't a sercure log in the var/log/ folder but now I'm addicted to looking at it like a poor reality show :p :p :p

---

### Post by Packard Dell on 2006-02-08
So what if let say in the near future, majority of PC are linux and Windows starts to vanish, well of course linux is the new target of these threats! Do you think linux will still be safe and **FREE**?
> 4. There are fewer vulnerabilities in Linux and the vulnerabilities that do exist get fixed more quickly due to the fact that the source-code is available for all to see.
in my own opinion, i think there is also disadvantage of having the source code available for all to see because anyone can study deeply the architecture of linux and hack it. Like they say, every software has a backdoor.

---

### Post by kaamos on 2006-02-08
But if 100 people are studying the program and 5 of those are looking for vulnerabilities to exploit, it's a pretty good chance the other 95 find and patch up the vulnerabilities before they could be used.

---

### Post by Klaidas on 2006-02-08
[QUOTE=kaamos]But if 100 people are studying the program and 5 of those are looking for vulnerabilities to exploit, it's a pretty good chance the other 95 find and patch up the vulnerabilities before they could be used.[/QUOTE]

Good point. I was looking for this answer, why open-source gets less viruses :)

---

### Post by az on 2006-02-08
[QUOTE=paulmilliken]My understanding is that the reasons are:
1.  most viruses are designed to exploit windows systems[/QUOTE]

A virus is a specific kind of vulnerability,  There are many other kinds of vulnerabilities.  What is specific to windows is that there are several ways to get code to be executed, as mentined previously in this thread.


[QUOTE=paulmilliken]2.  because there are more windows systems on the internet, the viruses spread more quickly[/QUOTE]

Well, there are more servers runnning apache on the net and a lot of them run linux.

[QUOTE=paulmilliken]3.  Linux and other Unix systems have file ownership and file permissions so that a non-root user cannot perform certain operations[/QUOTE]

Not really an issue.  If you run your windows box like this you are still more vulnerable.  But anyway, the most common exploit is to use a buffer overflow which can make your offending code be run as root.  This holds for any operating system.

[QUOTE=paulmilliken]4.  There are fewer vulnerabilities in Linux and the vulnerabilities that do exist get fixed more quickly due to the fact that the source-code is available for all to see.[/QUOTE]

Well, we hope so.  There really is no fair way to assess this, head to head.

The fact that there are centralised repositories is great.  The fact that linux operating systems is heterogeneous (not every linux distribution ships with the same apps - or the same version of apps) helps.  The fact that linux tries to do less for you out-of-the box helps.

---

### Post by Jimmey on 2006-02-08
Sorry for hijacking, but I've often wondered about Linux viruses myself.

It's clear that Linux/Unix is becomming increasingly popular - And it's not hard to see why. I installed it a couple of months back, and in that time, have helped my family to learn about it. Since then, my sister, with my help's installed Ubuntu, and my mum is increasinly interested in it's many benifits.

But, I read the article about viruses posted at The Register. It makes a point that a Linux virus, provided that it infected just one non-root user's account, would therefore be restricted to that persons files, and cannot mess up the system ( because of file permissions ). But, as my non-root user, I've been able to edit and delete files outside of my home folder. I've not really tried to delete/edit anything major ( for obvious reasons ), but I'm assuming that if I, as my user could edit/delete files outside of my home folder, so to could a virus? 

The only other conclusion I've drawn is that I, as a user, was able to do this, but a virus, as an executable, would be firmly restricted to /home/username. Is this correct?

Thanks

---

### Post by az on 2006-02-08
[QUOTE=kaamos]But if 100 people are studying the program and 5 of those are looking for vulnerabilities to exploit, it's a pretty good chance the other 95 find and patch up the vulnerabilities before they could be used.[/QUOTE]

That may be true, but you cannot say that is the case for every exploit.  Transparency helps, but it doesn't always work that way.

Free-libre software has a number of advantages that you can't really measure.  For example, a proprietary software maker may be commited to a given implementation of something and will have to go a lot further with it before ditching it for something with less vulnerabilities.  I think people who tend to use FLOSS are more flexible and are better able to pack up and move on to a different implementation of the same technology.

Likewise, the proprietary software maker may have to address vulnerabilities in a certain way, to preserve existing functionality, whereas the community approach can make it okay to use more creative workarounds or changes in the program.

Again, that's just meanignless talk - what speaks volumes is track record.  Paradoxically, your only as secure as your last big exploit.  Is linux more secure than Windows?  Probably.  Mac?  I dunno.  

I think it's in everybody's interest to be realistic about linux.

I'm still not worried about viruses and stuff in Ubuntu, though.

---

### Post by az on 2006-02-08
[QUOTE=Jimmey]

The only other conclusion I've drawn is that I, as a user, was able to do this, but a virus, as an executable, would be firmly restricted to /home/username. Is this correct?

Thanks[/QUOTE]


No.  A buffer overflow is when a program in memory writes to the memory that belongs to another process.  In this way, a non-root process can cause code to be executed as root.

But this is different from a virus.  However, we should be talking about security vulnerabilites in general, and not just viruses.

---

### Post by Jimmey on 2006-02-08
Does anyone have any security-oriented thoughts on Windows Vista? Will it be more secure? Or will, just because of the fact Windows is the most widely used desktop operating system, it sink into security hell?

---

### Post by gingermark on 2006-02-08
I think one other issue is the userbase.

Whilst I have no stats to back this up, it seems the majority of experienced Linux users are reasonably competent at securing their system. And most Linux n00bs have come from Windows, and one would think would have been reasonably competent there.

Just like AOL was blamed for bringing idiots on to the net (a bit before my time though), Windows is almost always the first experience people have with computers, whether at their library, at work, or wherever. These are the users that will click on those Adverts which are made to look like one of their OS' windows. And, I think to a certain degree such users help malicious software spread.

This is of course a huge generalisation - my point is I belive that there is a larger proportion of Windows users who don't know what they are doing (and have no desire to learn) then there are with Linux. And that is one contributory factor to the spread of malicious programs.

---

### Post by bartbes on 2006-02-08
[QUOTE=Theely] No one has ever gotting into my system before but in Linux I can actually see them try!! [/QUOTE]
Well that's why it is useful to use a firewall, *nix is less secure in that, because of a standard installed ssh server (sshd), I would recommend changing some settings there (especially the port number!)

---

### Post by az on 2006-02-08
[QUOTE=bartbes]Well that's why it is useful to use a firewall, *nix is less secure in that, because of a standard installed ssh server (sshd), I would recommend changing some settings there (especially the port number!)[/QUOTE]
The ssh client is installed on a base ubuntu system ao that you can ssh into another box  The server is not (sshd).  You have to install that yourself.  There you go.

---

### Post by bartbes on 2006-02-08
I can't remember installing it, but I do have it.

---

### Post by Leo_01 on 2006-02-08
[QUOTE=Jimmey]Sorry for hijacking, but I've often wondered about Linux viruses myself.

It's clear that Linux/Unix is becomming increasingly popular - And it's not hard to see why. I installed it a couple of months back, and in that time, have helped my family to learn about it. Since then, my sister, with my help's installed Ubuntu, and my mum is increasinly interested in it's many benifits.

But, I read the article about viruses posted at The Register. It makes a point that a Linux virus, provided that it infected just one non-root user's account, would therefore be restricted to that persons files, and cannot mess up the system ( because of file permissions ). But, as my non-root user, I've been able to edit and delete files outside of my home folder. I've not really tried to delete/edit anything major ( for obvious reasons ), but I'm assuming that if I, as my user could edit/delete files outside of my home folder, so to could a virus? 

The only other conclusion I've drawn is that I, as a user, was able to do this, but a virus, as an executable, would be firmly restricted to /home/username. Is this correct?

Thanks[/QUOTE]
a virus is a executable however there is 2 ways a virus can attack a user.
1) "giving" the virus access
2) Overflowing buffer via exploit

As for the first way it is highly unpossible as most disto comes with alot of softwares included and they can awalys use apt-get...\\:D/ (a new user don't really wanna mess around scripts and stuff like that...)

For the 2nd way is possible but open-sourcing and this whole community of linux hackers that release good fixes solve the problem...

pretty much all ways to get a virus on linux is highly impossible but it is still open for cracker attack. (you will need to close unused ports and have a good firewall to protect Linux from cracker attack...

---

### Post by johnyz on 2006-02-08
[QUOTE=paulmilliken]My understanding is that the reasons are:
1.  most viruses are designed to exploit windows systems
2.  because there are more windows systems on the internet, the viruses spread more quickly
3.  Linux and other Unix systems have file ownership and file permissions so that a non-root user cannot perform certain operations
4.  There are fewer vulnerabilities in Linux and the vulnerabilities that do exist get fixed more quickly due to the fact that the source-code is available for all to see.[/QUOTE]

Pretty much sums it all up.

---

### Post by Theely on 2006-02-08
[QUOTE=bartbes]Well that's why it is useful to use a firewall, *nix is less secure in that, because of a standard installed ssh server (sshd), I would recommend changing some settings there (especially the port number!)[/QUOTE]

Oh of course! Must change the default port and still have a firewall. I just think its semi-funny to view the brute-force attempts. This is course was happening before I knew about changing the port and how to block certain IPs.

On a side note, it was also fun to do a whois on the IP that was trying, even though it might not of been the actual IP of the "hacker"

---

### Post by m.musashi on 2006-02-08
[QUOTE=bartbes]Well that's why it is useful to use a firewall, *nix is less secure in that, because of a standard installed ssh server (sshd), I would recommend changing some settings there (especially the port number!)[/QUOTE]
So how many firewalls does an ubuntu user need? My router has a hardware firewall which, as I understand it, pretty much masks my computer to the world. Do I need a software firewall as well? In Windows the answer seems to be yes, but what about linux?

Also, can anyone explain about changing port numbers.

Thanks.

---

### Post by xequence on 2006-02-08
> So how many firewalls does an ubuntu user need? My router has a hardware firewall which, as I understand it, pretty much masks my computer to the world. Do I need a software firewall as well? In Windows the answer seems to be yes, but what about linux?


You really dont need a firewall on any OS unless you are paranoid, just want to be super secure, or run a server.

Ports? Well, they are what you connect to the internet through. I dont know if they are hardware or software, so someone else can say that =P

---

### Post by Jimmey on 2006-02-08
If you've got a router, there's two steps you need to take. 

The first step being to change the default port upon which a certain program operates - A quick example of this being vsftpd. By default, it runs on port 21, but you can configure it to run on any previously un-used port.

The second, router specific part is to change the port forwarding options. You've then to change the port which the router forwards to your networked PC in order for your program to work. A good guide for your router's most probably available at 
[www.portforward.com](www.portforward.com)

I myself am behind a router ( which, on a bad day, has 8 open ports ), using Ubuntu 5.10 with Firestarter. With Ubuntu, Firestarter's not really necessary, as ( from what I've heard ) it's just a user friendly GUI for IPtables. And so, an Ubuntu user would, at most, need one.

---

### Post by Virogenesis on 2006-02-08
you can use Firestarter for your firewall ubuntu comes shipped with no open ports.
So unless you start installing things like p2p you won't exactly need it but its suggested to use.
Firestarter is IPtables gui and its extremely easy to use.

Changing ports?....you won't need to change ports when they were talking about ports they were talking about listening ports such as a ftpd, mysql, httpd, sshd the chances of you running any of those pograms is unlikely and not suggested if you're new to linux.

Changing ports is also advised against as you are changing the importance of logging.
I won't go into advanced ways as it will just confuse you for now and its not needed for yourself.

---

### Post by az on 2006-02-08
[QUOTE=Leo_01] (you will need to close unused ports and have a good firewall to protect Linux from cracker attack...[/QUOTE]

By default, there is nothing installed that listens to the outside world.  If you install services that listen to the outside world and install a firewall because of that, you will still have to open those ports up.

Unless you know of a reason why you need a firewall, you don't need a firewall.  

It is assumed that you know what you are doing by installing software that listens to the outside world.

---

### Post by mwanafunzi on 2006-02-08
> ... A buffer overflow is when a program in memory writes to the memory that belongs to another process. In this way, a non-root process can cause code to be executed as root.

How is it possible that a program is able to do this? 

What happens with viruses such as ISTbar this or SlotchBar that install adware through the respective browsers? What prevents them from running on a *nix machine and what stops malicious javascript from running  on *nix machines.

---

### Post by az on 2006-02-09
[QUOTE=mwanafunzi]How is it possible that a program is able to do this? [/QUOTE]

The C language is very powerful because it is a low-level language.  You get to play around with memory yourself.  The advantage is that it is more efficient.  The dissadvantange is that, by having to do everything yourself, you make mistakes and forget things.

That's why some applications (like developmental versions of firefox) leak memory.  They just keep eating and eating memory because the memory it allocates for itself is not freed properly.

A common mistake is to allocate a space of memory for use and continue wtiting beyond the bounds you set up.  That's overflowing a buffer.

[QUOTE=mwanafunzi]What happens with viruses such as ISTbar this or SlotchBar that install adware through the respective browsers? [/QUOTE]

Internet explorer does not run on linux.

[QUOTE=mwanafunzi]What prevents them from running on a *nix machine and what stops malicious javascript from running  on *nix machines.[/QUOTE]

AFAIK, javascript is not able to do that in linux because of permissions.  There is also no such thing as active-X which is a framework by which the user is spared any of the decision-making in things like software installation and so forth.  Others would be better informed about this than me.

---

### Post by ClareJonsson on 2006-02-09
Hia,
This is how I think it works:

One of the real reasons Linux doesn't get a virus is because of the sheer nature of the OS. i.e. it being open source. The kernel on each system is usually pretty unique, this is why you can't just install software on your system like you can with windows. With Windows, the code is simply standard win32, but with Linux the program has to be compiled for your kernel. Usually when you run Linux, you're not logged in as root, so to compile anything you would be prompted for root permission etc.

A virus attempting to invade a Linux system would have to recompile itself for your kernel. If some bright spark did write code that launches such an install/compile, you would be asked for the root password, and therefore you're instantly alerted something is going on!

If I'm wrong here, please someone let me know :neutral: .

Clare.

---

### Post by bartbes on 2006-02-09
looks like you're right..

I'm using my firewall because I have installed a test-webserver to test my site first before putting online and as you can read ssh-server. I'm also running Courier (mail server) but I haven't got it to work. Also I want to ask where to find those logs..

---

### Post by az on 2006-02-09
[QUOTE=ClareJonsson]Hia,
This is how I think it works:

One of the real reasons Linux doesn't get a virus is because of the sheer nature of the OS. i.e. it being open source. ...[/QUOTE]

The fact that it is open source in of itself means nothing.  As It has been said before, the open source model *can* be more secure than other models, but this is not measurable.  More eyes looking at the code can be a good thing, but nothing can guarantee that it will work 100 percent of the time.  Ther eis no black-and-white concrete proof that one methos is more secure than the other.  Period.

This is an important thing to say, since to make unfounded claims tends to make people consider linux less seriously.

[QUOTE=ClareJonsson]
The kernel on each system is usually pretty unique, this is why you can't just install software on your system like you can with windows...[/QUOTE]

The kernel and userspace are two different things.  The kernel abstracts the userspace applications from the hardware.  Most userspace applications have no idea and don't care about the kernel.

However you are talking about binary compatibility.  Binary compatibility applies to userspace tools just like the kernel.  Something compiled for one distribution probably won't work on another distribution because configurations are different and shared libraries are of different versions.  However, you can still compile something that will run on any system that uses libc6.

So what you are saying is mostly true, except that is has no bearing on security since a malicious apllication will not use shared libraries.  


[QUOTE=ClareJonsson] With Windows, the code is simply standard win32, but with Linux the program has to be compiled for your kernel. Usually when you run Linux, you're not logged in as root, so to compile anything you would be prompted for root permission etc..[/QUOTE]

No for the kernel version.  No for the permissions thing, since windows has exactly the same permissions setup - although some do not chose to use it.  Most security flaws are in regards to code inadvertently being given root priviledges.

[QUOTE=ClareJonsson]
A virus attempting to invade a Linux system would have to recompile itself for your kernel. If some bright spark did write code that launches such an install/compile, you would be asked for the root password, and therefore you're instantly alerted something is going on!.[/QUOTE]

No.  I think a linux desktop is more secure than a windows desktop for different reasons that that.  There is no active X in linux.  Things are more transparent in linux.  There are many ways to do the same task in linux.  "Features" that are security risks are not usually kep around.  Etc...

---

### Post by ClareJonsson on 2006-02-09
Aha! I thought there was a flaw in my understanding :-|

---

### Post by sdamron on 2006-02-09
I know this has been beat on for awhile, but I have something to say...so...

I do network/computer security for a living...had to get that out off the bat.  The VERY LARGE Insurance company I work for runs some Linux, I have been a UNIX/Linux admin/user for the better part of 10 years.

Okay...Now to say what I started to say :o)

Linux is not less, or more secure than windows, both have regular exploits exposed, the BIGGEST thing that makes Linux better, is, if it is open source, it USUALLY gets the expoits fixed much faster.  Biggest reason is, there are MILLIONS of folks working on it, they can view source, and they may have found the problem, and fixed it already on their own system.  Being open, they contribute the fix back to the community, and presto...Bug/Sploit fixed!!  That said...you notice what I said at the get go on this post...I work in security, and I use Linux...nuff said\\:D/

---

