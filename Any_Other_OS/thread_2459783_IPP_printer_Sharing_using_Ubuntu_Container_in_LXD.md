---
title: "IPP printer Sharing using Ubuntu Container in LXD"
date: 2021-03-26
forum: Any Other OS
---

### Post by hvaria2 on 2021-03-26
I have a network printer that only supports LPD/LPR printing. This printer is currently Mapped to my Linux Container.
I have turned around and used ubuntu to share this printer. This allows the printer to be shared using the IPP protocol allowing driver less printing from my mobile devices.
Everything works like a charm the first time I try to print.

Issue happens after 10-15 minutes when for no known reason the printer becomes unavailable.
I have to then open the Ubuntu printer utility and then rename the printer description or some other filed a few times and after that the printer comes online.
I do not understand this behavior and how I can ensure that the printer is always shared using IPP.

Is there some type of sleep function that is messing things up here?

---

### Post by DuckHook on 2021-03-26
A clever use of LXD containers!

I can only think of the following:

[LIST=1]
[*]Look in your logs, both on the host and in the container. Filter for the network name of the printer, "LPR", "LPD", "IPP", IP address, etc. Everything you can think of.
[*]Is your printer going to sleep and dropping its network connection?
[*]When the printer becomes unavailable, can you still get in to its HTML maintenance page?
[/LIST]

---

### Post by hvaria2 on 2021-03-26
Hi DuckHook thanks for the suggestions... I am going to give it a try and see what I can find out in the logs on the Host. Cannot access server logs cause it is ChromeOS.
I know the actual printer is not sleeping. I have tested printer sharing using a virtual PDF printer and a real network printer.
Can you please elaborate on the HTML maintenance page please... what is that

---

### Post by DuckHook on 2021-03-26
> **hvaria2 said:**
> Hi DuckHook thanks for the suggestions... I am going to give it a try and see what I can find out in the logs on the Host. Cannot access server logs cause it is ChromeOS.
ChromeOS(!) Okay, you need to mention things like that when asking for help because it has huge bearing on the problem. I didn't know that ChromeOS was even capable of running LXD. If the Chrome host is doing funny things to your LXD container, then I can't help you. I have no familiarity with ChromeOS whatsoever.

I am also moving your thread to a more appropriate subforum since it does not fall under Ubuntu.
> Can you please elaborate on the HTML maintenance page please... what is that
Most printers can be accessed through a small built&#8209;in web server. I have no idea if yours can, but it's worth a try. If it can be, then you usually have the ability to both view and change printer settings using the maintenance page. Your printer user manual should have instructions on how to access this page. I had printers almost 29 years old (now all retired) that had such web interfaces. Frankly, I'm hard pressed to remember any printers that did not.

---

