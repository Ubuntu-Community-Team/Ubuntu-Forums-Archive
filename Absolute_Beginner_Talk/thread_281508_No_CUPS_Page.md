---
title: "No CUPS Page"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by coolboarderguy on 2006-10-21
Hi All,

I try to bring up CUPS via localhost:631 but get the following,



Unable to connect    
                  

Firefox can't establish a connection to the server at localhost:631. 

              

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.



Apache was not originally installed, which I figured would be needed so installed and confirmed is running. I then confirmed that cupsd is also running. See below.



mark@marklaptop:/etc/cups/cups.d$ sudo ps aux | grep apache
root     12733  0.0  0.2   4560  2096 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12736  0.0  0.1   4560  1348 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12737  0.0  0.1   4560  1352 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12738  0.0  0.1   4560  1336 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12739  0.0  0.1   4560  1296 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12740  0.0  0.0   4560   904 pts/0    S    21:18   0:00 /usr/sbin/apache

Please advise where it is I'm going wrong here. I've checked /etc/cups/cups.d/port.conf and /etc/cups/cups.conf. I don't see anything wrong. Thank you.


www-data 12749  0.0  0.0   4560   908 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12750  0.0  0.0   4560   908 pts/0    S    21:18   0:00 /usr/sbin/apache
www-data 12751  0.0  0.0   4560   908 pts/0    S    21:18   0:00 /usr/sbin/apache
mark     13229  0.0  0.0   2888   808 pts/0    R+   21:34   0:00 grep apache
mark@marklaptop:/etc/cups/cups.d$ sudo ps aux | grep cupsd
cupsys    4546  0.0  0.1   4200  1792 ?        Ss   17:47   0:00 /usr/sbin/cupsd
mark     13237  0.0  0.0   2892   808 pts/0    R+   21:34   0:00 grep cupsd

---

### Post by .t. on 2006-10-21
Are you accessing it through https, ie "https://localhost:631"?

I don't see why you'd need to, mine works fine out of the box (on Edgy).

---

