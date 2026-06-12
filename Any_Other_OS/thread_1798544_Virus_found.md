---
title: "Virus found"
date: 2011-07-06
forum: Any Other OS
---

### Post by abnordude on 2011-07-06
Well, I was in Facebook.
I decided to scan the system.

I found a virus.

Well, it read

Something called "asp.ace 4".

Well i Googled and found out that it is a backdoor or something which steals information.....

I just wanted to know whether my system was safe, or was I hacked or anything else.

Please help me.

P.S the virus was in the Google chrome folder.

---

### Post by haqking on 2011-07-06
it is a trojan usually associated with MS platforms ?

are you in ubuntu ? or do you have a Windows partition where the scan may have found it from ?

---

### Post by abnordude on 2011-07-06
I'm currently in linux mint.

And I dont have windows in my computer.

---

### Post by haqking on 2011-07-06
so what AV were you using ?

can you show the output ?

location etc of said trojan ?

---

### Post by abnordude on 2011-07-06
I'm using clam av.

Well.....
About the output,......

I deleted the virus, and closed the clam av window.

So I don't have it. unless there is a way to open the details..

I  just wanted to know,
whether my PC was infected during the time the virus was present..

Could any hackers have gotten any of the details that is stored in my computer or stuff like that.

---

### Post by haqking on 2011-07-06
Well just because a trojan or virus may be present does not mean you were infected, in linux viruses and trojans are very rare and though a windows virus can be present in a file local to your machine which an AV will find and treat such as ClamAV it does not mean it was doing harm to your machine.

this is current list of known virii and trojans which are known (very very very rarely) to infect Linux.

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

I suspect it was a false positive or if it was present i doubt it was causing any harm and just happened to be found by your AV.

The fact is though possible it is extremely rare for a virus or trojan to cause a linux system issue due to its security model. but then saying that, things change everyday ;-)

---

### Post by abnordude on 2011-07-06
So, It means that my system was not hacked. right.?

---

### Post by 3xp10r3r|X13 on 2011-07-06
definitely not hacked!  As already mentioned, you somehow downloaded a trojan (doesn't really matter how you did it) and it was stored in some file. Because of it probably being a trojan.exe file, you cannot execute it in the first place. If there actually is a virus for linux out there, it only depends on you being logged in as root or not. (all in all, you are probably save) 

However, clam av is also often used to scan windows drives, which means that it is able to locate/identify viruses which run only on windows systems as well.

further questions?

---

### Post by perspectoff on 2011-07-06
> **haqking said:**
> 

The fact is though possible it is extremely rare for a virus or trojan to cause a linux system issue due to its security model. but then saying that, things change everyday ;-)

From Wikipedia:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

"The number of malicious programs — including viruses, Trojans, and other threats — specifically written for Linux has been on the increase in recent years and more than doubled during 2005 from 422 to 863."

Small number compared to the Windows world, but that was 6 years ago. Also, a "system issue" is not the problem with malware -- it is the unseen transfer of data from a computer to an external location.

The biggest threats, IMO, are backdoors. It is somewhat trivial to write a backdoor into any program.

The Linux system of firewalls is one of its weakest points -- port-based firewall security is archaic. The problem, of course, is that the alternative (deep-packet inspection) is its own type of security risk unless the security program is absolutely trusted.

Also a lot of folks say "Linux" but the security risks are actually from applications. (Linux doesn't label it's executables .exe or .dll. Any program or script of any name can be executable if given permissions. It is the permission architecture that affords a measure of security. That can disappear completely, though, if there is a keylogger trojan on your system, especially a keylogger with a backdoor.)

A huge risk for Windows users was the browser application -- Internet Explorer. After all, the browser is the biggest portal to the Internet and is the most likely site of entry of malware.

Browsers run Java, Javascript, Flash, and usually display many cross-scripted locations.

On average, Linux is secure. The bigger question is how secure are the browsers (Firefox, IE, Safari, Chrome/Chromium, etc.) Those are the riskiest points.

Use NoScript and AdBlock, at the mimimum, if you'd like a modicum of control.

---

### Post by abnordude on 2011-07-06
I ran clam av as root while performing the scan.

Hope it's okay to do so.

---

### Post by perspectoff on 2011-07-06
> **abnordude said:**
> I ran clam av as root while performing the scan.

Hope it's okay to do so.

You have to do a large number of things with root permission in Linux. Debian/Ubuntu/Kubuntu uses temporary root-level privileges with sudo so you don't stay logged on as root, but it is still root-level permission.

Doing something with sudo has the same risk as doing something as root. It can't be avoided, though.

Logging on as a root user, doing something, and logging out is not any less risky. The problem has been that people forget to log out as root, and doing routine things logged in as root was considered the risk. That's why the sudo mechanism was created.

You'll hear all kinds of people who don't understand this who'll warble about how dangerous it is to do anything as root. Stuff and nonsense. Anything central to the computer must be changed as root, in one way (e.g. sudo) or another.

---

### Post by abnordude on 2011-07-06
> **perspectoff said:**
> You have to do a large number of things with root permission in Linux. Debian/Ubuntu/Kubuntu uses temporary root-level privileges with sudo so you don't stay logged on as root, but it is still root-level permission.

Doing something with sudo has the same risk as doing something as root. It can't be avoided, though.

Logging on as a root user, doing something, and logging out is not any less risky. The problem has been that people forget to log out as root, and doing routine things logged in as root was considered the risk. That's why the sudo mechanism was created.

You'll hear all kinds of people who don't understand this who'll warble about how dangerous it is to do anything as root. Stuff and nonsense. Anything central to the computer must be changed as root, in one way (e.g. sudo) or another.

yes. but, supposing that i run clamav as root [by using gksu clamtk] and then scan for virus.
Will my system get infected if a virus is present, since I'm now root.

---

### Post by abnordude on 2011-07-06
> **abnordude said:**
> yes. but, supposing that i run clamav as root [by using gksu clamtk] and then scan for virus.
Will my system get infected if a virus is present, since I'm now root.

Please answer, anyone.

---

### Post by Perfect Storm on 2011-07-06
Moved to Other OS/Distro Talk.

---

### Post by Dangertux on 2011-07-06
> **abnordude said:**
> Please answer, anyone.

Long story short that's not really how it works. 

A program executes with the privileges of the user that executes it. So if you are root, and you execute a ClamAV scan , ClamAV is now running with root privileges.

However, if ClamAV scans a file (which is not the same as executing it). The file will not inherit your root privileges (usually). So the bottom line is, no, you will not become infected this way.

If in fact it was a Windows Trojan (I didn't look up what the file mentioned was related to I'm using the general consensus of the thread) ; then even if it was executed as root on a Linux system it would likely fail, and by likely I mean it will fail. 

Now -- If you were to execute a Linux based Trojan as root you might find yourself having some problems. The wonderful caveat to that is that unless someone wrote a program specifically for you it probably wouldn't work. Linux malware is very poorly maintained and is more often the not proof of concept rather then effective live Malware for use on actual targets. Newer distributions are not as prone to the older malware threats which are out there.

This is NOT however to say that you are 100% secure because you are using Linux , far from it. As someone mentioned above Linux is as vulnerable to root-kits and backdoors as much as any other operating system.  Especially once you start getting into payloading legitimate executables (a method used to avoid anti-virus detection). However these methods usually signify that someone is targeting YOU specifically. As opposed to a random file you downloaded on the Internet, which works on law of averages to infect as many systems as possible. In cases like that Linux keeps you from being a statistic.

A side note on the person who mentioned DPI. While I agree DPI does have its advantages over traditional firewall methodology DPI is a little bit overkill for a home user IMO. Also a side note iptables is more then capable of becoming a stateful firewall rather easily (not to be confused with Deep Packet Inspection). So I think that the statement about iptables being archaic is oversimplified. Iptables in GUFW's default configuration may be archaic (although effective for most users) , however this does not change the potential the underlying iptables modules have.

Just my 2 cents.

---

### Post by abnordude on 2011-07-06
Thanks..

I was worried about my security.

Now, tis' all right.

Thanks everyone for your help.

---

### Post by 3xp10r3r|X13 on 2011-07-06
Sure it is, it is even necessary to do so, because as a standard user, you wouldn't be able to scan your system directories.

The thing about the root user I talked about:

If you were generally logged in as root the program/trojan would have the right/permission to execute itself and harm the system. As a standard user, it needs your permission.


Edit: Dangertux already went into it (with a bit more detail :) )

---

