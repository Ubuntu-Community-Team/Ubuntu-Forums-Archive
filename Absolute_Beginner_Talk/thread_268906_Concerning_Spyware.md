---
title: "Concerning Spyware"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-30
This is kind of a dumb question, but I'm going to ask anyways.  Does Linux get nearly as much spyware as Windows?  I know it doesn't get a lot of Viruses, but what about spyware?  

If Linux does get spyware how might one go about getting rid of it?

---

### Post by orb9220 on 2006-09-30
Nope because to install stuff on your system even you have to enter your password to do anything that has to do with adminstration.

---

### Post by ewl1217 on 2006-09-30
As long as you play it safe, spyware isn't an issue on an operating system. Just follow some basic security measures (for an operating system really) and you'll be fine. Use a firewall (Ubuntu includes one, called iptables, by default, but if you want, you can download an editor for it, like Firestarter) and never run untrusted software, especially as root (or with sudo in Ubuntu's case). With Ubuntu, or any other GNU/Linux, BSD, or similar UNIX-based OS, spyware is hardly an issue. Most spyware writers only target Windows, due to its large user base and fairly poor security.

---

### Post by Kingsley on 2006-09-30
as far as i know, linux has no viruses, spyware, or worms.

---

### Post by llamakc on 2006-09-30
There are linux viruses out there. Use a firewall, stay up to date with package updates.

[http://www.viruslibrary.com/virusinfo/Linux.htm](http://www.viruslibrary.com/virusinfo/Linux.htm)

---

### Post by ewl1217 on 2006-09-30
Duh... I knew I was forgetting something... that's what it was: updates.

---

### Post by nthdegree on 2006-09-30
GNU/Linux does not currently have known spyware that auto-installs on to your machine much like early Windows 98 machines suffered.  Windows XP suffers from spyware but it's software you have to install yourself, the same is for GNU/Linux.

A user cannot get spyware simply by surfing the web since all GNU/Linux distros by default use a limited account with NONE of the privileges required.  Provided a user stays up to date with security patches and bugfixes, there is little risk of exploits being used to place spyware on the system.

A user cannot get spyware by installing off official repositories either, since Ubuntu newbies aren't really able to compile software or add extra repositories Ubuntu remains pretty much secure by default against spyware through that route.

The only way a user can get spyware or malware is by installing from non-official repositories, compiling and installing untrusted software programs (ones not really known to the FOSS community) or by installing proprietary software in binary format which could potentially contain backdoors or spyware.

[NOTE:  *Firewalls have nothing to do with spyware.  Firewalls prevent malicious crackers from accessing network services that would normally be available to the Internet.  Since Ubuntu has not got any services listening on TCP/IP ports on Internet facing network adapters by default there is no need for a firewall unless in a corporate environment.*]

---

### Post by IYY on 2006-09-30
There was never any spyware at all on any Linux system in history. However, this does not mean it can't happen. Once you type your admin password, *anything* can be installed on your computer. So just be sure that what you install comes from a trusted source, and you won't have any problems.

---

### Post by llamakc on 2006-09-30
As much as you are correct that a firewall has nothing to do with spyware you're making quite an assumption about when firewalls should be used.

---

### Post by nthdegree on 2006-09-30
Ubuntu by default has no listening services that are on internet facing network adapters, if it did then there would be a fully functional firewall by default.

As I said it is only really needed in a corporate environment, unless a user goes and uses unsupported software or proprietary software that makes use of and/or configures components to listen on internet facing network adapter(s), in that case a user *should* be knowledgeable enough to either reconfigure the component to make it safe or deploy a firewall.

In corporate or small business environments a firewall can be used to isolate machines in the case of a virus attack, however on home networks most users use routers to supply all their machines with the Internet, which in 90% of cases automatically isolate each machine by default using NATed routing, thus meaning there would be no need for a firewall to be deployed on an Ubuntu install.

---

### Post by solarwind on 2006-09-30
> **llamakc said:**
> There are linux viruses out there. Use a firewall, stay up to date with package updates.

[http://www.viruslibrary.com/virusinfo/Linux.htm](http://www.viruslibrary.com/virusinfo/Linux.htm)

None that you'll come across for a long time, so don't worry. Viruses need admin privilages to run, just dont give untrusted apps your password.

---

### Post by sbergman27 on 2006-09-30
> **llamakc said:**
> There are linux viruses out there. Use a firewall, stay up to date with package updates.

Well, to be slightly nitpicky, all but 2 of those are actually worms.

A virus is code that can surrepticiously attach itself to an arbitrary executable.  It "infects" the executable file, and then that executable can infect others.

A worm is code that can take advantage of a known vulnerability in a network service, like a web server, and install itself on the vulnerable system.  Typically, it will then launch a search for other vulnerable machines and exploit them.

Another kind of exploit is a "trojan horse", or more commonly just "trojan".  It is simply a file that is put up for download that is supposed to do one thing, and usually does, but also does nasty things on the side.  It does not infect anything or propagate itself.  It is just what the name implies.  A trojan horse.

Viruses are the trickiest since they can infect arbitrary files and the file otherwise performs as expected.

Linux viruses do exist as laboratory curiosities, but are notorious for simply failing to propagate successfully.  Linux's attention to security and its general policy of not running things without the user's explicity instruction make virus propagation very difficult.

Linux worms do indeed exist and can propagate.  However they do require that the vulnerable machine have services listening on a publically visible network connection and that the service have some expoitable vulnerability.

Ubuntu does not, by default, have any services listening on the network.  And the automatic update facility is on by default.

That said, a hardware firewall is not a bad idea.  Other Linux distros come with a preconfigured software firewall based on Linux's iptables facility.  But Ubuntu does not.  I believe automatix has this available?

Trojans are potentially a problem for Linux.  Downloading from untrusted sources, you really don't know for sure what you are getting.  They are, fortunately, pretty rare.

All in all, Linux, the BSD Unixes, and Mac are virtually malware free in comparison to Windows.  In fact, the *only* OS that has had major problems with viruses are Microsoft operating systems, and of Microsoft operating systems, *all* of them have had problems going all the way back to DOS.

Whenever I hear the phrase "computer virus" it irks me.  Because the correct term is "Microsoft viruses".

---

### Post by Albi on 2006-09-30
Just tracking cookies, which is why I set my mozilla to ask before setting a cookie.

---

### Post by ijjz on 2006-09-30
> **sbergman27 said:**
> Well, to be slightly nitpicky, all but 2 of those are actually worms.

A virus is code that can surrepticiously attach itself to an arbitrary executable.  It "infects" the executable file, and then that executable can infect others.

A worm is code that can take advantage of a known vulnerability in a network service, like a web server, and install itself on the vulnerable system.  Typically, it will then launch a search for other vulnerable machines and exploit them.

Another kind of expoint is a "trojan horse", or more commonly just "trojan".  It is simply a file that is put up for download that is supposed to do one thing, and usually does, but also does nasty things on the side.  It does not infect anything or propagate itself.  It is just what the name implies.  A trojan horse.

This man knows what he is talking about.  

Be cautious on what you put on your box, and you will be ok.

---

### Post by aysiu on 2006-10-01
You might be interested in this thread: [What has been your spyware experience?](http://ubuntuforums.org/showthread.php?t=109278)

---

### Post by henriquemaia on 2006-10-01
A very nice explanation, [sbergman27]("http://ubuntuforums.org/member.php?u=126680"). I really enjoyed reading it.

---

### Post by nthdegree on 2006-10-01
"That said, a hardware firewall is not a bad idea. Other Linux distros come with a preconfigured software firewall based on Linux's iptables facility. But Ubuntu does not. I believe automatix has this available?"

Guarddog, firestarter and fwbuilder are all examples of software that can provide a firewall for Linux.  Automatix and EasyUbuntu are not the way to go, if a user is lazy and doesn't understand what he/she is doing it is asking for trouble.

A software firewall on Ubuntu based on it's default setup is unnecessary and may just become another way to exploit the machine itself.

As a general rule: firewalls should be on separate machines that filter the incoming traffic backed up by good intrusion prevention, otherwise if the firewall is installed on the main machine itself and it gets exploited then there may be data loss - whereas on a separate machine with good intrusion prevention all is safe providing the main desktop machine has no internet facing services.

---

### Post by llamakc on 2006-10-01
> **sbergman27 said:**
> Well, to be slightly nitpicky, all but 2 of those are actually worms.

A virus is code that can surrepticiously attach itself to an arbitrary executable.  It "infects" the executable file, and then that executable can infect others.

A worm is code that can take advantage of a known vulnerability in a network service, like a web server, and install itself on the vulnerable system.  Typically, it will then launch a search for other vulnerable machines and exploit them.

Another kind of exploit is a "trojan horse", or more commonly just "trojan".  It is simply a file that is put up for download that is supposed to do one thing, and usually does, but also does nasty things on the side.  It does not infect anything or propagate itself.  It is just what the name implies.  A trojan horse.

Viruses are the trickiest since they can infect arbitrary files and the file otherwise performs as expected.

Linux viruses do exist as laboratory curiosities, but are notorious for simply failing to propagate successfully.  Linux's attention to security and its general policy of not running things without the user's explicity instruction make virus propagation very difficult.

Linux worms do indeed exist and can propagate.  However they do require that the vulnerable machine have services listening on a publically visible network connection and that the service have some expoitable vulnerability.

Ubuntu does not, by default, have any services listening on the network.  And the automatic update facility is on by default.

That said, a hardware firewall is not a bad idea.  Other Linux distros come with a preconfigured software firewall based on Linux's iptables facility.  But Ubuntu does not.  I believe automatix has this available?

Trojans are potentially a problem for Linux.  Downloading from untrusted sources, you really don't know for sure what you are getting.  They are, fortunately, pretty rare.

All in all, Linux, the BSD Unixes, and Mac are virtually malware free in comparison to Windows.  In fact, the *only* OS that has had major problems with viruses are Microsoft operating systems, and of Microsoft operating systems, *all* of them have had problems going all the way back to DOS.

Whenever I hear the phrase "computer virus" it irks me.  Because the correct term is "Microsoft viruses".

Thank you for the elaboration. Since I haven't used Windows in eight years I'm ignorant about the language of viruses. To the point of my post: I was pointing out that if there is ONE virus, than there are such things as Linux viruses. That's all.

---

