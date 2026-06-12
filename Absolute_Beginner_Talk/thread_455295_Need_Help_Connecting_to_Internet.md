---
title: "Need Help Connecting to Internet"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Earthmars on 2007-05-26
I browse the forums and I can't  find how to connect to the internet. I have a belkin router and a ADSL modem. I have a Realtek network adapter.

---

### Post by neopsalmist on 2007-05-26
Have you checked your interface settings? Open a terminal in Applications > Accessories > Terminal and type:
ifconfig | less.

Make sure that everything is hooked up and that you are getting an ip number. Post your output here.

---

### Post by mart_in_brasil on 2007-05-26
Hi,

Setting up my Speedtouch 510 ADSL cable modem through an ethernet card was easy.
Use "sudo pppoeconf" and accept the defaults.  
There are some instructions:
[https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28adsl%29](https://help.ubuntu.com/community/ADSLPPPoE?highlight=%28adsl%29)

The thing I kept forgetting was the 'sudo' in front of commands.
Without the sudo nothing happens and you do not get any indication that nothing happens.

Subsequently I found that to stop and start my connection I needed
Off: "sudo poff dsl-provider"
On: "sudo pon dsl-provider"
Check it worked: "sudo plog"

Hope this helps

Martin

---

