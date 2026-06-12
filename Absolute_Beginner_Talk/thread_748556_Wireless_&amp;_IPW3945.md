---
title: "Wireless &amp; IPW3945"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by atorch on 2008-04-07
Hi,

I'm trying to get packet injection to work with my ipw 3945; I've been using the following tutorial:

file:///home/torch/Desktop/injection%20walkthrough.html [edit:  this is a link to a file on my desktop.  I'll leave it here because I think it's funny, but the actual link is below.  woops]

[http://aircrack-ng.org/doku.php?id=ipw3945](http://aircrack-ng.org/doku.php?id=ipw3945)

I got to the step named "Configure your Wireless Card," without errors as far as I could tell.

Unfortunately, when I run "iwconfig" after having run "sudo modprobe -r ipw3945" and "sudo modprobe ipwraw" I get the following output:

lo        no wireless extensions.

eth5      no wireless extensions.

...and nothing else.  Usually I have a third connection, eth6, which is my wireless card.  The wireless connection only reappears (and wireless begins working again) after I re-load my usual driver using "sudo modprobe -r ipwraw" and "sudo modprobe ipw3945".

What's going on?  

The tutorial states:
The device name must not &#8220;eth1&#8221; it can be &#8220;wifi0&#8221; or what ever. You can see this with &#8220;iwconfig&#8221;.

My device name is eth6.  Must I change it before installing the new driver?

Many thanks, in advance, for any help,

- Adrian

---

### Post by mick8985 on 2008-04-08
I don't know about your question, but the iwl3945 driver supersedes the ipw3945 driver (which was always really buggy for me). Perhaps you would have more luck blacklisting it and using the iwl3945 instead

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues")

---

### Post by atorch on 2008-04-08
Does iwl allow packet injection?

Edit for clarification:  I´m looking for a wireless driver that would allow me to use aircrack-ng.

---

### Post by mick8985 on 2008-04-08
I don't know, try it.

---

