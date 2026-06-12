---
title: "virus question"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Mr.Ganja on 2007-07-30
i have these questions

some basic info: 2 disks, one has windows 2000 and linux, the second is a FAT 32 shared between the OSes 
i know the windows partition is read only while linux is running. 

could a windows virus on my linux partition infect  the windows partition?
could a windows virus write it's self to the shared disk and attack when i boot to windows? 

Im a little bit worried because i need the windows sometimes, and i dont really want it getting infected from my browsing the internet on linux. I mainly use linux anyways but windows is needed from time to time.  

Im also wondering if i need any security in ubuntu? I don't really care if it crashes but i dont want other people meddling in my stuff. :-(:confused:

---

### Post by syko21 on 2007-07-30
Most viruses exploit vulnerabilities in the way windows operates so you should be safe while on linux unless you specifically download a file that is infected onto your shared partition and then access the file again once you are in windows. If you were to download an infected file, with a windows virus, while on linux it would be completely harmless since linux would be foreign to it. As far as security is concerned a firewall should help curb any malicious activity, for ubuntu your best bet is firestarter.
```

sudo apt-get install firestarter

```
I'm blanking on which antivirus you should use since I don't use one on my ubuntu install. Perhaps someone else can fill that in here.

---

### Post by swoll1980 on 2007-07-30
Smoke one for me :guitar:

---

### Post by Mr.Ganja on 2007-07-30
im kind of worried about getting a fire wall

will it block me out from everything like  my windows firewall?
and constantly ask questions? 

i dont really know much about firewalls but my past windows experience wasn't pleasant

i just dont want to be limited

---

### Post by Mr.Ganja on 2007-07-30
haha yeah sure swoll1980:lolflag:

---

### Post by mcduck on 2007-07-30
> **Mr.Ganja said:**
> im kind of worried about getting a fire wall

will it block me out from everything like  my windows firewall?
and constantly ask questions? 

i dont really know much about firewalls but my past windows experience wasn't pleasant

i just dont want to be limited

With the default settings after installing Firestarter all incoming connections are blocked and outgoing ones are allowed. This is a good default and you don't need to change anything and you won't even notice the firewall in any way (unless you want to run some kind of server). Firestarter will not pop up any messages, and you don't even need to run the GUI program all the time, it's only needed for changing your firewall settings.

Anyway, as long as you don't run any server software on your Ubuntu machine you don't really need any firewall. There are no programs running that would respond to any incoming connections so it hardly makes any difference if you close ports or leave them open..

What comes to those Windows viruses, if you download infected file with Ubuntu it can stay on Ubuntu's partiton but the virus itself won't run on Ubuntu so they can't infect your Windows. Hovever when you access that infected file from Windows the virus can activate. But you should have a good antivirus installed on your Windows anyway so it should protect you in these situations.

---

### Post by Mr.Ganja on 2007-07-30
thanks mcduck:)

but i have this one question will the firewall try to stop downloads or sudo apt-get or anything like that?

i just want to know before i install the fire wall.

---

### Post by RomeReactor on 2007-07-31
Hi. Ubuntu comes with a firewall already installed (iptables). Firestarter is a graphical interface to manage iptables (which is itself a command line application). Installing Firestarter won't stop you from installing applications with apt-get, aptitude, Synaptic or Add/Remove, nor will it stop you from updating; Firefox will still work as usual, too. The only problem you might face is having to open ports for bittorrent applications (if you use them),  or other filesharing programs you have, as well as Evolution (if you use it to read your mail), or certain messaging protocols (like XMPP/Jabber, port 5222).

Otherwise, you should have no problem with it. Remember, Firestarter is **not** the firewall; just a configuration/monitor utility for iptables (the actual firewall).

As for an antivirus, you could go to "Applications->Add/Remove", change the "Show:" drop menu to "All available applications" and search for the word **virus**. Two virus scanners will show up: Aegis and Clam. I haven't tried Aegis, though. Install either one to scan your shared partition; viruses in your Ubuntu partition won't do anything.

---

### Post by mcduck on 2007-07-31
> **Mr.Ganja said:**
> thanks mcduck:)

but i have this one question will the firewall try to stop downloads or sudo apt-get or anything like that?

i just want to know before i install the fire wall.

There's no problem, as it's your computer that opens the connection in the first place.

If somebody tries to connect to your machine the connection is blocked, but if you connect to some machine the response is allowed.

other machine --> your computer - blocked

your computer --> other machine - allowed

your computer --> other machine --> your computer - allowed

This way you may need to open ports for filesharing apps to get max speeds, but they should work even without that. All normal Internet use workks without doing any extra configuration.

RomeReactor: It's quite wrong to call iptables a firewall, it's more a tool that provides services needed to create a firewall. But just iptables itself does absolutely nothing. You always need some script that uses iptables to create a firewall, and in default Ubuntu install there is no such script running. You can write that script yourself and make it run on every boot, or you can install some GUI tool like Firestarter to do the job for you. (Firestarter actually has 2 parts, the firewall script and the GUI used to change settings). So you could actually say that Ubuntu doesn't have a firewall by default. And like I already said, Ubuntu doesn't even need a firewall by default.

---

### Post by RomeReactor on 2007-07-31
> **mcduck said:**
> RomeReactor: It's quite wrong to call iptables a firewall, it's more a tool that provides services needed to create a firewall. But just iptables itself does absolutely nothing. You always need some script that uses iptables to create a firewall, and in default Ubuntu install there is no such script running. You can write that script yourself and make it run on every boot, or you can install some GUI tool like Firestarter to do the job for you. (Firestarter actually has 2 parts, the firewall script and the GUI used to change settings). So you could actually say that Ubuntu doesn't have a firewall by default. And like I already said, Ubuntu doesn't even need a firewall by default.

True; I often forget about that and make uneducated observations (twice in this case). I apologize. However, I think the rest of my points stand.

---

### Post by Mr.Ganja on 2007-07-31
so i installed firestarter. Then I ran the GUI thing for it and it came up with a setup wizard type thing. It's asking me about selecting a device, it's set for eth0 by default. Then it asks "Start firewall on dial out" a check box next to it
then it has a check box with  "IP adress is assigned via DHCP" written next to it 

I dont know what to do? If this description is insufficient then i will include a screenshot of the window.

---

### Post by mcduck on 2007-07-31
> **Mr.Ganja said:**
> so i installed firestarter. Then I ran the GUI thing for it and it came up with a setup wizard type thing. It's asking me about selecting a device, it's set for eth0 by default. Then it asks "Start firewall on dial out" a check box next to it
then it has a check box with  "IP adress is assigned via DHCP" written next to it 

I dont know what to do? If this description is insufficient then i will include a screenshot of the window.

What kind of Internet connection do you have? Do you have to configure your IP by hand or does it "just work"?

Dial Out is needed if you use modem or ISDN, it starts the firewall when you connect.

"IP address assigned by DHCP" means that you get your IP automatically from your ISP, and you don't need to configure it by hand. Most likely you'll want to enable this.

---

### Post by Mr.Ganja on 2007-07-31
it just works, so i think the DHCP is the right one. 

im kind of scared to try it, i dont want to mess with my connection too much. 
this may sound silly, but being a windows user for years just makes me shudder at a thought of changing such settings. But if i learned anything about linux these changes are reversible, right?

---

### Post by steve.horsley on 2007-07-31
They are reversible. But it is possible to configure such that you can't get to this forum to find out how to reverse it.

If you haven't installed any services like a web server, VNC server etc, then you don't need a firewall. The default Ubuntu install doesn't listen for incoming connections on any port number - no open ports even without a firewall. 

You only need ot think about getting a firewall running once you install a service that you want to prevent network connections to. Even then, since only the service you installed is listening, a firewall is only of use if you know which IP addresses you want to permit/deny - you don't need a fiirewall to restrict access to certain services, because only the services you deliberately installed are listening anyway.

---

### Post by Mr.Ganja on 2007-08-01
> **steve.horsley said:**
> They are reversible. But it is possible to configure such that you can't get to this forum to find out how to reverse it.

If you haven't installed any services like a web server, VNC server etc, then you don't need a firewall. The default Ubuntu install doesn't listen for incoming connections on any port number - no open ports even without a firewall. 

You only need ot think about getting a firewall running once you install a service that you want to prevent network connections to. Even then, since only the service you installed is listening, a firewall is only of use if you know which IP addresses you want to permit/deny - you don't need a fiirewall to restrict access to certain services, because only the services you deliberately installed are listening anyway.

So they way i understand this is that unless i have a network i probably don't need a firewall. So if i wanted to make a home network with another computer the firewall might get in the way? Or is it wrong? These things are confusing. And what if my ISP provides a firewall with the service? I think my provider does, or maybe not because the WinXP system i have needed a Mcafee firewall thing. Im not sure if it's a firewall or just a control panel for the provided firewall that comes with my service. I just don't want  my firewall to conflict the one provided by my ISP. (If any) I hope this isn;t too confusing.

---

### Post by lisati on 2007-08-01
So far I've found the firewall built in to my router and the Ubuntu defaults sufficient....with the added precautions of changing the admin passwords on my router & ADSL modem, along with enabling WEP & MAC access control on the wifi portion of my home network's setup.

---

### Post by Colro on 2007-08-01
As for an antivirus, I've heard good things about [ClamAV]("http://www.clamav.net/") -- It'll scan for windows viruses while on Linux. You really shouldn't need it as McDuck says, but if you're paranoid then go nuts.

---

### Post by sad_iq on 2007-08-01
> **Mr.Ganja said:**
> So they way i understand this is that unless i have a network i probably don't need a firewall. So if i wanted to make a home network with another computer the firewall might get in the way? Or is it wrong? 

The firewall will get in the way for your network only if you install it and try to share files with the other pc and forget to configure it(happened to me). The firewall your ISP offers is probably a downloadable one(they will probably charge you for it) that works for windows! The firewall will not mess with anything related to your ISP, it only works on your pc...your connection is not affected. Also if you have a router it comes already with a firewall installed witch should prevent anyone from harming you so that makes your firewall useless. Install a firewall only if you have a network with people you don't trust or install apps that need an opened port to work (bittorrent, emule...).Firestarter is a nice way to open ports, on your pc it will do nothing else as everything is already locked up! Also don't worry about your ISP, they can't see if you use a firewall or not, if it's theirs or not, they don't scan to see if your ports are opened or not. The ISP only provides you with the internet link and charge you for it(they are charging me for an firewall and antivirus every month despite me beeing windows free for a few years now).

---

### Post by steve.horsley on 2007-08-01
A firewall's job is to prevent or allow only selected network connections, with the decision based either on the remote IP address (e.g. only allowing known trusted machines in) or on the service (port number) being connected to (e.g. allowing only HTTP). But in the case of Ubuntu, there are no services running and listening that you might want to prevent untrusted people from connecting to, unless you install a service on the computer yourself. So filtering selected protocols/services is not needed. And until you install that service, allowing selected hosts to connect is meaningless too.

I would not trust the ISP's firewall. They might be compromised or inadequate.

---

### Post by Mr.Ganja on 2007-08-02
thanks! 

I think i will not install the firewall after all. I probably don't need it according to most i asked. Thanks once again for your advice and help. But i have new problem. 

I had my system *freeze!*:( After 2 months of smooth seamless operation it freezes forcing me to reboot using ctrl+alt+delete. (not the power button like windows) The circumstances were that i was logging out of a different account and the colours on the desktop went all screwy. So it logs out, puts me in the login screen. I try to switch to one of TTYs and bam it freezes. So i try to restart X using ctr+alt+backspace, nothing. Then i press ctrl+alt+ delete, and after a moment the login screen seems to move half way across the screen with another moving in from the left. After a few seconds the Ubuntu shutting down screen appears and the system reboots. This was posted right after it did it.

So being a little freaked out i installed clam antivirus using the instructions in the book *Beginning Ubuntu Linux* by Keir Thomas, thinking it's a virus. Okay it installs, the GUI app works, i update the signatures, Then try to scan. This error pops up. 

You do not appear to have virus definitions!
Running "freshclam -v" as root may fix the problem.

So i get into root using sudo su

run freshclam -v

This is the output

```
root@apeman-desktop:/home/apeman# freshclam -v
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Thu Aug  2 02:23:26 2007
Querying current.cvd.clamav.net
TTL: 90
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 3846
daily.cvd is up to date (version: 3846, sigs: 8937, f-level: 20, builder: ccordes)

```

So i don't know what happened there. But whatever it did it does not work the same error pops everytime i try to run a scan.  I also tried updating the signatures through the GUI app, it says my signatures are up to date, yet it still dosent work. Im going to reboot the system on more time and see if that fixes the problem. If it does i will post the changes. For now i need help.

---

### Post by lisati on 2007-08-02
I think rebooting won't remove the error message - it looks as though Clamav is reommending that you update to a newer version. Have you visited the website mentioned in the message - [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)?

---

### Post by Mr.Ganja on 2007-08-02
Haven't thought of that. 

Well i will tomorrow when my mind is fresh and rested, right now the instructions on the page confuse me, it being 4 am where i live im really sleepy.

(you were right reboot didn't work. Thought it would because in windows when you install new things most of the time you have to reboot to get them fully functional. Silly me) :redface:

---

### Post by Mr.Ganja on 2007-08-02
Okay, which packages should i install to update?

The list for Debian packages is at

[http://wiki.clamav.net/Main/DebianInstall]("http://wiki.clamav.net/Main/DebianInstall")

---

