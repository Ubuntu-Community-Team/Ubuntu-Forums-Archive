---
title: "nameserver confusion"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by malk on 2007-03-15
Hello, i have a bit of a situation regarding a new domain and nameservers.
I had purchased a domain from ipower and i want it to point at my webserver, i did this about 24 hours ago. I made the nameserver in my bind settings and i was able to reload bind successfully and then i entered the new nameserver i created on ipowers web domain management. i know it takes 24-48 hours for it to propegate but is there a way to test the name server to ensure they are set right? At the moment the domain points at ipowers dns and ip which i would like changed.
Cheers
Malk

---

### Post by siciliancasanova on 2007-03-15
You can test the IP address of the same server the domain name is pointing at to make sure the server is resolving right but I don't know of too much else you can do.  I recently had to wait 72 hours for a propagation because on this particular weekend my ISP was slow in refreshing and kept giving me a cached version of the site.  My neighbor was able to get on the site fine with a different ISP.

---

### Post by irwa82 on 2007-03-15
Hi,

I am assuming that you want to test if the dns you setup is working.

to do so you can use dig on the machine with the dns.

dig yourdomain.com

to see what the mx records return do dig yourdomain.com mx

if you want to ensure that dig is looking at your name server do the following

dig @yourdnsserver domain.com
dig @yourdnsserver domain.com mx

---

### Post by malk on 2007-03-15
I'm not very good with bind and dns settings but when i set the nameservers in bind it reloaded successfully, although when i did a dig few minutes ago it responded with ;; reply from unexpected source: xxx.xxx.x.xxx#53, expected 192.168.1.1#53

The xxx.xxx is the dns my isp originally provided but the second domain i bought is from an outside source. Am i missing something trivial or just wait a day and see what happens?
I really would like this to work becuase my wife also bought a url that i will host on my webserver which would be 3 in total. My original domain that i have now is working fine with dns and all so just a bit puzzled.
Thanks
Malk

---

### Post by irwa82 on 2007-03-15
Hi,

Assuming that 192.168.1.1 is your dns server then you can do the command below to see what your dns returns for the domain.

dig @192.168.1.1 yourdomain.com

---

### Post by malk on 2007-03-15
Here is the result from that command.
> ; <<>> DiG 9.3.2 <<>> @192.168.1.1 northernwindsofgor.com
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached


---

### Post by malk on 2007-03-15
I can post the zone file if it would help clear things up for me.
Malk

---

### Post by malk on 2007-03-15
Does it seem right that the nameserver i had created for the domain can be pinged from multiple people using different isp's but cant ping the domain name?
I did a test at [http://www.dnsstuff.com]("http://www.dnsstuff.com") and everything passed for the dns except the final spot for NS which i dont understand unless that becuase it may not be done propagating. Here is the link to my results for the test if anyone can explain what i may or may not did wrong. Thanks. [http://www.dnsstuff.com/tools/dnsreport.ch?domain=northernwindsofgor.com]("http://www.dnsstuff.com/tools/dnsreport.ch?domain=northernwindsofgor.com")
Cheers
Malk

---

