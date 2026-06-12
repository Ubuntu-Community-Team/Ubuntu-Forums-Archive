---
title: "DNS settings and the internet"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by reeceaxl on 2006-09-02
I've been trying to follow the advice on the million other posts about connecting to the internet but so far no luck. I am using a router.
What I have done: 
manually entered my configuration as static IP address and then entered the settings I found on the router status page. I also entered my provider's DNS.
I disabled ipv6 in Firefox. 
Still, I get the "Server not found" message. 
If anyone could give me a hand, I would appreciate it. Let me know what other info you might need.

---

### Post by reeceaxl on 2006-09-02
oh, I also checked and my pppoe package is indeed installed.

---

### Post by reeceaxl on 2006-09-03
Maybe I didn't give enough info for anyone to help me. Initially when I tried to connect I received this message: 


Sorry I scanned 1 interface,but the Access Concentrator of your
provider did not respond ... check cables... another pppoe proc
might be controlling... etc.

I followed the ADSLPPPoE Community Ubuntu Documentation guide that was posted and got stuck when I reached that message. Then I followed the steps I mentioned above from this post: 
[http://ubuntuforums.org/showthread.php?t=179534&highlight=pppoe+scanned+access+concentrator](http://ubuntuforums.org/showthread.php?t=179534&highlight=pppoe+scanned+access+concentrator)

Please help me out if you can because I am out of ideas.

Thanks!

---

### Post by Norfolk 'n' Good on 2006-09-03
I have a similar problem, so to temporalrily connect at each log-on try the following...

 >System
 >Administration
 >Networking
 >Enter your password
 >Highlight the 'Ethernet connection' under the 'Connections' tab
 >Properties
 >At 'Configuration' select 'Static IP address' from the drop-down menu
 >Reselect DHCP from the drop-down menu
 >Okay everything and you should be done

This is only a temporary measure that allows me to connect each time I log into Ubuntu.  It's not great but it works for me.  

Good luck and let me know if the fix works.

---

### Post by reeceaxl on 2006-09-03
Thanks! That fix worked so that is rad. If anything permanent comes up I would like to hear about it, but this works for now.

---

