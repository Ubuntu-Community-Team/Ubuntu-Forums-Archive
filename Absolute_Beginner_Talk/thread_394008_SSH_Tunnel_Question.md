---
title: "SSH Tunnel Question"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Pete89 on 2007-03-26
Hello,

I just got OpenSSH working on a Windows 2003 server at a remote sight. I am now able to SSH in with my Ubuntu laptop and everything seems to work just fine. I changed the defualt port of 22 to a high port number because I heard this was a good practice on Linux Reality.

So now I would like to know if it is possible to relay all my HTTP traffic from my laptop via the remote Winders machine over SSH? The idea is to have this trafiic encrypted.

Do I need to create somekind of tunnel first?

Thanks,

Pete Noob

---

### Post by lamalex on 2007-03-26
I'm not sure if this is possibleit may very well be. If it is it will be some sort of port forwarding. It would look something like this

ssh -l username -p (custom ssh port) sshserver -L port-to-forward-through:ip-of-host:port-of-service

example ssh  -l administrator -p 1022 [www.google.com](www.google.com)  -L 59595:192.168.1.1:80

that would send web traffic from 192.168.1.1 into your 59595, so i think in firefox you would do [www.ubuntuforums.org:59595](www.ubuntuforums.org:59595) to go through their maching and the ssh tunnel. 

 a VPN may better suit your needs here. You could then even close off SSH to the internet for remote control over that server and only allow it from internal, which you would be if you're VPNed into the network.

---

### Post by Pete89 on 2007-03-26
Thanks for your reply but that did not seem to work for me. When I run the command you gave me I was able to connect to my SSH server but when I opened my browser I was still going through my ISP directly. The VPN is a great idea but I am doing this because I want to see if it will work.

 Do you think I need to install something like FoxyProxy or something similar.

Thanks,

Pete

---

### Post by lamalex on 2007-03-26
did you add the port to the end of your url? you don't need any sort of extension. I don't have an ssh server available to me right now to test this on but I've done it before from work (all of our ssh authentication is key based, no passwords and I don't have the keys on my laptop). so if you're trying to go to google it'd be open ssh tunnel, and then [www.google.com:59595](www.google.com:59595)

---

### Post by Pete89 on 2007-03-26
Thanks again for replying so quickly. I did try using the port number after the URL. The error I see on the server side while I am connected is:

channel 4: open failed: connect failed: Connection timed out

or

channel 3: open failed: connect failed: Connection timed out

Lost...

---

### Post by lamalex on 2007-03-26
i just did it using this syntax
```

ssh root@server -L 8888:whereyouwanttogo:80

```

---

### Post by lamalex on 2007-03-26
also try this to see if it's working at all
```
 ssh root@server -L 8889:serverinteralip:80
(in firefox) localhost:8889
```

---

### Post by lamalex on 2007-03-26
OK THIS WORKS. I am port forwarding through my CS server to google.

ssh root@server -L 8889:[www.google.com:80](www.google.com:80)
then localhost:8889 in FF.

if you navigate away from google, you lose your secure session. :) im happy and I hope you're happy!

---

### Post by kpatz on 2007-03-26
The best way to do this is to have some sort of proxy running on the box you're SSH-ing into, or some other box that is on the network you're SSH-ing into.

For example, if you had a Squid Proxy running on port 3128 on your ssh server, you could set up the tunnel like this:

ssh user@server -L 3128:localhost:3128

Then go into your browser's connection settings, and tell it to use a proxy server on localhost:3128.  Then all your web traffic will go through the SSH tunnel to the proxy.

---

### Post by Pete89 on 2007-03-26
Oh boy thanks...but right now I am at home  and getting ready to go to bed. (I am in Spain) I will check out what you guys said to try and I will report back tomorrow

Greatly appreciated,

Pedro

---

### Post by Pete89 on 2007-03-27
OK I am back to report this worked for me:

ssh -p 22222 root@server -L 8889:[www.google.com:80](www.google.com:80)
then localhost:8889 in FF

So the next step would be how can I do this for ALL my web browsing and not just google.com with my present setup? I cant install a proxy server on the Winders box even though I´d like to. Would this be possible?

Many thanks to Iamalex for helping out this noob. The forums in Ubuntu are the best I have ever seen and people like Iamlex make the difference!!

Muchas Gracias!!

Pedro

---

### Post by Pete89 on 2007-03-27
Hello Again,

I thought I would let everyone know I found an answer to my own question which was:

Is there a way to tunnel **ALL** my HTTP traffic over the SSH tunnel with my present setup (which meant I coundnt install SQUID like KPatz suggested). And there is.

I first set up a tunnel with dynamic port forwarding like so:

```
ssh -p 22222 pedro@pedro.com -D 4545
```

This lets me browse away from google.com

And then in Firefox I set the proxy setting to *localhost* where it says SO_C_KS Host: and used port 4545. I marked version 5v for the SOCKS version. I dont know if that will make a difference or not. Everything else on that page was blank except for where it says No Proxy for: where it has localhost, 127.0.0.1

And thats it.

Now I have another question:

How can I tunnel ALL protocols over the SSH tunnel and not just HTTP??

Thanks for everyones help

---

### Post by lamalex on 2007-03-27
you want to do https tunneling as well? eek that might be a tough one. I really don't know. I've never gotten it to work but also havn't tried that hard, never had a reason to. good luck, let me know if you figure it out

---

### Post by Pete89 on 2007-03-27
Hey,

I want to be able to tunnel **all** traffic/protocols over SSH. 

Say for instance your in a cyber cafe and want to safely use your pop3/smtp mail or over thier wireless or you need to ftp into a site and grab a file while your on a hotels LAN. 

I know the right answer to all of this is called VPN but this is all part of an exersise in how things work.

Thanks,

P.

---

### Post by lamalex on 2007-03-27
you should be able to, just change your destination port to whatever port you're trying to do uses, 110 for pop3 and so on. ssh tunneling isn't a substitute for a vpn, but it will do somethings.

---

