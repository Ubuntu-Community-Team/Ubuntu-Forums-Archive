---
title: "Unable to upgrade packages via Update Manager"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by bteck on 2007-02-04
I am using Ubuntu 6.10.  After enabling both universe & multiverse in /etc/apt/sources.list, I still could not :confused:  via [Update Manager].  Below is my settings in sources.list file:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main

After a long waite, I clicked cancel and a message box showing some error massages was received.  The first two error messages were:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.3_i386.deb)
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.2-4.1ubuntu5.6.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.2-4.1ubuntu5.6.10_i386.deb)
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

What's the problem?  Thanks for any help.

---

### Post by taurus on 2007-02-04
What happens if you run these from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by bteck on 2007-02-04
I started a Terminal and ran: sudo aptitude update
The results are shown below.  It basically stayed at 0% while trying to connect to  the site. 

bteck@bteck-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

When I ran: sudo aptitude upgrade, the results are the same - waiting at 0% connection.

What has gone wrong?

---

### Post by lamego on 2007-02-04
> Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Or you have setup a proxy on http(1.0.0.0) or your dns is not properly configured, apt should not be trying to contact 1.0.0.0, make sure you don't have that IP setup for the proxy.

---

### Post by bteck on 2007-02-05
> **lamego said:**
> Or you have setup a proxy on http(1.0.0.0) or your dns is not properly configured, apt should not be trying to contact 1.0.0.0, make sure you don't have that IP setup for the proxy.

Thanks for response.  

I ran System->Preferences->Network Proxy and in the [Network Proxy Preferences] window, under the [Proxy Configuration] tab, the selection was [Direct Internet connection].  Under the [Advanced Configuration] tab, the [Ignore Host List] contained: localhost, 127.0.0.0/8, and *.local.  

I then ran System->Administration->Networking to check my DNS.  In the [Network Settings] window, under the [DNS] tab, my DNS Servers was set to 192.168.1.1 which is my wireless router home page.  No other DNS setting was present.

Are the above settings correct?  What other settings should I check?

---

### Post by bteck on 2007-02-05
> **lamego said:**
> Or you have setup a proxy on http(1.0.0.0) or your dns is not properly configured, apt should not be trying to contact 1.0.0.0, make sure you don't have that IP setup for the proxy.

I have finally resolved the issue of connection to ubuntu sites for updating of packages.

I  ran System->Administration->Networking.  In the [Network Settings] window, under the [DNS] tab->[Search Domains] edit box, I clicked the [Add] button and added the domain name: [www.google.com](www.google.com).  I then clicked the [Close] button.

When I started a Terminal session and typed: sudo aptitude update, the system was able to connect to various ubuntu update sites and downloaded the required files.

What I have learned for this and from observing the many similar problems faced by newbees is that there is a serious lack of examples in the various Ubuntu help documentation (perhaps the same can also be said about other Linux doc?).  Below is an example I picked from the Networking help to make my point:

"3.6.&#8195;To add a new search domain
In the Search Domains section, press the Add button and fill in the new list row with the new search domain."

From this help, the user is not certain whether a "new search domain" is absolutely necessary, or does the system already has some well known domains as defaults which were not shown?  If it is absolutely necessary, the help documentation MUST state so, and give a few examples of well known domain names (such as [www.google.com](www.google.com) which I used) to help the newbee.

I understand that it takes lots of efforts to produce a good documentation.   It is just a thought that could we _make it a point_ to add at least ONE example for each item requiring a help?  Otherwise, the efforts put into help is wasted anyway.

Anyway, thanks for all who has responded.  Your certainly have helped me.
:guitar:

---

### Post by bteck on 2007-02-05
Now, my problem with unable to use Evolution for my email is also solved!  All because of the absence of a "search domain".

 :guitar:

---

### Post by ter_minus on 2007-02-16
Just wanted to say a big thank you to bteck for his findings! =D> It helped me solve my 1.0.0.0 problem when i wanted to download updates or using telnet. Great find!  Bteck, you da man! :wink:

---

