---
title: "[SOLVED] How safe are the applications downloaded from torrents?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-08-02
Hi
 I wanted to know whether the applications(programs) downloaded via torrents are safe to work with in Ubuntu (Linux)?
   I know in Windows, they have a possibility of carrying malware, viruses, trojans etc.. but what about in Ubuntu? 

Also, is there a way to block (or reset to  default) all incoming connections (ports). I opened some (using a code in the terminal) for Bittorrent to work but dont remember all. 

Thanks in advance :)

---

### Post by nitro_n2o on 2007-08-02
I'd say don't install Linux software from torrent unless you are installing a distro you trust from their official site. Anyways, even if the software is harmful it shouldn't affect much if not run by sudo!! The internet and sourceforge.net is full of application to download from. 

for ports, i guess you should start with this [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html) and then move to blocking ports by googling iptables or ```
man iptables
```

---

### Post by jackmc on 2007-08-02
there arent too many (if any) viruses or malware for linux. There is a possibility though, depending on the way it is installed.

What programs would you need to download via torrent for linux?

---

### Post by Alexander2007 on 2007-08-02
> **genbuntu said:**
> Hi
 I wanted to know whether the applications(programs) downloaded via torrents are safe to work with in Ubuntu (Linux)?
   I know in Windows, they have a possibility of carrying malware, viruses, trojans etc.. but what about in Ubuntu? 

Also, is there a way to block (or reset to  default) all incoming connections (ports). I opened some (using a code in the terminal) for Bittorrent to work but dont remember all. 

Thanks in advance :)

Well torrents can carry malicious code, but currently most are aimed at Windows. So you can download torrents but remember to do so with caution (No OS is invisible). 
*Also for downloading torrents, i must recommend "Deluge" get it at: [http://www.getdeb.net/app.php?name=Deluge](http://www.getdeb.net/app.php?name=Deluge)
You can also find other great software for Ubuntu at: [www.getdeb.net](www.getdeb.net)

---

### Post by Jimmyfj on 2007-08-02
I'll agree with nitro - Don't install software from third parties unless you trust those as much as your distro's developers. Use the Add/remove or Synaptic to install new software.

As for virus and those kinds - I've run Ubuntu for about eight months now and not one time have I had any problems like the ones Windows are so famous of. I don't even have a working antivirus scanner installed. Tried ClamAV but it doesn't work so I un-installed it again.

---

### Post by genbuntu on 2007-08-02
Hi

 First, I must admit that I was quite frankly surprised by the speed of your responses. Wow, it was faster than if I'd have called some technical support guys. (This lightning support pulls a linux newbie like me even more closer to  linux) :D

 I was thinking of trying crossover for ms-office; but judging by the responses, I guess I should better be safe than sorry.
In case you are wondering whether I tried wine for that purpose - Yes I did but the installation closes unexpectedly (at later stages). don't know why ? (ms-office version is 2003.)
 The reason for my wanting to use ms-office than open-office is because I have many files in ms-word (like CVs etc) which lose their formatting when I open them in Open-office. If anyone has a better solution to the formatting problem, I'll be happy to hear.

 :)

---

### Post by Claus7 on 2007-08-02
Hello,

crossover office is working pretty nice to me, except from some minor issues, for example it is a little bit slower than the office counterpart, yet as you say is doesn't change the format, so for doc files you can open them pretty nicely. And I do not think that the doc files have such a high risk for virus attack. 
As far as the version of office you are talking about I use an earlier one, so this might cause some problems. From their site :
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

I can see that they support the version of office you have. Do you have the latest version of crossover?

Regards!

---

### Post by genbuntu on 2007-08-02
I haven't downloaded crossover yet, but I guess they'll give me the latest version for trial. 

 I found another new application- Wine-doors. Don't know much detail but I'm guessing it should also be able to run ms-office.
Is it the same as wine? (cause I was unsuccessful with wine before).

---

### Post by Alterax on 2007-08-03
I trust execurable binaries, shell scripts, or source code from torrents about as much as I trust a sandwich I found on the street.  May look good, but if I don't know where it's been, I ain't touching it...

---

