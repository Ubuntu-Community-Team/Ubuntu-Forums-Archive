---
title: "internet tweaking"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by sp0onman on 2007-09-21
ok i have a fast cable internet connection its  30720 / 1024 kbps which is pretty darn good for australia. my internet isn't as fast as it was when i used xp (well this site is pretty fast but others aren't). so if anyone knows any good guides or have any idea's  for making it faster. 

i have disabled ipv6,  and i am using the latest firefox. oh and btw i have a new avatar, bit more family friendly.

---

### Post by alienexplorers on 2007-09-21
Try looking over this page: > [http://www.supernova00.biz/userchrome.html](http://www.supernova00.biz/userchrome.html)

---

### Post by gupta_sumesh63 on 2007-09-22
Making Firefox or Browsing faster:

In the URL location Bar type > about:config

You'll get a > filter Bar
1.	In filter Bar type>  network.http.pipelining
	Default value is false. Double click on false to make it > true.

2.	In filter bar type > network.http.pipelining.maxrequests
	Default value is 4. Double click and change it to > 8.

3.	In filter bar type > network.http.proxy.pipelining
	Double click on false and change to > true.

4.	In filter bar type > network.dns.disableIPV6
	Double click on false to change it to > true.

5.	In filter box type > plugin.expose_full_path	
	Double click false to make it > true

6.	Right click on the browser anywhere
	select > screen->New->Integer
	In the dialog box at the preference name type > nglayout.initialpaint.delay.
	press>  O.K, enter 
	In the new dialog box enter>  0 in the value field and close the dialog box.

7.	Right click the screen again and > New->Integer
	Type > content.notify.backoffcount in preference name.
	Press > O.K, enter 
	Enter > 5 in the value field. Close the dialog box.

8.	Right click browser > screen -> New -> Integer.
	Type > ui.submenuDelay in preference name.>  O.K, enter
	Enter > 0 in the value field.

9.	Now restart the firefox browser. All the above modifications can be done in > offline mode (Without internet running.)

I had also followed the above steps from some link which I forget now. However the effect on browsing speed was phenomenal. I hope it helps.
Enjoy.:guitar:

---

### Post by Warren Watts on 2007-09-22
There is a possibility that the problem lies with the order in which your available DNS servers are being used.

Here's a Thread on the issue:

[How to speed up Ubuntu]("http://ubuntuforums.org/showthread.php?t=550193")

---

