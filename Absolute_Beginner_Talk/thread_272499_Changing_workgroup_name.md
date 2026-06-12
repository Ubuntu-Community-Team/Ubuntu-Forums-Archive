---
title: "Changing workgroup name?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by WeeManDan on 2006-10-06
Hi

I'm trying to work out how to change the workgroup name on Ubuntu so it's in the same place for windows and mac. 

How? 

Thanks for the help

WeeManDan

---

### Post by Ben Sprinkle on 2006-10-06
Linux doesn't have a workgroup it can read the shares on windows no matter what. Samba shares is good for the job.

---

### Post by WeeManDan on 2006-10-06
What about a Mac? Ubuntu cant access the shares on it?

Cheers

WMD

---

### Post by Ben Sprinkle on 2006-10-06
Don't know about mac, only windows. Sorry.

---

### Post by WeeManDan on 2006-10-06
Ok, also how do I know if I have Samba installed?

Dan

---

### Post by WeeManDan on 2006-10-06
I've been looking on the documentation and under Network Administration Tool it has:

3.6.&#8195;To change the way your system identifies itself in Windows networks

In the General section, change the description or workgroup of your system in Windows networks. You can also specify the WINS server if you need one.

Where is this program though?

Cheers 

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> I've been looking on the documentation and under Network Administration Tool it has:

3.6.&#8195;To change the way your system identifies itself in Windows networks

In the General section, change the description or workgroup of your system in Windows networks. You can also specify the WINS server if you need one.

Where is this program though?

Cheers 

Dan

Try looking here: System--->Administration--->Networking

---

### Post by WeeManDan on 2006-10-06
> **IoCaster said:**
> Try looking here: System--->Administration--->Networking

And then the General Tab, but the only options are domain or host-name?

Dan

---

### Post by Ben Sprinkle on 2006-10-06
Ubuntu already has Samba installed.

---

### Post by IoCaster on 2006-10-06
You may want to read up some more [**here**.]("http://ubuntuguide.org/wiki/Dapper")

I've got a complicated home network setup through a Chilibox server. I've got 2-WinXP, 1-IntelMac and 1-Ubuntu comps networked and it was a bit of a hassle putting it all together and making it work. I used the guide I linked above. Good Luck.

Regards - Joe

---

### Post by WeeManDan on 2006-10-06
Ok, so any idea how I access the Mac?

Dan

---

### Post by Ben Sprinkle on 2006-10-06
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=mac](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=mac)
Why don't you start there. I cannot find an article about your answer but perhaps you will.

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Ok, so any idea how I access the Mac?

Dan

It's specific to my network so I don't know how much use you can make of it, but I'll describe it to you.

I use a Chilibox server as router, firewall, mail server, dhcp server, nas, dns server, gateway, wap and so on.

I use Samba to share files and folders across the network. I gave all my comps static ips and created a domain name for each of them. For example: mymac.mydomain.com and use dns resolution to target each pc/mac. I connect to the mac like this ---> smb://myname@mymac.mydomain.com using nautilus. My hp all-in-one printer has networking capabilities as well (ethernet+wireless), so I gave it a static ip and I share it across the network through a wireless connection from my server. I set it up this way because I wanted a solid and seamless home network built for heavy traffic/use. It all works very well, but it was a bunch of trial and error finding the right solution. Good luck.

Regards - Joe

---

### Post by WeeManDan on 2006-10-06
Grr this is frustrating, why couldnt it be simple?

Do I need some kind of Samba GUI?

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Grr this is frustrating, why couldnt it be simple?

Do I need some kind of Samba GUI?

Dan

If all you want to do is access files on your mac then just enable ftp or ssh on it and you're good to go. If you want full access to your mac from a pc running Ubuntu through a file manager/browser then you're going to have to do some work.

Which is it?

If the former then your task is much simpler and you can find the answers quickly in any of the guides that have been linked. 

If you want full gui enabled networking linux<--->mac then you'll have to do some reading and Samba would probably be the easiest solution. You could always opt for NFS, but I would think that's not a very newbie friendly task to set for yourself. 

It's best if you give us a specific topology diagram of your comps and what you're trying to accomplish. How many comps, what OS they're running and what type of networking protocols you need.

Use plain language to describe it.

---

### Post by WeeManDan on 2006-10-06
The first is what I want to do, simply access the Mac from Ubuntu. At the moment my Mac is configured such that Windows based machines can see it. I can navigate to my Mac from Ubuntu and see it but there is nothing there?!?

So as a setup up, the Mac is basically a file server and the Linux box the client

Thanks for the help,

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> The first is what I want to do, simply access the Mac from Ubuntu. At the moment my Mac is configured such that Windows based machines can see it. I can navigate to my Mac from Ubuntu and see it but there is nothing there?!?

So as a setup up, the Mac is basically a file server and the Linux box the client

Thanks for the help,

Dan

Turn on remote login and/or ftp access on the mac in system preferences--->sharing. Look at the bottom of the panel and it should tell you how to remotely connect to your mac with either of those protocols. For example: [ftp://some-address](ftp://some-address) or ssh (mac)username@someaddress.

For ftp you can use nautilus or the browser/ftp client of your choice. For ssh you use the terminal. 

Try that and see if that will suit your needs for now. Good luck.

Regards - Joe

---

### Post by WeeManDan on 2006-10-06
Yay! Thanks I've got an ftp share set up now on my Ubuntu desktop 

Will that stay there indefinately? Presumably every time the IP changes I will have to change the IP of the share.

Thanks

Dan

---

### Post by WeeManDan on 2006-10-06
Also, how do I change the workgroup name so that on the Mac it is in the same workgroup as other comps?

Cheers

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Yay! Thanks I've got an ftp share set up now on my Ubuntu desktop 

Will that stay there indefinately? Presumably every time the IP changes I will have to change the IP of the share.

Thanks

Dan

You haven't told us how you aquire your ip address yet. If you'd like it to remain the same then you'll have to use a static ip on the mac. In the system preferences ---> network panel enter the ip address you currently have assigned into the **IP Address** box. Make sure that in the **Configure IPv4:** drop down menu you have selected....```
Using DHCP with manual address
```

That will keep the ip address static and you should be able to keep connecting to it indefinitely. If it were to change dynamically you can always check that same panel to get the current address and use that to connect from your ubuntu box instead.

---

### Post by WeeManDan on 2006-10-06
Sorry yeah they're both attatched to a router and the IP is assigned automatically so yeah I would have to do it so the IP was static. 

But will it be automatically always be mounted if the IP stays the same?

Also any idea on the workgroup thing?

Thanks

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Also, how do I change the workgroup name so that on the Mac it is in the same workgroup as other comps?

Cheers

Dan

I don't remember that being a neccessary component on the mac end of things or ubuntu for that matter. As long as your win comps are set to the same peer-to-peer workgroup name it should be good. You can search for windows shares by the workgroup name on the mac/ubuntu comps as a means to an end though. 

For a more robust and long term networking environment you might be well advised to get well aquainted with Samba and it's capabilties. It can often be difficult to configure, but time spent now can payoff big dividends down the line. Good luck.

Best regards - Joe

---

### Post by WeeManDan on 2006-10-06
So to access the Ubuntu machine from the Mac I need to sort out Samba?

Cheers

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Sorry yeah they're both attatched to a router and the IP is assigned automatically so yeah I would have to do it so the IP was static. 

But will it be automatically always be mounted if the IP stays the same?

Also any idea on the workgroup thing?

Thanks

Dan

The router will not be concerned if if doesn't have to assign an ip address to your mac or any other machine. It's a souless pile of silicon and plastic. It couldn't care less.

:mrgreen:

---

### Post by WeeManDan on 2006-10-06
Lol ;)

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> So to access the Ubuntu machine from the Mac I need to sort out Samba?

Cheers

Dan

It's probably the easiest solution, yes. You'll have to assign shares in ubuntu and Samba would be the easiest to configure. Read the various guides until you get comfortable editing the right config files.

Try this ---> open nautilus ---> /root or file system ---> /media ---> right click any of your selections like hda1. Choose (Share Folder) and you'll get a dialog box. How do you decide what choices to make there? SMB or NFS? Path? Share with? Allowed Hosts?

You can't really make an informed decision unless you have a basic foundation of understanding what those terms/selections refer to. Take your time, don't rush things if you have the choice. Learn what you need to know and you'll eventually be able to configure everything so well that you'll fidget and fuss because you need some new challenges to confront.:p 

If that happens you'll know you've been transformed into a technogeek.:shock:  

Oh, the humanity.....!!

---

### Post by WeeManDan on 2006-10-06
Well I'm at Uni to study network computing and thought it a good head start to start using a linux distro

What is nautilius? Where do I find it?

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> Well I'm at Uni to study network computing and thought it a good head start to start using a linux distro

What is nautilius? Where do I find it?

Dan

Hmm...nautilus is a file manager/browser app. Kind of like windows explorer. If you're using Ubuntu-Gnome it's pretty much the default, I believe.

---

### Post by WeeManDan on 2006-10-06
I think I'm getting there slowly but for some reason when I try to load the SMB share in OS X it says the password is wrong, any idea? I've triple checked it :-? 

Cheers

Dan

---

### Post by IoCaster on 2006-10-06
> **WeeManDan said:**
> I think I'm getting there slowly but for some reason when I try to load the SMB share in OS X it says the password is wrong, any idea? I've triple checked it :-? 

Cheers

Dan

You might need to do some research on that. If I remember correctly it has to do with OS X not wanting to use an unencrypted password. You'll have to make the linux-mac handshaking sync with either/or. It can be done.

There's certainly an element of ***"Thinking Outside the Box"*** to it. 8) 

Regards - Joe

---

### Post by WeeManDan on 2006-10-07
So does Ubuntu basically use unencrypted passwords then?

Cheers

Dan

---

### Post by IoCaster on 2006-10-08
> **WeeManDan said:**
> So does Ubuntu basically use unencrypted passwords then?

Cheers

Dan


I'm going by memory here so you'll want to read one of the Samba guides to confirm. I think that by default, Samba uses plain text for passwords. The Mac by default requires encryption for passwords. You'd have to change one or the other. The easiest would probably be to configure Samba to use encrypted passwords. You **can** force the Mac to use unencrypted passwords, but I'd think that wouldn't be a good idea. Totally up to you which method to use. There's a subforum on networking [here]("http://www.ubuntuforums.org/forumdisplay.php?f=136"). It's a good place to post specific questions about all Ubuntu related networking issues.

Regards - Joe

---

### Post by WeeManDan on 2006-10-08
Ok cool cheers, from what I've read that seems to be the prob

Dan

---

