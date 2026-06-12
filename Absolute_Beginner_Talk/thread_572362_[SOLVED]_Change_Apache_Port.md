---
title: "[SOLVED] Change Apache Port"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-10-10
Hi All

I followed the instructions here:
[http://lijinjoseji.wordpress.com/2007/02/28/steps-to-change-the-default-port-number-for-apache-http-server/](http://lijinjoseji.wordpress.com/2007/02/28/steps-to-change-the-default-port-number-for-apache-http-server/)
here:
[http://ubuntuforums.org/showthread.php?t=525847](http://ubuntuforums.org/showthread.php?t=525847)
and here:
[http://ubuntuforums.org/showthread.php?t=427711](http://ubuntuforums.org/showthread.php?t=427711)

I am trying to change the port my http server listens on because my ISP blocks port 80 and I'm only using it for my personal Egroupware server so I don't care if I have to specify the port. 

I am trying to change it to port 3352 (a random port, up high, that they don't block, and is seldom used). First I tried making it listen on both 80 and 3352 but did not restart apache right so that didn't work. I then changed it to listen on just 3352 and restarted  apache (I tried on 80 and got nothing so I know it worked). I then changed it to listen on 80 and 3352 and restarted the server again. I have yet to actually access it on port 3352 though. I have added the appropriate rules in my firewall and I am accessing it with the local ip so I'm not sure why I would now be able to access it on 80 but not 3352.

Any help is much appreciated.

P.S. I'm running Xubuntu if that makes any difference and when I restart apache I get this error:
```
 * Forcing reload of web server (apache2)...                                                        
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by bsharp on 2007-10-10
That is a warning meaning that you haven't specified a FQDM (fully qualified domain name) in your virtual server entry.  

As for running it on the port, I'm at school right now and can't really check myself, but you could configure your router to forward everything from your WAN on port 3352 to your LAN ip on port 80

---

### Post by Dr Small on 2007-10-10
> **bsharp said:**
> That is a warning meaning that you haven't specified a FQDM (fully qualified domain name) in your virtual server entry.  

As for running it on the port, I'm at school right now and can't really check myself, but you could configure your router to forward everything from your WAN on port 3352 to your LAN ip on port 80
+1
That's what I would do, that is, if he is behind a router.

---

### Post by High Camp on 2007-10-10
Hey bsharp

Thanks for the reply. I think my router has a "security feature" that it won't forward to port 80. I can get it to forward to port 21 for an ftp server but no matter what I do it will not forward http. At first I thought it might have something to do with the remote management on port 8080 so I disabled that and it still won't forward. I even went so far as to try DMZ (demilitarized zone) the computer I am using as the server and still no go.

Thanks,

---

### Post by Dr Small on 2007-10-10
What kind of router you have ?

---

### Post by High Camp on 2007-10-10
Linksys.

As you can see from the attached screen shots. I think I have set everything up right. I should at least be able to connect on the local ip, I think.

Thanks,

---

### Post by Dr Small on 2007-10-10
[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/HTTP.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/HTTP.htm)
<< A tutorial on how to setup port forwarding for your router.

Just change the ports around to what you want.

Dr Small

---

### Post by hangthedj on 2007-10-10
try added port 3352 on the first screenshot page
and make sure your VirtualHost directive (newer versions of apache usually have one for the main site, even if you only have one site) is set to VirtualHost * or VirtualHost *:3352

---

### Post by High Camp on 2007-10-10
Still no go. I don't have static ip's setup but that shouldn't matter as far as getting it working. The only thing I had to change with that tutorial is the security settings and I have played with those already. 

I have just completely disabled all security settings as a test and still nothing. I have used...

Scratch all that. I have now got it working! I tried the DMZ again and it worked. I guess the first time I tried it I didn't have the ports forwarded properly.

So, for anyone else trying this:
1. Change your http port to something that is not blocked.
2. Add a rule on your firewall for that port.
3. Forward ports on your router.
4. Enable the firewall.
5. Disable blocking of "Anonymous Internet Requests" and filtering of "Internet NAT Redirection".
6. Make the server demilitarized (DMZ). 

NOTE: By doing this you are potentially opening yourself to the world wide web and all the nasty people on it. Be careful, know what you're doing, and better safe than incredibly sorry.

Thanks so much for everyones help,

---

