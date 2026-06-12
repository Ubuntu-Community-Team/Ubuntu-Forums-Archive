---
title: "I cannot connect to the web"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-03-07
I am new to Linux and I find this all very curious. Ubuntu will download from repositories, but it will not connect to the internet.  The online documentation at help.ubuntu.com comes up just fine, but no other website in the world will display. Why is that?

---

### Post by vayde on 2007-03-08
Need more information.

Are you sure that you are connecting to your router?

If connecting to router, can you ping an outside IP address?

Is it just having problems resolving names?

If so, there's a good chance you are just having problems with DNS.

Anyway, we'll need more info to diagnose the problem.

---

### Post by Mr. C. on 2007-03-08
Most likely you do not have DNS servers configured.

Go to System->Administration->Networking and click on the DNS tab.  Place the DNS IP addresses there that your ISP gave to you when you receive the service, and close the dialog.

MrC

---

### Post by WhiteSphinx on 2007-03-08
I don't have a router.  I am connecting to my DSL Modem via a hub.  My other three computers connect up just fine (with Windows). I have no idea what you mean by "ping"!  I am not a "techie"!  The internet worked just fine the first time that I used Ubuntu live.  Since installing it I can't get it to work at all - even running it live.

---

### Post by vayde on 2007-03-08
Ok, no problem.  We'll walk you through the 'techie' aspects.

It sounds like you are having problems with DNS resolution.  

Try Mr C's advice above, and post again if you are still having trouble.

---

### Post by WhiteSphinx on 2007-03-08
I have no idea how to find the IP. I do not have a static IP. It is a dynamic IP.  On all of my windows computers I just plug in the network cable and I have instant access to the internet. With PCLinuxOS, I had no problems with the internet (other problems - but not with the internet).

---

### Post by vayde on 2007-03-08
It's not your IP that is the problem, but the DNS.

DNS stands for Domain Name Server.  One of the main things that DNS does for you is it translates the human readable url of [http://ubuntuforums.org](http://ubuntuforums.org) into an IP number that the computer can use, in this case 82.211.81.186 .

Most network appliances these days use not only dynamic IP but dynamic DNS as well.  I don't really understand why, but in my experience, the dynamic DNS set up by most routers, dsl, cable modems, etc. does not play nice with linux/ ubuntu.

If this is your problem, then giving your machine a known good DNS server IP will fix it.

You should be able to get a DNS address from your ISP, but we'll save that for later.

Right now try this:
Go to System->Administration->Networking->DNS and add the following value:
206.191.207.250

Delete the other values

Hit Ok, and close down the window.

Try to connect to the internet again.

If that works, then you need to get a known good DNS address from your ISP or someone near you.  The one mentioned above is probably not close to you, but I know it works.  I'm in Minneapolis, MN USA.  You are better off with something local.

Let me know how it goes.

---

### Post by WhiteSphinx on 2007-03-08
Thanks!! That worked really well!

---

### Post by vayde on 2007-03-08
Excellent.  Now all you need to do is find a good known DNS address that's a bit closer to you than I am.

Call your ISP and see what they recommend.  You can also check out [www.opendns.com](www.opendns.com) and try using their servers.

Caution: The value you put in there will only work for a while.  The next time you bring up the network interface, you are going to get the default values that you were having problems with in the first place.

To fix it more permanently, you are going to need to edit a file:

go to a command prompt and type the following:
```

sudo gedit /etc/dhcp3/dhclient.conf

```

about 18 lines down you will see a line starting with a # that says 'prepend domain-name-servers 127.0.0.1'

Replace 127.0.0.1 with your known good DNS value.  Then every time your network comes up, it will automatically pop the good value to the top of the list.

Let me know how it goes.

---

### Post by WhiteSphinx on 2007-03-08
It worked for one reboot - but then it stopped working.  I checked the 'prepend domain-name-servers' statement again and my new dns address was still there.  But now I have to change the address again in the network settings to get the internet to work.  We must be missing something here.

---

### Post by Mr. C. on 2007-03-08
Did you remove the # from the front of the prepend line?

---

### Post by vayde on 2007-03-08
pull up a terminal window and type the following:

```

cat /etc/resolv.conf

```

The known good DNS should be in there.  Hopefully at the top of the list.

Good call Mr. C.  I didn't specifically tell him about that.  my bad.

---

