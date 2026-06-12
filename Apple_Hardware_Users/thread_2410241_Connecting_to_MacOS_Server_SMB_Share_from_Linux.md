---
title: "Connecting to MacOS Server SMB Share from Linux"
date: 2019-01-13
forum: Apple Hardware Users
---

### Post by Asif_Ahmad on 2019-01-13
[FONT=sans-serif]Hey Guys,

[/FONT]
[FONT=sans-serif]I have a Mac Mini Server that is running macOS Mojave that I am trying to connect to from my linux laptops. I know this isn't a specific linux issue, but hoping someone out there may be running a MacOS server and resolved this already:
[/FONT]
[FONT=sans-serif]_The Issue:_[/FONT]
[FONT=sans-serif]When I am trying to access the Mac's SMB share from my Linux Laptop, I am unable to mount and browse the directories on my mac mini. I CAN SSH into the mac mini with no issues, but I can't mount (or browse) to find my mac mini on the network tab. I was able to do this previously with my old Mac server from my Linux machines, so I am unsure if something changed in MacOS Mojave that is preventing this from working.

[/FONT]
[FONT=sans-serif]If anyone could offer any assistance, it would be greatly appreciated.[/FONT]
[FONT=sans-serif]
Thanks in advance![/FONT]

---

### Post by Morbius1 on 2019-01-13
2 questions:

[1] macOS _Server_ operating system on a Mac Mini or _normal_ macOS on a mac mini used as a server?

[2] What version of Ubuntu are you using?

I don't notice any difference accessing a Mojave share on a MacBook from Xubuntu 18.04 from earlier versions of either OS.

---

### Post by Asif_Ahmad on 2019-01-13
Hey,

Thanks for the quick reply.  Let me answer your questions directly below:

[COLOR=#000000][1] macOS [/COLOR]_Server_[COLOR=#000000] operating system on a Mac Mini or [/COLOR]_normal_[COLOR=#000000] macOS on a mac mini used as a server?
[/COLOR]**I am using _normal_ macOS Mojave on my Mac Mini.  I am just using it as a server. **


[COLOR=#000000][2] What version of Ubuntu are you using?
[/COLOR]**I am using 18.04 version of Ubuntu currently.**

I had previously had an older version of MacOS on the Mac Mini (High Sierra), so I recently wiped everything and did a clean install on the drive of macOS Mojave.  I am now hitting this issue.  I think it may be because I am starting 'fresh' on macOS Mojave.  I turned on all the file sharing settings in macOS that I did previously, but something is preventing my Linux laptop from seeing the Mac Mini (and mount it) correctly.

Also, to note, my wife has a MacBook Pro, and she is able to see and mount the Mac Mini with no issues (her computer is also running MacOS Mojave).

If you need any additional information please let me know.  Any assistance you could provide would be greatly appreciated.  TIA.

---

### Post by Morbius1 on 2019-01-14
> [FONT=sans-serif]but I can't mount (or browse) to find my mac mini on the network tab[/FONT]

Discovery ( browsing for ) and accessing a specific share are two different things. You should be able to access the MacMini by ip address worst case.

The discovery part should be automatic from Ubuntu  since it shares macOS' native networking protocol so let's see if avahi ( Bonjour in macOS ) is working on the ubuntu box:

You should see the MacMini by it's host name if avahi is working properly by running this command in a terminal in Ubuntu.
```
avahi-browse -at | grep Network
```
If you don't see it there are only a few things that can break avahi:

** The service is not running. Check to see if it's running:
```
sudo service avahi-daemon status
```
If it's not running start it:
```
sudo service avahi-daemon start
```
Then check the status again.

** Browsing and name resolution depends upon the two machines being in the same subnet.

Both machines have to be connected to the same router. Switches in the mix are fine but another router will cause a problem.

** I suppose a firewall on the Linux box could be a problem but you would have to go out of your way to block avahi since it's enabled by default like TCP/IP.

** There is one other obscure issue and it has to do with your ISP. 

Some ISP's incorrectly use the .local domain within their own network which interferes with how avahi works. Run the following command from the Ubuntu box:
```
host -t SOA local
```
It should come back with something like this: **Host local not found: 2(SERVFAIL)** OR **Host local not found: 3(NXDOMAIN)**
If it comes back with an actual address like this that's a problem:
> local has SOA record localhost. xxxx.yyyy.zzz.
One way out of this is to change the DNS servers you use from the one supplied by your ISP to ... um ... google ( 8.8.8.8 ) for example. You can test this temporarily by forcing the host command to use google instead of your ISP:
```
host -t SOA local 8.8.8.8
```
You should get the **Host local not found** response.

[COLOR=#000080]*Note: The MacBook is unaffected by the ISP problem because Apple has more experience with this than Linux so it knows how to handle the situation automatically.*[/COLOR]

---

### Post by Asif_Ahmad on 2019-01-14
Hello Morbius1,

Thank you for the details and thorough reply!  I super appreciate your time and help with this matter!  =)

_**Browse / Discovery:**_
So you are correct, I am trying to discover (browse) to my Mac Mini from my Ubuntu laptop.  It does appear to 'find' it correctly, screenshots below if I look into the "other locations" tab inside the Files Application:
[https://imgur.com/a/ftGHRh8](https://imgur.com/a/ftGHRh8)

However, when I click on "Asifs-Mac-Mini (File Sharing)", I get the following error message:
[https://imgur.com/a/QWzERum](https://imgur.com/a/QWzERum)


[U][B]Access SMB Share Directly with IP Address:
[/B][/U]When I try to access the Mac Mini via the SMB share and IP address, I get a prompt (as expected) but I don't know what to fill in for the "domain" section of the prompt:
[https://imgur.com/a/HnkuPNV](https://imgur.com/a/HnkuPNV)

This domain is preventing me from logging into the Mac Mini correctly.  Do you know what should be used here?

[B][U]ISP / Router:
[/U][/B]Both machines are on my home network and are both utilizing the same router currently.  

[U][B]Output:
[/B][/U]This section contains output for the avhi command and the host command per your request:

**[aahmad@aahmad-pc ~]$ avahi-browse -at | grep Network**
+ wlp58s0 IPv6 Asifs-Mac-Mini                                Microsoft Windows Network local
+ wlp58s0 IPv4 Asifs-Mac-Mini                                Microsoft Windows Network local
[aahmad@aahmad-pc ~]$ 


**[aahmad@aahmad-pc ~]$ host -t SOA local**
Host local not found: 2(SERVFAIL)
I believe both of these commands gave the expected output and show that things should be working correctly.


Please let me know if I can provide any additional information to assist in the troubleshooting process.  Thanks again for all of your time and help, it is greatly appreciated!

---

### Post by slickymaster on 2019-01-14
*Thread moved to **Apple Hardware Users**.*

---

### Post by Morbius1 on 2019-01-14
On the MacMini: Did you enable the remote user and allow him access?

System Preferences > Sharing > under "File Sharing: On" > Options there is a list of users that will be allowed access to the share.

**Note**: The workgroup name doesn't matter. It's a netbios ( Windows ) thing. We aren't using netbios.

---

### Post by Asif_Ahmad on 2019-01-14
Yes, I gave my user access to both drives under sharing on the MacMini:
[https://imgur.com/a/ONFKTZk](https://imgur.com/a/ONFKTZk)

In addition, everyone should have read access as the screenshot above shows.  Any idea what the "domain" should be?

---

### Post by Morbius1 on 2019-01-14
Your attached image doesn't go far enough. Click on the Options button. Did you select all the users that you want to have access to your shares?

It doesn't matter what the domain is it will be ignored. We aren't using Windows.

---

### Post by gsahli on 2019-01-14
Not sure this is still required... (I'm on High Sierra, not Mojave)
Do get Info on the drive, and check the box "shared Folder."

---

