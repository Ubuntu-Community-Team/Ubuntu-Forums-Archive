---
title: "Proxy troubles..."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Dog'sDay on 2007-01-21
Hi All!

I just Installed Ubuntu 6.10 for the first time yesterday and am a complete Linux newbie. I'm having trouble with my proxy server. After struggling for hours last night to get my internet to work, I finally got Firefox to access the internet. The problem comes in when I try to run 'Synaptic Package Manager' or 'Add/Remove Applications'. I have tried setting the proxy settings exactly the same in 'Firefox', 'System/Preferences/Network Proxy' and under Synaptic Package Manager's Network Preferences, but to no avail I get a "http://za.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg: Could not resolve 'ooc-proxy.shbhpb.net'" error message from both Synaptic and Add/Remove Applications. I have not tried apt-get yet, but that's because I'm not exactly sure how to use it.

I'm not sure what type of proxy server is running, just that it does require authentication, which firefox promptly asks me for when I start accessing the internet. Can anybody give me a suggestion on how to fix my problem?

Thanks!

P.S I have tried putting 'username:password@' in front of the proxy's address in Synaptic, but that didn't work. I have also tried just typing 'export something something' (which i found on another thread) on the terminal and that  didn't help either...

---

### Post by JamieC on 2007-01-21
**apt-get**
You'll need to configure the proxy for apt-get...

Open a new terminal window and type the following command (where <editor> is your preferred editor, such as vim or nano):
```

sudo <editor> /etc/apt/apt.conf

```

Add the following lines (replacing <ip> and <port> respectively):
> 
ACQUIRE {
http::proxy "http://<ip>:<port>/"
}


Save the file, then run the following:
```

apt-get update

```

**wget**
You may also need to configure wget...

Again, open the file with your preferred editor:
```

sudo <editor> /etc/wgetrc

```

Find the following line and change appropriately (remembering to remove the hash):
> 
#http_proxy = [http://proxy.yoyodyne.com:18023/](http://proxy.yoyodyne.com:18023/)


Find the following line:
> 
#use_proxy = on


Change to:
> 
use_proxy = on


Then save it.

---

### Post by CroEragon on 2007-01-21
Just to let you know, Synaptic is actually apt-get's graphical user interface. Synaptic uses apt-get to handles installing and everything. So when you configure apt-get, Synaptic will work. And i think there is one central file that needs to be modified so every program on computer use proxy(is that what you want?) but i have no idea what one.

---

### Post by shoaibi on 2007-01-21
have you tried:
export_proxy="http://your_name:your_password@your_proxy:Your_port/'
in terminal and then doing some apt-get?
if that's works i really have no clue where is the problem..

---

### Post by Dog'sDay on 2007-01-21
Wow! You guys are quick! Thanks for the advice.

I tried JamieC's advise and this is the message i get: 
"apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

Synaptic still gives the same error...

---

### Post by JamieC on 2007-01-21
Sorry, use the following command instead:
```

sudo apt-get update

```

(You need to be root)

---

### Post by Dog'sDay on 2007-01-21
That worked a bit, but now apt-get is also giving me the 'Could not resolve' Error...

---

### Post by JamieC on 2007-01-21
Even with the proxy?

Can you access the URL in a browser?

---

### Post by Dog'sDay on 2007-01-21
Which URL? Sorry, I'm not that great with this stuff. I can access the internet through firefox, and I can see the other computers on the network, but that's about it...

---

### Post by JamieC on 2007-01-21
You definitely saved the file right? Try using that proxy for Firefox too and typing the URL that could not be resolved. If it does not connect you may want to try a different proxy.

---

### Post by Dog'sDay on 2007-01-21
I think I found the problem...
A program called 'websense' on the proxy server is blocking the address. I think that's the problem , because I typed one of the addresses that apt-get wants to access into my web browser and Websense came up, blocking it.

Do you know of a way I can get around this?

---

### Post by JamieC on 2007-01-21
Configure the proxy for Firefox too and then try accessing the URL, does Websense still filter it?

---

### Post by Dog'sDay on 2007-01-21
I am using the same proxy for both apt-get and firefox, with the same ports as well. If I put 'http://za.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz' into firefox's address bar, I get: "Reason: 
	

The Websense category "Uncategorized" is filtered. Access to this file is restricted. File type: Compressed Files.
  	

URL: 
	

[http://za.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Pack](http://za.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Pack) ages.gz"

---

### Post by JamieC on 2007-01-21
Looks like you cannot bypass Websense. Try again with another proxy, if that is to no avail I am unsure how to proceed.

---

### Post by Dog'sDay on 2007-01-21
I don't think there is another proxy avaiable, but thank you VERY much for all your trouble. It's really appreciated. Do you of another way/ another site where I can get the updates? Maybe if i try that, websense will let me through...

---

### Post by JamieC on 2007-01-21
You're very welcome, seeing as Websense is filtering compressed files, and the headers are all in a .gz format, I don't think it's possible to access them...

---

### Post by Dog'sDay on 2007-01-21
Just my luck, Thanks alot! I guess I'll try again from another location, when I'm not stuck behind a proxy or a web filter...

---

### Post by rmartz on 2007-01-25
It worked for me, but my proxy doesn't require user:password. 

I am curious why these are not changed when one would set the Network Proxy settings at System->Preferences->Network Proxy.

I can't even get my browser to utilize the settings in this. What is it for if it doesn't work for the browser or apt-get?

---

