---
title: "Internet DNS Still Slow!"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by richpor_1 on 2006-12-31
Hello all again, 

well, I've done everything I could find in the forums, I've disabled IPV6 (and all the alias'), done the modprobe thing, downloaded swiftfox and installed it,  and tried everything else, DHCP, static IP, you name it... BUT THE INTERNET CONNECTION STILL SUCKS.

Everything is two to three times faster in XP,  Could this be something to do with tweking the "rwin" settings or "mtu" settings that I did in XP to optomize for high speed.  

I don't seem to have any speed problems downloading packages, but the problems seem to have more to do with DNS resolution- and yes, I've done the change to the "prepend host" line (in whatever file, I can't remember)..

Is there any way to get ubuntu to resolve the DNS names as fast as XP?:confused: :confused: :confused: :confused: :confused: 

Thanks in advance...

---

### Post by hyper_ch on 2006-12-31
Try disabling IPv6... there's a howto for that... Try this here [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) and if that doesn't work use the search function of this forum to find alternate ways...

If you are behind a router that does not understand IPv6 then it will massively slow down connections... this happened at my mom's place... after I have disabled it it works like a charm... however at my place I was not required to disable IPv6...

---

### Post by richpor on 2007-01-01
IpV6 is off and Swiftfox still takes 3 to 4 seconds to reslove Google.com... XP does it in less than .4 of a second!  Can anyone help me any further with this?

Thanks,](*,) ](*,) ](*,)

---

### Post by bmt on 2007-01-02
Just a 'me too', I'm afraid.  I'm sure Ubuntu never used to be this slow.

As noted above, DNS resolution is the bottleneck: 4~5 seconds in Ubuntu; less than 1 second in Win2k.  The Ubuntu time was about 10 seconds until I blacklisted IPv6 this week.

These times are similar in Opera and Firefox on both OSs.  Similar delay in getting mail addresses (Claws-Mail) resolved, too.

Any ideas how to diagnose where the hold-up is, please?

---

### Post by r4ik on 2007-01-02
Please post you're /etc/resolv.conf

---

### Post by r4ik on 2007-01-02
Oke here is why i ask and it solved my problem.


When you ask for [www.someut.com](www.someut.com), your computer asks the internet what IP number is associated with [www.someut.com](www.someut.com). A network can only speak in IP numbers, which look like 64.124.112.18 .

It your case, you ask for [www.someut.com](www.someut.com) and Debian asks the DNS servers (listed in /etc/resolv.conf) what the IP number is. Something is wrong with the first DNS server, so you have to wait for that to time out and then try the next one. That's the delay.

Edit /etc/resolv.conf (with kwrite/gedit) and remove that spurious 'search private' line. Then put a # in front of the router's IP to comment it out, and add these lines after it as an experiment:
nameserver 68.87.66.196
nameserver 68.87.64.196

Then save the file. No need to restart anything in this case to make the change take effect, although this case is the exception.

Now try browsing. Should be instant. If not, there's an IPV6 problem.

The nameservers you put in your resolv.conf files are near me (Seattle), and you'll want nameservers closer to you for internet ecology. Edit the file again, remove my nameservers and put in your router's IP. Save and try surfing. If it works fine, your router is acting as your nameserver, and for IP's it does not know, it passes the request to the nearest higher-ranking nameserver, and it knows about the ones near you. 

It is Debian but worth a try and reversable.

Edit: credits go to quantum on the debian forum

Good luck !

---

### Post by bmt on 2007-01-02
But my /etc/resolv.conf file contains only the two OpenDNS nameserver IPs.  They are refreshed on boot by the router (where they are manually entered -- not obtained from the ISP).

OpenDNS has recently (in the last couple of days) gone live with their London service, so things should have speeded up ...

---

### Post by r4ik on 2007-01-02
I noticed the dns refresh on boot it gives me only one nameserver when i add the 
same dns things seem to speed up.
Until reboot.
The numbers are identical have to find a way to keep them there or set the router to it.
I even bought a 125Mbps router to speed things up with no succes.
So i would not be to hopefull about the "London" service.
I am going to set it manualy until a solution is found it irritates me.

---

### Post by r4ik on 2007-01-02
Please read,

[http://www.ubuntuforums.org/showthread.php?t=330189](http://www.ubuntuforums.org/showthread.php?t=330189)

For some more advice.

---

### Post by richpor_1 on 2007-01-03
> **r4ik said:**
> Please post you're /etc/resolv.conf


The only things in there are

Nameserver 201.xxx.xxx.xxx
Nameserver 201.xxx.xxx.xxx

Which are the two bell DNS servers...:-?

---

### Post by bmt on 2007-01-03
The delay is before the DNS servers are queried, in my case.  If I enter a web address in the browser, it takes those 4 seconds or so before the router port lights start to flicker -- so I think it's a localhost problem, rather than slow Internet DNS performance.

From the terminal, ping an IP address and there's no delay; ping a name and the same delay is there at the beginning, then the ping responses are fine (and quick).

---

### Post by richpor_1 on 2007-01-03
So, have you managed to find a way around it?  

I have no problems with speed, just seems to be realted to the DNS lookups.  I have not looked at the router to see if the lights differ from a dns look up to a direct ip address, but I'll try the ping thing tonight.

---

### Post by simonsimon on 2007-01-05
First post...sorry if noobish.

I am having what I think is the same problem.  

When I ping [www.yahoo.com](www.yahoo.com) or enter [www.yahoo.com](www.yahoo.com) in Firefox everything is PAINFULLY SLOW.

If I ping 209.73.186.238 (this is yahoo.com) or put that in Firefox everything is pretty much instant.  

This is day two of Ubuntu for me and I'd love to stick around and try it out but I may not have an intact head if I have to put up with Firefox being this slow for another 24 hours.

Also...I've done the fasterfox and ipv6 stuff already as well.

---

### Post by simonsimon on 2007-01-05
OK.

[THIS]("http://www.ubuntuforums.org/showthread.php?t=241576&highlight=ping%2Bproblem") seems to solve my problem...for now.  We'll see.

This may be totally unrelated to your problem as I'm a total noob and have no idea what I'm talking about.

---

### Post by bmt on 2007-01-05
> **simonsimon said:**
> This is day two of Ubuntu for me and I'd love to stick around and try it out but I may not have an intact head if I have to put up with Firefox being this slow for another 24 hours.
Hang on!  I think DNS caching is the answer (it has been for me, anyway).  I have written a How-To -- just waiting for it to be moderated and (hopefully) appear in the appropriate forum.

Edit to say, I'm already using the OpenDNS servers (208.67.222.222 and 208.67.220.220) and I can't see how locking the resolv.conf file could help.  It's only written at boot and if everything else is set correctly, it should be written correctly, too.  Mine is written from the router information (which is the LAN DHCP server) at boot and it is always written the same.

---

### Post by bmt on 2007-01-06
My How-To is now [here]("http://www.ubuntuforums.org/showthread.php?t=331850").

Using pdnsd to provide DNS caching has given me similar performance in Ubuntu compared with what I had in Windows.

However, if I disable DNS caching in Windows, the performance doesn't degrade as much as Ubuntu without the caching.  So there's still something adding overhead to Ubuntu, but I've no idea what that could be.

---

### Post by Hachi on 2007-01-06
Hey guys, I though I had the same problem, but my problem was that the IP for my wireless router was in the DNS settings. 

So when the wireless router was turned of my machine still tried to query that address, and because it was placed before my usual DNS addresses it slowed DNS down by checking it. Once removed all was back to normal speed :) 

System>Administration>Network Settings>DNS

Don't know if this helps anybody, but it's worth a check.

--------
Hachi

---

### Post by richpor_1 on 2007-01-07
> **bmt said:**
> My How-To is now [here]("http://www.ubuntuforums.org/showthread.php?t=331850").

Using pdnsd to provide DNS caching has given me similar performance in Ubuntu compared with what I had in Windows.

However, if I disable DNS caching in Windows, the performance doesn't degrade as much as Ubuntu without the caching.  So there's still something adding overhead to Ubuntu, but I've no idea what that could be.

I'll give it a whirl some time this week.

Thanks for the time putting the information together... I'll let you know how it works for me!
:D

---

### Post by meleeglow on 2007-01-07
I think I am having this problem to, though I am not as IP Savy, I just know that my internet is really slow for app downloads, haven't noticed it on HTTP though

---

### Post by richpor_1 on 2007-01-08
*bump*

Any Mods able to chime in here... Is there a bug reported for this problem??

Thanks,

---

### Post by richpor_1 on 2007-01-10
Well, tried this on edgy 64 bit and no go, here;s what happned...

Starting proxy DNS server: pdnsdError in config file (line 70): comment without closing */
 (failed).
invoke-rc.d: initscript pdnsd, action "start" failed.
dpkg: error processing pdnsd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pdnsd
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@workshop:~$ 

Any other ideas?

---

### Post by bmt on 2007-01-11
> **richpor_1 said:**
> Starting proxy DNS server: pdnsdError in config file (line 70): comment without closing */
 (failed).
Read the error message: you've made a mistake in editing the pdnsd.conf file and left a comment start marker without a corresponding end marker.

Correct that and try starting pdnsd again.  The other problems may disappear or not.

---

### Post by G Morgan on 2007-01-11
If your system is struggling to resolve addresses try entering this at the command prompt.

#sudo su
#echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

Then try and see if the problem persists.

//edit you have to sudo su btw. You can't perform that command as sudo.//

---

### Post by bmt on 2007-01-11
> **G Morgan said:**
> #sudo su
#echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
Mine is already on (according to powertweak) -- I haven't changed it, so I presume that it's the default setting.

---

### Post by LaVache on 2007-01-23
As others mentioned, have a look at /etc/resolv.conf

If you're on a DCHP network, the file probably looks something like this:

search sometexthere.com
nameserver 1.2.3.4
nameserver 2.3.4.5

but with different values in the second column.

Whats likely happening is that the DNS delay is due to the first line, where it first searches that given domain for the DNS query before going to the listed DNS servers.

To test if this is your problem, edit the file and comment out the search entry (but leave the other entries as-is):

#search sometexthere.com
nameserver 1.2.3.4
nameserver 2.3.4.5

(Notice the '#'; this comments-out the line).

Be sure to save the file; you'll need to edit as root (sudo) in order to have proper permissions to save it. 

Now load your browser and enter a domain which previously gave you problems.  If the domain now loads instantly, then the "search" line in /etc/resolv.conf was your problem.

Hope that helps.

(PS - The above fixed the dns delay problem for me.)

---

### Post by r4ik on 2007-01-25
Here a link worth to try,

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

Option 2 worked for me.

Good luck.

---

### Post by Data Doctor on 2007-08-10
Try this solution:

Ubuntu is having difficulty with DNS because of miscommunication with your router (related to wrong ports).

Establishing a direct DNS connection solves the problem. No need to disable IPv6!

1. Find your DNS servers. You may need to check your router settings (usually 192,168.1.1 or 192.168.0.1). Look for a status tab, or similar with the current DNS information. Write down your DNS servers (x.x.x.x & x.x.x.x).

You may wish to back up your dhclient.conf file at this point. In the Terminal, type:
cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak

2. Enter these DNS servers directly in your dhclient.conf file:

sudo gedit /etc/dhcp3/dhclient.conf

You should see your dhclient.conf file displayed (with text in it). Add two lines to the end:

supersede domain-name-servers x.x.x.x,x.x.x.x;
prepend domain-name-servers x.x.x.x,x.x.x.x;

The x's represent your DNS server IP addresses that you found in Step 1.

Save your dhclient.conf file, close gedit and return to the Terminal.

Now restart your DNS lookup with (assuming eth0 is your connection to the router):

sudo ifdown eth0 && sudo ifup eth0

You should immediately experience an improvement in your Internet speed.

After I updated Dapper, pages loaded very slowly until I made these changes.
I researched the solution on [https://forum.bytemark.co.uk/viewtopic.php?pid=1790](https://forum.bytemark.co.uk/viewtopic.php?pid=1790) as well as other Ubuntu forum entries.

---

### Post by Felix21685 on 2007-08-23
> **G Morgan said:**
> If your system is struggling to resolve addresses try entering this at the command prompt.

#sudo su
#echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

Then try and see if the problem persists.

//edit you have to sudo su btw. You can't perform that command as sudo.//


this solution solved my problem,

before this i tried

```
gksudo gedit /etc/modprobe.d/blacklist
```

then adding

```
blacklist ipv6
```

link to site [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

so i dont know if it was the combination of the two or just this latest thing, but hopefully this info will help someone else.


EDIT:

I rebooted the machine and it was slow again until I did the echo 0 part again.
any way to make it permanent?

---

