---
title: "can I speed up Firefox?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by randell6564 on 2006-05-31
Im using Ubuntu 5.10 Breezy, dual booting with XP.

I have the firefox that came with ubuntu and I remember that at one time, you could type somthing into your web browser and it would bring up a page that would allow you to change settings in order to make firefox faster!

Any ideas?

Also...

Applications in ubuntu open kind of slow!

is there a way to improve this?

I have an MSI board P4 Processor, 512 ram and plenty of free space!

---

### Post by Phlosten on 2006-05-31
I think what you are referring to is 'about:config'. Type that into your Firefox browser to get lots of config options. The one that is most popular to change is the IPV6 value.

network.dns.disableIPv6

changing this value to 'true' can help speed things up on some systems.

---

### Post by catlett on 2006-05-31
[http://doc.gwos.org/index.php/DapperGuide#How_to_load_Web_site_faster_in_Mozilla_Firefox](http://doc.gwos.org/index.php/DapperGuide#How_to_load_Web_site_faster_in_Mozilla_Firefox)
Should be the same. It's a Firefox thing not a Ubuntu thing but you might be running a different version of firefox than Dapper does. Again I don't think Firefox's config would change and these directions should work but I just wanted to add it as a "disclaimer" if you no what I mean.

---

### Post by nalmeth on 2006-05-31
Do you have dual core or hyper-threading ability with your processor? If so, you can grab a specified kernel for a performance improvement.

Running a prelink (search for howto to do this) to prelink all the shared libraries makes a noticeable difference, though the actual prelinking can take a long time (especially the first one).

And lastly, you should consider upgrading to Dapper, or doing a fresh install of Dapper (6.06). It's due to be released tomorrow, it has a newer kernel, and give's a lot of speed increases.

Basically the point is your can tweak your system to run faster all across the board, including disabling unneeded services at start-up for a faster boot time.

There are many good howto's on the forums, and wiki.ubuntu.com's User Documentation, and the Ubuntu Document Storage Facility are two other great places to learn how to tweak, and do just about anything for that matter.

---

### Post by Ozitraveller on 2006-05-31
Enter "about:config" in the adress bar and hit enter. Find the following fields and modify them to the following values (format: "field_name: value"):

Try these:
network.dns.disableIPv6: true
network.http.pipelining: true
network.http.proxy.pipelining: true
network.http.pipelining.maxrequests: 8

browser.turbo.enabled: true (I don't think this works in 1.5+)


HOWTO: Make firefox spit fire
[http://ubuntuforums.org/showthread.php?t=10339](http://ubuntuforums.org/showthread.php?t=10339)

---

### Post by randell6564 on 2006-05-31
[QUOTE=Phlosten]I think what you are referring to is 'about:config'. Type that into your Firefox browser to get lots of config options. The one that is most popular to change is the IPV6 value.

network.dns.disableIPv6

changing this value to 'true' can help speed things up on some systems.[/QUOTE]

Thats Exactly what I was reffering to!

Thanks Phlosten!

I just changed it! gonna take it for a test drive!

---

### Post by jason.b.c on 2006-05-31
[QUOTE=Ozitraveller]

Try these:
network.dns.disableIPv6: true
network.http.pipelining: true
network.http.proxy.pipelining: true
network.http.pipelining.maxrequests: 8

browser.turbo.enabled: true (I don't think this works in 1.5+)[/QUOTE]


Actually you can set *Maxrequests:* as high as 50 or so..

Thats what i have mine set to..  Without any problems.;)

---

### Post by RAV TUX on 2006-05-31
[QUOTE=randell6564]Im using Ubuntu 5.10 Breezy, dual booting with XP.

I have the firefox that came with ubuntu and I remember that at one time, you could type somthing into your web browser and it would bring up a page that would allow you to change settings in order to make firefox faster!

Any ideas?

Also...

Applications in ubuntu open kind of slow!

is there a way to improve this?

I have an MSI board P4 Processor, 512 ram and plenty of free space![/QUOTE]

not sure this will work with your processor?
[http://www.getswiftfox.com/](http://www.getswiftfox.com/)

---

### Post by Ozitraveller on 2006-05-31
[http://www.pcmag.com/print_article2/0,1217,a=153989,00.asp](http://www.pcmag.com/print_article2/0,1217,a=153989,00.asp)

Try here as well: (this will thrash the site you are browsing)
Fasterfox
[https://addons.mozilla.org/firefox/1269/](https://addons.mozilla.org/firefox/1269/)

---

### Post by Ozitraveller on 2006-05-31
[QUOTE=jason.b.c]Actually you can set *Maxrequests:* as high as 50 or so..

Thats what i have mine set to..  Without any problems.;)[/QUOTE]

That's true! And I've tried it a 100 as well. I don't know how the site you are browsing will take it though. ;-)

EDIT: I'm browsing via a network so I wonder what this will do the internal network bandwidth.

---

### Post by PingunZ on 2006-06-12
Goto the HOWTO in my sig ;)

---

