---
title: "some websites not working"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by dberg on 2007-09-01
Every once in a while a website that I use regularly just stops working, I get "Server not found". This time it is [http://home.ingdirect.com/]("http://home.ingdirect.com/"). I know the site is up because it works fine using my windows machine.

I have tried clearing my cache, restarting, resetting my router, etc. Nothing seems to work. Are others having the same problem or is it just me? Running 7.04 and Firefox 2.0.0.6

Thanks

---

### Post by Majorix on 2007-09-01
Does refreshing the page not work? It also happens to me on both Ubuntu AND Windows but usually when I refresh it it works fine.

---

### Post by dberg on 2007-09-01
Nope, refreshing doesn't help.

---

### Post by snowjm on 2007-09-01
Not sure if this is the wisest method for doing anything about it, but you could possibly flush your DNS settings.

---

### Post by Seisen on 2007-09-01
try using opendns
[http://www.opendns.com/]("http://www.opendns.com/")

---

### Post by banewman on 2007-09-01
When I have a similar problem on occasion, I click the back button then forward button and mostly get in to the site. I just figured the site was busy. :)

---

### Post by Lord Illidan on 2007-09-01
Don't think it's a problem with Ubuntu in general..can see it here.

---

### Post by dberg on 2007-09-01
Must be AT&T's problem. Using OpenDNS it works like normal.

---

### Post by bone2006 on 2007-09-01
you didn't indicate if you used IE in windows or if you used firefox to determine if it's a browser problem or not?  

try going to the website via IP instead of DNS, type in ping and the url and you'll see the IP.  But I wold try using opendns as well, generally it will increase your speeds.

But I would start off trying firefox in windows, I just clicked on the link and I'm using ubuntu and it came up just fine for me.  Also try searching for the URL maybe in google and clicking it there to see what happens and finally I'd try using another DNS such as opendns as has been suggested.

---

### Post by dberg on 2007-09-01
In windows I used both IE and Firefox, both worked.

---

### Post by bapoumba on 2007-09-01
Try to clear the cookie(s) related to this site.

---

### Post by cubicsilver on 2008-01-14
For me the website that did not work was oemdepot.com

There is a bug (59331) in the kernel  that causes some websites to stop loading

To fix, you need to add some lines to the sysctl.conf

```
sudo gedit /etc/sysctl.conf
```

add these lines:
```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

save and run this

```
sudo sysctl -p
```

then try your website again

---

