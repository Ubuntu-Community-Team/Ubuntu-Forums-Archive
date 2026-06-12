---
title: "Dynamic DNS"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-19
I am starting to use VNC alot now, its a very userfull tool. Im sick and tired of checking my IP address every time it changes, going to my other computer, typing it in and connecting. It looks like Dynamic DNS is just what im looking for. If anyone uses it for VNC or knows more about it please tell me. 

Steven

---

### Post by CatKiller on 2006-10-19
[This Wikipedia page]("http://en.wikipedia.org/wiki/Dynamic_DNS") might explain the basics. All I knew previously was the name. I think I read it in the [networking forum]("http://ubuntuforums.org/forumdisplay.php?f=136"), so a browse in there might get you some recommendations for a provider or configuration.

---

### Post by junglepeanut on 2006-10-19
I don't know much about it, but I setup a server with it. It was very easy.

And since I think once a month or every other month I go to the website and click renew free service. (or some command that means the same thing)

When I first started using it, it felt like after restart it would take like a half hour to recognize the address again, but now I know it is very quick. I can login remotely update, restart the box, and then wait a minute for the box to restart and bam I can login again, and the box has a new ip too. So it is nice.

---

### Post by grim918 on 2006-10-19
If you have several computers within your network then you can configure them with static internal ip addresses and then you don't have to keep checking for the dynamic ip everytime you want to log in to another computer using vnc. If you want to log into one of your computers from a remote location lets say from your job to your home computer then you could use a service like no ip.
check out [http://www.no-ip.com](http://www.no-ip.com).

heres a helpful link:[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)

Heres one on dynamic dns: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

