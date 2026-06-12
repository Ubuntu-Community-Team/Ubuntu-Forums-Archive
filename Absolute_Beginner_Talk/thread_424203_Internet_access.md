---
title: "Internet access"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by meinzy on 2007-04-26
Been trying for two days now to get the internet on my desktop.  Installed Feisty after seeing same problem with 6.10.  Here goes:

I can access Google through my LAN connection to a common router connected to my brother's PC.  But I can not access any other sights (except any of the Google sites).  The network connection is obviously good since I can view files and such on my bothers PC.  I can ping Google just fine.  I can not ping other sites (tried Comcast.net).  So...that would tend to indicate that the problem involved Comcast (our provider).

BUT...I installed Feisty on my laptop and although I can't get the wireless working (seperate issue) I can fully access the Internet when I plug in the cable that was originally plugged in my desktop.  Ain't that a hoot!

That eliminates Comcast as the problem.  Could it be that I need to configure my network settings on the Desktop differently?  They are, as far as I know how to look, identical to the laptop.

Hope you can help,
Zy

---

### Post by Cypher on 2007-04-26
It's strange that you can access google but cannot access other sites.

Do
```

ifconfig -a

```
and see if the IP address is in line with what your brother's PC and your laptop is getting.

Then do
```

cat /etc/resolv.conf

```
and confirm that the DNS info is correct in there.

Ping the namservers and confirm you can talk to them. Then
```

nslookup

```
start typing various address, google.com, yahoo.com, ubuntu.com and so on and see what you get back..

---

### Post by meinzy on 2007-04-26
I'm a complete and total newbie to Linux.  Where do I type the command lines?  Haven't done anything like that since the DOS days.

---

### Post by Cypher on 2007-04-26
Applications->Accessories->Terminal and that's where you'd type these commands..

If you know DOS, you'll love Linux command line..:)

---

### Post by meinzy on 2007-04-26
under eth0 I see inet addr, Bcast , Mask, inet6 addr.  Which do I compare?

---

### Post by Cypher on 2007-04-26
Unless you've already implemented IPV6, I'd start with "inet addr". That should be a DHCP address that the router gave your PC. Now you can compare that to the other machines and if that's OK, try the other things I suggested..

---

### Post by meinzy on 2007-04-26
On my Bro's PC (Windows) his network settings are:
IP: 192.168.1.103
Default Gateway: 192.168.1.1
Mask:identical

On My Ubuntu PC:
inet address: 192.168.1.100
Bcast: 192.168.1.255

---

### Post by meinzy on 2007-04-26
I can ping both nameservers.

---

### Post by meinzy on 2007-04-26
When I do the nslookup and type in various addresses I get their Name and address back.  If I open Firefox and type the addresses in direct I just get a Server Timeout.

What now?

---

### Post by Cypher on 2007-04-26
OK..so within nslookup, you can type in yahoo.com and have it resolve to 216.109.112.135 and 66.94.234.13?? Can you also just do a "ping yahoo.com" in the Terminal and have it work? If all that is working, then we might need to focus more on why Firefox is mis-behaving rather than your system as a whole..

---

### Post by agurk on 2007-04-26
It sounds to me as if you have a proxy set in Firefox. Check that "Edit -> Preferences -> Advanced -> Network -> Connection -> Settings..." is set to "Direct connection to the Internet"

---

### Post by meinzy on 2007-04-26
Yes, yahoo.com resolves correctly.  And Firefox was set for direct connect.  When I type those addresses in directly to Firefox it still just times out.  This is a doozy, isn't it?

---

### Post by Cypher on 2007-04-26
OK..well now you've definitely got me! Even if firefox was having issues with resolution, punching in the IP address should definitely make it work. 

Can you check under Applications->Internet and see if you have "Lynx" and if you do, can you try using that and see if you can access the web. Don't be scared if it shows up as a text browser, because that's what it is..

---

### Post by agurk on 2007-04-26
Heh, funky indeed. Does Synaptic work, i.e. when you go to System -> Administration -> Synaptic Package Manager and press Reload, does it connect to the online repositories correctly? If it does, you may want to reinstall Firefox, or try a different browser.

---

### Post by meinzy on 2007-04-26
If i scroll through Google after doing a search using random terms and keep clicking on links, every once in a while (maybe 1 in 30) a page partially loads.  I can access any of  Googles' sites.

---

### Post by meinzy on 2007-04-26
OK, Synaptic tries to download.  Files with size '191 B' show as done, all else Failed.   They initially show as 'hit', if that makes any difference.

---

### Post by meinzy on 2007-04-26
Oh, and I don't have Lynx.

---

### Post by meinzy on 2007-04-26
Know of any other resources I can tap into?  Other forums, experts or support gurus?

---

### Post by agurk on 2007-04-26
Since you seem to be able to both ping and download very small files, it suggests to me that the problem might be related to your system-wide MTU size setting ([http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)), and that it might be worth checking out threads like these:

[http://www.linuxquestions.org/questions/showthread.php?t=469531](http://www.linuxquestions.org/questions/showthread.php?t=469531)
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630)

I'd try setting it to 1400 to see if that helps. I've had similar problems in the past when running Ubuntu under VMware.

Have to catch some shuteye, good luck!

---

### Post by John the train on 2007-04-26
As it looks as if it could be a Firefox problem you could try their forum, try googling ' Mozilla ' and that should give you some leads to it.

---

### Post by meinzy on 2007-04-26
I didn't know the command to ping from within the terminal.  So I went to network tools and pinged yahoo with success.  But Firefox just times out with the same IP.  It seems that all short comms are ok, since Synaptic can download little files.  And very simple web pages can partially load.  It's almost as if anything other than Google can only communicate short bursts.  But why in the hell can all of Google's sites work?  That would seem to exclude hardware or driver.  Google would seem to exclude Firefox.  And Firefox works fine on my laptop which loaded Ubuntu from the same CD.

---

### Post by meinzy on 2007-04-26
And this problem was present when I had version 6.1 also.  I upgraded to Feisty to see if that would fix it.

---

### Post by meinzy on 2007-04-26
Thanks for all the help.  I'm going to take this to the networking forum.

---

### Post by VraiChevalier on 2007-04-26
I am having a similar problem since installing Feisty. Dapper worked great! Edgy upgrade would not connect to internet. Feisty clean install from desktop CD works fine except for intermittent internet connection. Wired connection. Cable modem. Works with my other PC.

I have been searching these forums and Launch Pad and this seems to be a common problem.

---

### Post by meinzy on 2007-04-26
Well, if I find a solution I'd be glad to let you know.  I tried posting in the Networking forum but apparently no one wants to touch this one.  It is a bizarre problem!  Very frustrating since I can't get my Belkin wireless USB working either.  I really need the LAN to work, however.

This is a rough way to get one's feet wet with Linux.

---

### Post by wirelessmonkey on 2007-04-27
Sounds almost like a firewall issue....  if it's on, turn it off for a bit.

---

### Post by meinzy on 2007-04-27
> **VraiChevalier said:**
> I am having a similar problem since installing Feisty. Dapper worked great! Edgy upgrade would not connect to internet. Feisty clean install from desktop CD works fine except for intermittent internet connection. Wired connection. Cable modem. Works with my other PC.

I have been searching these forums and Launch Pad and this seems to be a common problem.

Fixed! :)  Check out this post in the Networking forum:

[http://ubuntuforums.org/showthread.php?p=2545109#post2545109](http://ubuntuforums.org/showthread.php?p=2545109#post2545109)

Good luck

---

### Post by rpaco on 2007-04-27
I had a similar problem with Firefox not connecting  in 6.10 but I could ping any address from the network tools applet.
Chilli555 solved it for me as follows:
Open a terminal Applications>accessories>terminal
then type 
sudo gedit  /etc/modprobe.d/blacklist  (you will be asked for your password here)

then gedit will open and show you the blacklist file. Scroll to the bottom of the file and add a new line that says
blacklist ipv6

then save the file, close things and re-boot.

It worked for me so it may for you; as an aside there is a line in Firefox "about:config" that also disables ipv6 but it does not work the same way or have the same effect as the blacklist method on my system. I still have other problems in that Firefox and skype are the only things which will connect, I cannot get any email or system updates. Chilli555 if you read this please help with my other problems posted elsewhere.

---

### Post by agurk on 2007-04-27
Glad to hear you were able to nail it down meinzy, nice work of lloyd_b over in the other thread.

---

### Post by VraiChevalier on 2007-04-29
Well, I tried everything I could find to fix the problem with Feisty dropping internet connection but finally gave up and went back to Dapper.

That's the weird thing, no problem whatsoever with Dapper connecting to the internet. I just plug in my cable modem USB cable and away we go!

Feisty never did see my USB cable modem internet connection. Only the ethernet cable.

One interesting and perhaps useful bit of info; With this install of Dapper the ethernet connection dropped out after about 5 minutes. Switched to USB connector and have been going strong for several days now. Never lost the connection once. I'm stumped!

I wonder if the root of the problem has something to do with how Feisty talks to USB interfaces or busses.

Love the Dapper!
Love these forums!

---

