---
title: "can you traceroute to a specific port"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by tommythecat on 2006-06-13
Can anyone tell me if/how you can traceroute to a specific port?  

Thanks :)

---

### Post by Juippisi on 2006-06-13
> ultima joonas # tcptraceroute ubuntuforums.org 80
Selected device eth0, address 81.175.158.128, port 58340 for outgoing packets
Tracing the path to ubuntuforums.org (82.211.81.186) on TCP port 80 (http), 30 hops max
 1  at1-0.dsl-home-r1.hol.phnet.fi (81.175.152.1)  6.976 ms  6.315 ms  6.637 ms
 2  salpakangas-pe1.hol.phnet.fi (62.165.129.73)  8.200 ms  7.017 ms  6.729 ms
 3  harjukatu-p2.mpls.php.fi (62.241.209.38)  7.792 ms  7.648 ms  7.697 ms
 4  harjuk-pe-r5.lht.phnet.fi (81.175.254.69)  7.633 ms  7.774 ms  7.953 ms
 5  ae0-2.core-r2.lht.phnet.fi (81.175.254.1)  6.954 ms  6.938 ms  6.601 ms
 6  ae0-50.brdr-r1.hki.phnet.fi (62.165.129.185)  8.293 ms  8.130 ms  8.814 ms
 7  hki1r5.k.fv.fi (217.78.199.113)  8.571 ms  8.164 ms  8.787 ms
 8  hki2r5.k.fv.fi (217.78.198.34)  8.893 ms  8.994 ms  9.303 ms
 9  * * tuk2r2.k.fv.fi (217.78.198.202) 15.179 ms
10  ge-0-3-0-ycr2.skt.cw.net (166.63.220.81)  15.798 ms  16.528 ms  16.189 ms
11  so-5-1-0-dcr1.amd.cw.net (206.24.147.197)  40.815 ms  41.099 ms  41.091 ms
12  so-3-0-0-zcr1.amt.cw.net (208.173.211.238)  41.269 ms  41.176 ms  41.556 ms
13  so-4-3.core1.Amsterdam1.Level3.net (213.244.165.245)  41.077 ms  41.152 ms  42.046 ms
14  so-4-0-0.mp1.Amsterdam1.Level3.net (4.68.113.74)  42.315 ms  40.953 ms  41.817 ms
15  ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  51.396 ms  50.262 ms  50.444 ms
16  ae-0-55.gar1.London2.Level3.net (4.68.117.139)  51.188 ms  51.035 ms  51.186 ms
17  ge-6-2.core-r-1.lon2.mnet.net.uk (195.50.91.138)  50.678 ms  50.523 ms  51.401 ms
18  85.133.32.134  51.428 ms  50.613 ms  50.926 ms
19  82.211.81.76  51.182 ms  51.096 ms  51.912 ms
20  ohiggins.ubuntu.com (82.211.81.186) [open]  50.906 ms  51.527 ms  52.376 ms
ultima joonas # tcptraceroute --help

tcptraceroute 1.5beta6
Copyright (c) 2001-2005 Michael C. Toren <mct@toren.net>
Updates are available from [http://michael.toren.net/code/tcptraceroute/](http://michael.toren.net/code/tcptraceroute/)

Usage: tcptraceroute [-nNFSAE] [-i <interface>] [-f <first ttl>]
       [-l <packet length>] [-q <number of queries>] [-t <tos>]
       [-m <max ttl>] [-pP] <source port>] [-s <source address>]
       [-w <wait time>] <host> [destination port] [packet length]

ultima joonas # tcptraceroute ubuntuforums.org -p 80
Selected device eth0, address 81.175.158.128, port 80 for outgoing packets
Tracing the path to ubuntuforums.org (82.211.81.186) on TCP port 80 (http), 30 hops max
 1  at1-0.dsl-home-r1.hol.phnet.fi (81.175.152.1)  6.592 ms  6.798 ms  6.226 ms
 2  salpakangas-pe1.hol.phnet.fi (62.165.129.73)  6.670 ms  6.696 ms  8.039 ms
 3  harjukatu-p2.mpls.php.fi (62.241.209.38)  7.390 ms  7.182 ms  7.578 ms
 4  harjuk-pe-r5.lht.phnet.fi (81.175.254.69)  7.695 ms  7.522 ms  7.823 ms
 5  ae0-2.core-r2.lht.phnet.fi (81.175.254.1)  18.063 ms  7.392 ms  7.347 ms
 6  ae0-50.brdr-r1.hki.phnet.fi (62.165.129.185)  8.291 ms  8.144 ms  8.321 ms
 7  hki1r5.k.fv.fi (217.78.199.113)  8.562 ms  8.405 ms  8.313 ms
 8  hki2r5.k.fv.fi (217.78.198.34)  8.965 ms  9.256 ms  9.280 ms
 9  * tuk2r2.k.fv.fi (217.78.198.202) 15.053 ms  15.062 ms
10  ge-0-3-0-ycr2.skt.cw.net (166.63.220.81)  15.439 ms  15.060 ms  15.950 ms
11  so-5-1-0-dcr1.amd.cw.net (206.24.147.197)  41.064 ms  41.655 ms  41.091 ms
12  so-3-0-0-zcr1.amt.cw.net (208.173.211.238)  41.064 ms  40.914 ms  41.327 ms
13  so-4-3.core1.Amsterdam1.Level3.net (213.244.165.245)  41.310 ms  41.407 ms  41.810 ms
14  so-4-0-0.mp1.Amsterdam1.Level3.net (4.68.113.74)  42.294 ms  41.663 ms  41.552 ms
15  ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  50.200 ms  50.760 ms  50.692 ms
16  ae-0-51.gar1.London2.Level3.net (4.68.117.11)  50.433 ms  50.087 ms  50.431 ms
17  195.50.91.146  50.705 ms  51.096 ms  50.429 ms
18  85.133.32.134  51.093 ms  51.082 ms  51.181 ms
19  82.211.81.76  51.590 ms  51.135 ms  51.576 ms
20  ohiggins.ubuntu.com (82.211.81.186) [open]  51.167 ms  51.002 ms  52.132 ms

As you can see, --help helps you :-).

tcptraceroute destination -p port

---

### Post by tommythecat on 2006-06-13
Thank you for the reply:

I tried --help among other things, but couldn't seem to find tcptraceroute or even just traceroute on my badger install.

Maybe I just need to apt-get it first...

---

### Post by tommythecat on 2006-06-13
I was able to apt get traceroute and using a -p lets me specify a port, so I guess I'm all set now.  Thanks for the help.

---

